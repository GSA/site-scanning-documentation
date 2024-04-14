_[This is a description of the step-by-step technical process by which we 'scan' each Target URL.  These steps come after the initial process of [building the Target URL list](https://github.com/GSA/federal-website-index/blob/main/process/index-creation.md).]_

First off, before any scans take place, the process of ingesting the target URL list into the database populates the following fields: 
* `Target URL`
* `Target URL - Base Domain`
* `Target URL - Top Level Domain`
* `Target URL - Base Domain Agency Owner`
* `Target URL - Base Domain Bureau Owner`
* `Target URL - Base Domain Branch`
* `Target URL - Data Source`

When scanning commences, [this core file](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/core-scanner.service.ts#L36) dictates which scans are run.  Due to the nature of the code base, the scans run asynchronously (i.e. they don't necessarily run in the order they are written in the code). Each scan operates separately and don't talk to each other.  

The [current scans](https://github.com/GSA/site-scanning-engine/tree/main/libs/core-scanner/src/pages) are: 

- [`primary`](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/pages/primary.ts) - Loads the Target URL and analyzes the resulting Final URL, generating most of the Site Scanning data.  
- [`dns`](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/pages/dns.ts) - Analyzes the DNS of the Final URL using a Node.js library (instead of Puppeteer).  
- [`notFound`](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/pages/not-found.ts) -  Tests for proper 404 behavior using an https service (instead of Puppeteer).  
- [`robotsTxt`](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/pages/robots-txt.ts) - Appends `/robots.txt` to the Target URL, loads it, and analyzes the resulting `robots.txt` Final URL.  
- [`sitemapXml`](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/pages/sitemap-xml.ts) - Appends `/sitemap.xml` to the Target URL, loads it, and analyzes the resulting `sitemap.xml` Final URL.

Each scan notes whether it Completed, or failed due to one of the following reasons: Timeout, DNS resolution error, Invalid SSL cert, Connection refused, Connection reset, or Unknown error.  These populate the `Scan Status - Primary`, `Scan Status - DNS`, `Scan Status - Not Found`, `Scan Status - Robots.txt`, and `Scan Status - Sitemap.xml` fields.  

The `Scan Status - Date` field is populated when the scan data is written to the database.  


### Primary Scan

The primary scan uses [Puppeteer](https://pptr.dev/) to load a Target URL in a headless Chrome/Chromium browser.  It then (again asynchronously) runs a number of what might be thought of as scan components, the list of which can be found [here](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/pages/primary.ts#L48-L58) and the code for which can be found [here](https://github.com/GSA/site-scanning-engine/tree/main/libs/core-scanner/src/scans).  

At the moment, these 'scan components' are: 
* [urlScan](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/scans/url-scan.ts) - which loads the Target URL and then notes whether it redirects; what the Final URL is; whether it is live; what its server status code, filetype, and base domain are; and whether the Final URL is on the same domain and same website as the Target URL. This populates the `Final URL`, `Final URL - Base Domain`, `Final URL - Base Website`, `Final URL - Top Level Domain`, `Final URL - Media Type`, `Final URL - Live`, `Target URL - Redirects`, `Final URL - Same Base Domain As Target URL`, `Final URL - Same Base Website As Target URL`, and `Final URL - Status Code` fields.
  * For `Final URL - Live` - it is marked `TRUE` if the final server status code is one of these - 200, 201, 202, 203, 204, 205, 206.
  * For `Target URL - Redirects` - it is marked `TRUE` if the are one or more components in the redirect chain of the request method.  
* [cloudDotGovPagesScan](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/scans/cloud-dot-gov-pages.ts) - which looks to see if there's an x-server response header that says `cloud.gov pages`.  This populates the `Infrastructure - Cloud.gov Pages Detected` field.  
* [cmsScan](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/scans/cms.ts) - which looks for certain code snippets in the page html and headers that indicate the use of a certain CMS.  These code snippets are borrowed from the great work of [Wappalyzer](https://github.com/tunetheweb/wappalyzer), specifically the files in [this folder](https://github.com/tunetheweb/wappalyzer/tree/master/src/technologies). This populates the `Infrastructure - CMS Provider` field.  
* [cookieScan](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/scans/cookies.ts) - which uses Puppeteer's built in functionality to note the domains of all cookies that load. This populates the `Infrastructure - Cookie Domains` field.  
* [dapScan](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/scans/dap.ts) - which captures the outbound requests that occur when the target URL loads and notes whether a call using the Digital Analytics Program tag IDs ('UA-33523145-1' or 'G-9TNNMGP8WJ') is one of them.  If it is, the Google Analytics parameters are also captured.  This capture of parameters fails though if the DAP snippet is self-hosted.  Therefore, the scan looks at all outbound requests and sees if they come from a url ending in `Universal-Federated-Analytics-Min.js` and if it does, then still captures the parameters.  These steps populate the `Infrastructure - DAP Detected` and `Infrastructure - DAP Parameters` fields.  
* [loginScan](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/scans/login.ts) - which looks for certain code snippets in the page html to indicate the presence of a login form or the use of a certain  login provider.  This populates the `Infrastructure - Login Provider` and `Infrastructure - Login Detected` fields.  
* [mobileScan](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/scans/mobile.ts) - which looks for a certain code snippet to indicate the presence of a viewport meta tag.  This populates the `Mobile - Viewport Meta Tag Detected` field.
* [requiredLinksScan](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/scans/required-links.ts) - which looks for certain strings in each hyperlinked text and associated URLs that may indicate the presence of a required link, as specified on [this Digital.gov page](https://digital.gov/resources/required-web-content-and-links).  This populates the `Required Links - URL` and `Required Links - Text` fields.
* [searchScan](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/scans/search.ts) - which looks for certain code snippets in the page html to indicate the presence of a site search form or to indicate the use of Search.gov.  This populates the `Infrastructure - Site Search Detected` and `Infrastructure - Search.gov Detected` fields.
* [seoScan](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/scans/seo.ts) - which looks for various search engine optimization elements within the page's source code.  This populates the `SEO - title`, `SEO - description`, `SEO - og:title`, `SEO - og:description`, `SEO - article:published_time`, `SEO - article:modified_time`, `SEO - Main Element` and `SEO - Canonical Link` fields.  
* [thirdPartyScan](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/scans/third-party.ts) - which captures the outbound requests that occur when the target URL loads, notes them, and counts how many unique third party services they represent.  This populates the `Infrastructure - Third Party Service Domains` and `Infrastructure - Third Party Service Count` fields.  
* [uswdsScan](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/scans/uswds.ts) - which looks for various US Web Design System elements within the page's source code, and also uses a formula to calculate the likelihood that USWDS is present on that page.  This populates the `USWDS - Favicon`, `USWDS - Favicon in CSS`, `USWDS - Merriweather Font`, `USWDS - Public Sans Font`, `USWDS - Source Sans Font`, `USWDS - Tables`, `USWDS - Count`, `USWDS - USA Classes`, `USWDS - Inline CSS`, `USWDS - String`, `USWDS - String in CSS`, `USWDS - Semantic Version`, and `USWDS - Version`	fields.


### DNS Scan 

- The IPv6 test looks within the DNS for the presence of an AAAA record.  This populates the `DNS - IPv6` field.  
- For the `hostname` field, only certain results that contain [one of these strings](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/pages/dns.ts#L66-L79) are included, so as to better highlight the most common cloud services.  This populates the `DNS - Hostname` field.  


### Not Found Scan
- A [random string](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/pages/not-found.ts#L13-L15) is added as a path after the Target URL to test how the site handles 404 errors.  This populates the `Target URL - 404 Test` field.  

### Robots.txt Scan 

`/robots.txt` is appended to the Target URL and loaded.  The scan then notes whether it redirects; what the Final URL is; whether it is live; what its server status code, filetype, and file size are; whether the Final URL is live and if the entire path is `/robots.txt`; what the robots.txt crawl delay is (if it is there); and what the urls of sitemaps listed in the robots.txt are. This populates the `Robots.txt - Detected`, `Robots.txt - Target URL - Redirects`, `Robots.txt - Final URL`, `Robots.txt - Final URL - Live`,`Robots.txt - Final URL - Status Code`, `Robots.txt - Final URL - Media Type`, `Robots.txt - Final URL - Filesize`, `Robots.txt - Crawl Delay`, and `Robots.txt - Sitemap Locations` fields.
  * For `Robots.txt - Final URL - Live` - it is marked `TRUE` if the final server status code is one of these - 200, 201, 202, 203, 204, 205, 206.
  * For `Robots.txt - Target URL - Redirects` - it is marked `TRUE` if the are one or more components in the redirect chain of the request method.  
  * For `Robots.txt - Detected`, the analysis looks at whether `Robots.txt - Final URL - Live` is `TRUE` for its decision (as opposed to the relevant server status code).


### Sitemap.xml Scan 

`/sitemap.xml` is appended to the Target URL and loaded.  The scan then notes whether it redirects; what the Final URL is; whether it is live; what its server status code, filetype, and file size are; whether the Final URL is live and if the entire path is `/sitemap.xml`; what the sitemap.xml item count is; and what count of urls ending in `.pdf` are in it. This populates the `Sitemap.xml - Detected`, `Sitemap.xml - Target URL - Redirects`, `Sitemap.xml - Final URL`, `Sitemap.xml - Final URL - Live`, `Sitemap.xml - Final URL - Status Code`, `Sitemap.xml - Final URL - Media Type`, `Sitemap.xml - Final URL - Filesize`, `Sitemap.xml - Items Count`, and `Sitemap.xml - PDF Count`fields.
  * For `Sitemap.xml - Final URL - Live` - it is marked `TRUE` if the final server status code is one of these - 200, 201, 202, 203, 204, 205, 206.
  * For `Sitemap.xml - Target URL - Redirects` - it is marked `TRUE` if the are one or more components in the redirect chain of the request method.  
  * For `Sitemap.xml - Detected`, the analysis looks at whether `Robots.txt - Final URL - Live` is `TRUE` for its decision (as opposed to the relevant server status code).

### Other Notes

- In the above folders, the x.ts files are the scans/scan components themselves and the x.spec.ts files are the test files.
