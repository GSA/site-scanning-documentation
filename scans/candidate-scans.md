This is a list of individual scans that _could_ be run with the Site Scanning program.  This is a brainstorming page and all ideas are welcome.  

The list of scans that have alreadby been built and are active is [here](https://github.com/18F/site-scanning-documentation/tree/master/scans#README).  Feel free to suggest further ideas by [editing this page](https://github.com/18F/site-scanning-documentation/edit/master/scans/candidate-scans.md), [filing an issue](https://github.com/18F/site-scanning/issues) or emailing us at site-scanning@gsa.gov.      

## Functional Scans for TTS Programs

* For data.gov
  * Replicate the data.json analysis done by the [Project Open Data Dashboard](https://labs.data.gov/dashboard/offices/qa) so that the data.gov team doesn't have to do it.   
* For the Digital Analytics Program
  * Detect CORS policy
  * Detect misconfigurations of the DAP snippet?  
  * Detect and analyze GTM implementations
* For the Feedback Analytics program
  * Priority - page load time, other performance data.
  * Monitor the adoption of Touchpoints.
* For ther US Digital Registry
  * Maybe some way to validate or authenticate offical government social media accounts? 
  * Find new social media accounts that need to be added to the registry by looking at all links in the page
* For search.gov
  * Scan for and analyze the search.gov snippet? 
  * Search for other major site scanning implementations 
* For TTS
  * Which websites use which TTS services


## Business Intelligence for TTS Programs

## Best practices
* More with Lighthouse
* Core Web Vitals
* Performance (perhaps addressed in ^^^) 
* Mobile-friendliness (perhaps addressed in ^^^) 
* a11y: Note that the legislative branch has a specific need, spelled out [here](https://www.congress.gov/bill/116th-congress/house-resolution/756/text#toc-HCE76E2BE29E84D5D8C2611BE41C479D0).  Note that there's a similar effort at 
https://www.feda11y.com/, run by former Pulse engineer Scott McAllister.  

## Technical Analysis
* Use of CDNs
* CMS


## Security
* DNS record certificate holder: Monitor changes in agency's DNS record certificate holder, and alert agencies if there are changes, which may be a sign of malicious behavior. 
* domain certificate transparency scanning (idea -  give a flag to openssl to have it check CT)
* CNAME Hijacking 
* OWASP - https://github.com/zaproxy/zaproxy
* HTTPS cert - [example of need](https://www.bloomberg.com/news/articles/2019-12-09/federal-regulations-website-goes-dark-blocking-public-input)
* Mozilla Observatory scans - https://observatory.mozilla.org/analyze/www.gsa.gov
* Owasp with an eye to detecting ability to redirect (or could be done without owasp) - _[note coverage of this](https://gizmodo.com/a-year-later-u-s-government-websites-are-still-redire-1835336087)_ - a.k.a. Open Redirectors?



## Policy Compliance
* /foia pages
  * Presence and characteristics of the pages
  * Are there possibly standards around XML files at certain locations?
* Privacy officers
  * more of the material from [these reports](https://www.dhs.gov/sites/default/files/publications/FY%202018%20SAOP%20FISMA%20Metrics-508c.pdf)
  * Presence of PII
  * Presence of forms 
  * Form fields (perhaps fed from a manually generated list of URLS)
  * For any of these scans that detect a machine readable file, copy and store in perpetuity the files themselves, so that powers that be can track trends.  
* /socialmediaTOS - Per [this](https://digital.gov/resources/federal-compatible-terms-of-service-agreements/#for-federal-agency-points-of-contact) and [this](https://www.whitehouse.gov/sites/whitehouse.gov/files/omb/memoranda/2013/m-13-10.pdf)
* more from fisma reports, as seen in [these](https://www.dhs.gov/sites/default/files/publications/FY%202018%20SAOP%20FISMA%20Metrics-508c.pdf) [questions](https://www.dhs.gov/publication/fy18-fisma-documents)

## Other
* Presence of forms
  * Analyze the source code of eage page that loads in order to detect forms and/or PRA numbers.
* 404 pages - Try to use the detection of 404 pages to discover broken links or websites.  For instance, one idea could be to take ever link found in a page and then check links for their status.  
* Well known services hosted by webservers:  [more info here](https://en.wikipedia.org/wiki/List_of_/.well-known/_services_offered_by_webservers) and [here](https://www.iana.org/assignments/well-known-uris/well-known-uris.xhtml)
* /security.txt ?
* data for GSA's privacy dashboard - https://github.com/18f/privacy-dashboard
* Social media pages: Uncover agency's social media pages for inclusion in the [U.S. Digital Registry](https://digital.gov/services/u-s-digital-registry/).
* HTML Metadata: Uncover HTML metadata, which could help to populate sub-domain scanning capabilities.
* Others from https://policy.cio.gov/.
* Contact information for a website (beyond perhaps what can be found on the [dotgov whois page](https://domains.dotgov.gov/dotgov-web/registration/whois.xhtml))
* Find phone numbers and email addresses on a page.
* Similar to services like siteimprove (used by gsa.gov team). 
* More from [thinking about involved javascript](https://timkadlec.com/remembers/2020-04-21-the-cost-of-javascript-frameworks/)
* others possibly could be found in [here](https://github.com/ombegov/policy-v2)
* any way to derive what the top tasks for sites might be?
* keywords? site summaries 
* links, aa, to same site, has words 'about', 'contact', etc.
* readability
* more from schema.org ?
* More from this [market research](https://docs.google.com/document/d/1hzNRRPL1SiJmw4EpTgXjtaPePnGZ0EFNPRyIWUxV6_Y/edit?pli=1).
* A replacement for statuspage
* Misc. ideas from Jay  -  CDNs; js Libraries - e.g. what % of the gov us using a (outdated) jQuery; 3rd Party Ads; % of sites that are PHP & Drupal and vulnerable to the drupalgeddon; % of sites that are a CMS (and it would be interesting to know which ones are not); % of sites w/ PDF forms (and tie to Rokus data + DAP usage)
* Add a layer to the data to reflect if the result has been human verified (perhaps with a date)
* A fetcher scan: to consume some foundational data that can be integrated into the other scans


## Other Scopes to Scan Against
* Run scans against second level domains, subdomains, and top 500 (or) 1000 pages in DAP.  Also, consider CFO act delineations, agency delineations, what else?
