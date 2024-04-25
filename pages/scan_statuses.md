
# Scan Statuses Explained
- **Completed** - The scan was able to run successfully.
- **Timeout** - When the headless browser loaded the Target URL, the request timed out (i.e. there's something at that URL, but it never finished loading).
- **DNS resolution error** - When the headless browser loaded the Target URL, the DNS request did not resolve (i.e. there's nothing at that URL accessible over the public internet).
- **Invalid SSL cert** - The Target URL's SSL certificate, used for HTTPS, is expired or not properly configured.
- **Connection refused** - When the headless browser loaded the Target URL, the site's server actively refused the connection request, blocking the scan engine.
- **Connection reset** - For an unknown reason, a part of the connection request failed either at the browser, computer, network, or server level.  
- **Unknown error** - An error occured that kept the scan from running successfully that is not one of the above.  


## Website Index Ingestion

- Target URL
- Target URL - Base Domain
- Target URL - Top Level Domain
- Target URL - Base Domain Agency Owner
- Target URL - Base Domain Bureau Owner
- Target URL - Base Domain Branch
- Target URL - Data Source
- Target URL - Public

## All/Any Scans

- Scan Status - Date


## Scan Status - Primary

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




## Scan Status - Not Found

- Target URL - 404 Test


## Scan Status - Accessibility

- Accessibility - Violations

## Scan Status - DNS

- DNS - IPv6
- DNS - Hostname



## Scan Status - Performance

- Performance - Cumulative Layout Shift
- Performance - Largest Contentful Paint







## Scan Status - Security


- Security - HTTPS Required
- Security - HSTS Preloaded

## Scan Status - Robots.txt


- Robots.txt - Detected
- Robots.txt - Target URL - Redirects
- Robots.txt - Final URL
- Robots.txt - Final URL - Live
- Robots.txt - Final URL - Status Code
- Robots.txt - Final URL - Media Type
- Robots.txt - Final URL - Filesize
- Robots.txt - Crawl Delay
- Robots.txt - Sitemap Locations

## Scan Status - Sitemap.xml


- Sitemap.xml - Detected
- Sitemap.xml - Target URL - Redirects
- Sitemap.xml - Final URL
- Sitemap.xml - Final URL - Live
- Sitemap.xml - Final URL - Status Code
- Sitemap.xml - Final URL - Media Type
- Sitemap.xml - Final URL - Filesize
- Sitemap.xml - Items Count
- Sitemap.xml - PDF Count



