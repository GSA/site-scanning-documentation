
# Scan Statuses Explained (technical status in parenthesis; remediation in sub-bullet) 
- **Completed** - The scan was able to run successfully.
  - No remediation needed.  
- **Address Unreachable** - Often the result of a site no longer existing.  (ERR_ADDRESS_UNREACHABLE)
  - Check the website's status.  
- **Connection closed** - Often the result of a a server/hosting service flaw or the site no longer existing. (ERR_CONNECTION_CLOSED)
  - Check the website's status.  
- **Connection refused** - When the headless browser loaded the Target URL, the site's server actively refused the connection request, blocking the scan engine. (ERR_CONNECTION_REFUSED; ECONNREFUSED)
  - Check the website's status.  
- **Connection reset** - For an unknown reason, a part of the connection request failed either at the browser, computer, network, or server level. (ERR_CONNECTION_RESET; ECONNRESET)
  - Check the website's status.  
- **DNS resolution error** - When the headless browser loaded the Target URL, the DNS request did not resolve (i.e. there's nothing at that URL accessible over the public internet). (ERR_NAME_NOT_RESOLVED; ENOTFOUND)
  - Check the website's status.  
- **Empty Response** - The website does not return any data. (ERR_EMPTY_RESPONSE)
  - Check the website's status.  
- **Evaluation Failed** - Puppeteer experienced an error while attempting to perform a scan.  (Evaluation failed)
  - The Site Scanning engine failed.  
- **Execution Context Destroyed** - Puppeteer experienced an error because the page it was scanning changed after the scan began, possibly due to further navigation. (Execution context was destroyed) 
  - The Site Scanning engine failed.  
- **HTTP2 Error** - Often the result of the website not supporting HTTP2 or an SSL configuration. (ERR_HTTP2_PROTOCOL_ERROR)
  - Ask your agency's network team to check for and remedy an HTTP2 protocol error.  
- **Invalid SSL cert** - The Target URL's SSL certificate, used for HTTPS, is expired or not properly configured. (ERR_CERT_COMMON_NAME_INVALID; ERR_CERT_DATE_INVALID; ERR_BAD_SSL_CLIENT_AUTH_CERT; unable to verify the first certificate)
  - Ask your agency's network team to check for and remedy any issues with the HTTPS/HSTS configuration for the site.  
- **Page Frame Not Ready** - Specific to the accessibility scans, this status indicates that page or an element did not finish loading and could not be scanned. (Page/Frame is not ready)
  - The Site Scanning engine failed.  
- **SSL Version Cipher Mismatch** - Often the result of invalid or misconfigured SSL certificates.  (ERR_SSL_VERSION_OR_CIPHER_MISMATCH)
  - Ask your agency's network team to check for and remedy any issues with the HTTPS/HSTS configuration for the site.  
- **Timeout** - When the headless browser loaded the Target URL, the request timed out (i.e. there's something at that URL, but it never finished loading).  (ERR_CONNECTION_TIMED_OUT; ETIMEDOUT)
  - 
- **Too Many Redirects** - A misconfiguration of the server, page source, or third party services is causing an infinite redirect loop. This requires correction by the site owner.   (ERR_TOO_MANY_REDIRECTS)
  - Ask your website's technical owner to investigate the redirect chain of the site.  
- **Unknown error** - An error occured that kept the scan from running successfully that is not one of the above.  



# Which Fields Come From Which Scan

### [These fields are generated when the index is first ingested and not by a scan]

- Target URL
- Target URL - Base Domain
- Target URL - Top Level Domain
- Target URL - Base Domain Agency Owner
- Target URL - Base Domain Bureau Owner
- Target URL - Base Domain Branch
- Target URL - Data Source
- Target URL - Public
- Scan Status - Date

### Scan Status - Primary

- Target URL - Redirects
- Final URL
- Final URL - Base Domain
- Final URL - Top Level Domain
- Final URL - Base Website
- Final URL - Live
- Final URL - Status Code
- Final URL - Media Type
- Final URL - Same Base Domain As Target URL
- Final URL - Same Base Website As Target URL
- Infrastructure - CMS Provider
- Infrastructure - Cloud.gov Pages Detected
- Infrastructure - Login Provider
- Infrastructure - Login Detected
- Infrastructure - Site Search Detected
- Infrastructure - Search.gov Detected
- Infrastructure - DAP Detected
- Infrastructure - DAP Parameters
- Infrastructure - Third Party Service Domains
- Infrastructure - Third Party Service Count
- Infrastructure - Cookie Domains
- Mobile - Viewport Meta Tag Detected
- Required Links - URL
- Required Links - Text
- SEO - title
- SEO - description
- SEO - keywords
- Open Graph - og:title
- Open Graph - og:description
- Open Graph - article:published_time
- Open Graph - article:modified_time
- Open Graph - og:image
- Open Graph - og:type
- Open Graph - og:url
- Other Tags - Canonical Link
- Other Tags - Language
- Other Tags - Language Links
- Other Tags - Main Element Detected
- USWDS - Favicon
- USWDS - Favicon in CSS
- USWDS - Public Sans Font
- USWDS - In-page CSS
- USWDS - USA Classes
- USWDS - String
- USWDS - String in CSS
- USWDS - Semantic Version
- USWDS - Version
- USWDS - Count




### Scan Status - Not Found

- Target URL - 404 Test


### Scan Status - Accessibility

- Accessibility - Violations

### Scan Status - DNS

- DNS - IPv6
- DNS - Hostname



### Scan Status - Performance

- Performance - Cumulative Layout Shift
- Performance - Largest Contentful Paint







### Scan Status - Security


- Security - HTTPS Required
- Security - HSTS Preloaded

### Scan Status - Robots.txt


- Robots.txt - Detected
- Robots.txt - Target URL - Redirects
- Robots.txt - Final URL
- Robots.txt - Final URL - Live
- Robots.txt - Final URL - Status Code
- Robots.txt - Final URL - Media Type
- Robots.txt - Final URL - Filesize
- Robots.txt - Crawl Delay
- Robots.txt - Sitemap Locations

### Scan Status - Sitemap.xml


- Sitemap.xml - Detected
- Sitemap.xml - Target URL - Redirects
- Sitemap.xml - Final URL
- Sitemap.xml - Final URL - Live
- Sitemap.xml - Final URL - Status Code
- Sitemap.xml - Final URL - Media Type
- Sitemap.xml - Final URL - Filesize
- Sitemap.xml - Items Count
- Sitemap.xml - PDF Count



