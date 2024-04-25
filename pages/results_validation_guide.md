

Target URL: N/A  
Target URL - Base Domain: Extract the second level domain of the `Target URL`  
Target URL - Top Level Domain: Extract the top level domain of the `Target URL`   
Target URL - Redirects: ???   (possibly note if there's 2 or more entries in the network tab when the page is loaded, but need to test against meta redirets, etc.)  Note exact wording of how puppeteer does it.  
Final URL: Copy the `Target URL` into a browser's address bar, load the page, and note the last URL that resolves  
Final URL - Base Domain: Extract the second level domain of the Final URL   
Final URL - Top Level Domain: Extract the top level domain of the Final URL  
Final URL - Base Website: Extract the host from the Final URL (the part after the protocol and before the path)   
Final URL - Live: ???     (one of 200, 201, 202, 203, 204, 205, 206)
Final URL - Status Code: Open Chrome's Developer Tools; choose the Network tab, load the Target URL, and note the last (lowest) code in the Status column.    
Final URL - Media Type: Open Chrome's Developer Tools, choose the Network tab, load the Target URL, click on the last (lowest) Name, and look under Headers->Response Headers for the `Content-Type` field.  
Final URL - Same Base Domain As Target URL:  ???  (compares final url and target url)
Final URL - Same Base Website As Target URL:  ???    
Target URL - Base Domain Agency Owner: Take the `Target URL - Base Domain` field and compare it to the `Domain name` field [here](https://github.com/cisagov/dotgov-data/blob/main/current-federal.csv), then note the Agency column.  
Target URL - Base Domain Bureau Owner:  Take the `Target URL - Base Domain` field and compare it to the `Domain name` field [here](https://github.com/cisagov/dotgov-data/blob/main/current-federal.csv), then note the `Organization name` column.  
Target URL - Base Domain Branch:  Take the `Target URL - Base Domain` field and compare it to the `Domain name` field [here](https://github.com/cisagov/dotgov-data/blob/main/current-federal.csv), then note the `Domain type` column.  
Target URL - 404 Test: Open Chrome's Developer Tools; choose the Network tab, take the Target URL, apend a `/randomstringofcharacters` as a path, load the resulting combined URL, note the last (lowest) code in the Status column, and ???? 
Target URL - Data Source:  Check the [snapshots of the source files](https://github.com/GSA/federal-website-index/tree/main/data/snapshots#readme) that were generated at the most recent creation of the Federal Website Index and note whether the Target URL appears as a website in a particular file.  
Target URL - Public  
Scan Status - Date  
Scan Status - Primary  (derived from the error messages given back by the engine? - https://github.com/GSA/site-scanning-engine/blob/main/entities/scan-status.ts)
Scan Status - Accessibility  
Scan Status - DNS  
Scan Status - Not Found  
Scan Status - Performance  
Scan Status - Robots.txt  
Scan Status - Security  
Scan Status - Sitemap.xml  
Accessibility - Violations  
DNS - IPv6  
DNS - Hostname
Infrastructure - CMS Provider  
Infrastructure - Cloud.gov Pages Detected  
Infrastructure - Login Provider  
Infrastructure - Login Detected  
Infrastructure - Site Search Detected  - ??? If any element in the page is using a `usa-search` class.  it will look for the string search anywhere in an id, class, or action attribute within an input or form element. If it detects one, then the result will be TRUE. If not, FALSE.
Infrastructure - Search.gov Detected: View the page source and search for an HTML element that has an 'action' attribute which equals `https://search.usa.gov/search`.  
Infrastructure - DAP Detected  
Infrastructure - DAP Parameters  
Infrastructure - Third Party Service Domains  
Infrastructure - Third Party Service Count  
Infrastructure - Cookie Domains  
Mobile - Viewport Meta Tag Detected  
Performance - Cumulative Layout Shift  
Performance - Largest Contentful Paint  
Required Links - URL  
Required Links - Text  
Security - HTTPS Required  - Note the https_bad_hostname, https_expired_cert, and downgrades_https fields in the original file as  context for possible failures. 
Security - HSTS Preloaded  
SEO - title  
SEO - description  
SEO - keywords  
Open Graph - og:title  
Open Graph - og:description  
Open Graph - article:published_time  
Open Graph - article:modified_time  
Open Graph - og:image  
Open Graph - og:type  
Open Graph - og:url  
Other Tags - Canonical Link  
Other Tags - Language  
Other Tags - Language Links  
Other Tags - Main Element Detected  
Robots.txt - Detected  
Robots.txt - Target URL - Redirects  
Robots.txt - Final URL  
Robots.txt - Final URL - Live  
Robots.txt - Final URL - Status Code  
Robots.txt - Final URL - Media Type  
Robots.txt - Final URL - Filesize  
Robots.txt - Crawl Delay  
Robots.txt - Sitemap Locations  
Sitemap.xml - Detected  
Sitemap.xml - Target URL - Redirects  
Sitemap.xml - Final URL  
Sitemap.xml - Final URL - Live  
Sitemap.xml - Final URL - Status Code  
Sitemap.xml - Final URL - Media Type  
Sitemap.xml - Final URL - Filesize  
Sitemap.xml - Items Count  
Sitemap.xml - PDF Count  
USWDS - Favicon  
USWDS - Favicon in CSS  
USWDS - Public Sans Font  
USWDS - In-page CSS  
USWDS - USA Classes  
USWDS - String  
USWDS - String in CSS  
USWDS - Semantic Version  
USWDS - Version  
USWDS - Count  
