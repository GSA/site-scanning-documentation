
This is a description of the step-by-step technical process by which we 'scan' each Target URL.  For information on the process of building the Target URL list, go [here](https://github.com/GSA/federal-website-index/blob/main/process/index-creation.md).  

* Order of scans 
  * For each scan, order of operations 
    * For each operation - a human readable but technical description of what happens and what data fields are written
    * For each operation - a link to the source code 
  * For each scan, a link to the source code  
* Link to the order of scans  


First off, before any scans take place, the process of ingesting the target URL list into the database populates the following fields: 
* `Target URL`
* `Target URL - Base Domain`
* `Target URL - Top Level Domain`
* `Target URL - Base Domain Agency Owner`
* `Target URL - Base Domain Bureau Owner`
* `Target URL - Base Domain Branch`
* `Target URL - Data Source`

When scanning commences, [this core file](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/core-scanner.service.ts#L36) dictates which scans are run.  Due to the nature of the code base, the scans run asynchronously (i.e. they don't necessarily run in the order they are written in the code). Each scan operates separately and don't talk to each other.  

The primary scan uses [Puppeteer](https://pptr.dev/) to load a target URL in a headless Chrome/Chromium browser.  It then (again asynchronously) runs a number of what might be thought of as scan components, the list of which can be found [here](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/pages/primary.ts#L48-L58) and the code for which can be found [here](https://github.com/GSA/site-scanning-engine/tree/main/libs/core-scanner/src/scans).  

At the moment, these 'scan components' are: 
* [urlScan](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/scans/url-scan.ts) - which notes whether the Target URL redirects; what the Final URL is; whether it is live; what its server status code, filetype, and base domain are; and whether the Final URL is on the same domain and same website as the Target URL. This populates the `Final URL`, `Final URL - Base Domain`, `Final URL - Base Website`, `Final URL - Top Level Domain`, `Final URL - Media Type`, `Final URL - Live`, `Target URL - Redirects`, `Final URL - Same Base Domain As Target URL`, `Final URL - Same Base Website As Target URL`, and `Final URL - Status Code` fields.  
* [dapScan](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/scans/dap.ts) - which captures the outbound requests that occur when the target URL loads and notes whether a call using the Digital Analytics Program tag IDs ('UA-33523145-1' or 'G-9TNNMGP8WJ') is one of them.  If it is, the Google Analytics parameters are also captured.  This then populates the `DAP - Final URL` and `DAP - Parameters - Final URL` fields.  
* [seoScan](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/scans/seo.ts) - which looks for various search engine optimization elements within the page's source code.  This populates the `SEO - article:published_time - Final URL`, `SEO - article:modified_time - Final URL`, `SEO - og:title - Final URL`, `SEO - og:description - Final URL`, and `SEO - Main Element - Final URL` fields.  
* [thirdPartyScan](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/scans/third-party.ts) - which captures the outbound requests that occur when the target URL loads, notes them, and counts how many unique third party services they represent.  This populates the `Third Party - Service Domains` and `Third Party - Count` fields.  
* [uswdsScan](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/scans/uswds.ts) - which lookos for various US Web Design System elements within the page's source code, and also uses a formula to calculate the likelihood that USWDS is present on that page.  This populates the `USWDS - Favicon`, `USWDS - Favicon in CSS`, `USWDS - Merriweather Font`, `USWDS - Public Sans Font`, `USWDS - Source Sans Font`, `USWDS - Tables`, `USWDS - Count`, `USWDS - USA Classes`, `USWDS - Inline CSS`, `USWDS - String`, `USWDS - String in CSS`, `USWDS - Semantic Version`, and `USWDS - Version`	fields.  
* loginScan
    
    

* The technical details of how each scan operates can be found in the following locations: 
  * [primary](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/pages/primary.ts)  (and then [here](https://github.com/GSA/site-scanning-engine/tree/main/libs/core-scanner/src/scans))
  * [notFound](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/pages/not-found.ts)
  * [robotsTxt](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/pages/robots-txt.ts)
  * [sitemapXml](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/pages/sitemap-xml.ts)
  * [dns](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/pages/dns.ts)






Key file - https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/core-scanner.service.ts






for the other four - scan source code is in - https://github.com/GSA/site-scanning-engine/tree/75d5b532c556291353b3dd73fbc4fd2fa3b4a214/libs/core-scanner/src/pages




url scans -  https://github.com/GSA/site-scanning-engine/blob/75d5b532c556291353b3dd73fbc4fd2fa3b4a214/libs/core-scanner/src/scans/url-scan.ts#L21-L29
it's being passed the http response that's being received by the browser and then pulls out these figures.  



for dap, we capture the outbound requests that take place, via a different scan ([code](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/scans/dap.ts)).  




For the robotsTXT scan, 

...

For the sitemapxml scan,  

...

For the notFound scan,  

...
doesn't use puppeteer - uses an https service that is passed through to it.  

random url suffix is generated at this point - https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/pages/not-found.ts#L13-L14

For the dns scan, 

for the hostnames, only [this list](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/pages/dns.ts#L66-L79).  

...

doesn't use puppeteer - uses a node.js library 

for cms - it uses the primary scan, and [this regex library](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/scans/cms.ts) and scans the response body (not any linked assets though) for the snippets.  


for the required links scan 
https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/scans/required-links.ts#L10

for cms scan 

https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/scans/cms.ts

for login detection - 

https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/scans/login.ts


target url redirects - looks at the redirect chain in the request method  and if there is 1 or more components to it, then it is considered to have redirected.  

final url = live.  if the final server status code is one of these - 200, 201, 202, 203, 204, 205, 206

404 test - appends to the end /not-found-test${uuid} where uuid is a random string

for dns hostname, we only include if the domain of the hostname includes a string from here - https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/pages/dns.ts#L66-L79

for cms scan, we search the html and headers using the rubric linked above 



cloud.gov pages - we look to see if there's an x-server response header that says cloud.gov pages 


sidenote - the x.ts files are the scans and the x.spec.ts files are the test cases 


entire chain of server status codes and notes whether any of them inclue a 3xx code.  


uses puppeteer's built in cookie method to note all of the cookies that load 


viewport meta tag on for a long time, looking at the html 


for robots and sitemap detected, looks at whether live = true instead directly at server status code 


scan status codes 
