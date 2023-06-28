This is a list of individual scans that _could_ be run with the Site Scanning program.  This is a brainstorming page and all ideas are welcome.  

The list of scans that have alreadby been built and are active [can be found here](https://digital.gov/guides/site-scanning/understand-the-data/).  Feel free to suggest further ideas though by [editing this page](https://github.com/GSA/site-scanning-documentation/edit/main/pages/candidate-scans.md), [filing an issue](https://github.com/GSA/site-scanning/issues) or emailing us at site-scanning@gsa.gov.      


* Other IPv6? [Note the NIST site](https://fedv6-deployment.antd.nist.gov/).  


## Functional Scans for TTS Programs

* For data.gov:
  * Replicate the data.json analysis done by the [Project Open Data Dashboard](https://labs.data.gov/dashboard/offices/qa) so that the data.gov team doesn't have to do it.   
* For the Digital Analytics Program:
  * Whether migrated to GA4.
  * Detect CORS policy.
  * Detect subagency filter.
  * Detect misconfigurations of the DAP snippet?  
  * Detect and analyze GTM implementations.
  * Note if it is registered in the analytics.usa.gov export. 
  * Add in GA traffic data. 
* For the Feedback Analytics program:
  * Priority - page load time, other performance data.
  * Monitor the adoption of Touchpoints.
  * Presence of forms.
    * Analyze the source code of eage page that loads in order to detect forms and/or PRA numbers.  (a lot more technical detail on ways to do this [here](https://github.com/18F/site-scanning/issues/438)).
* For the US Digital Registry:
  * Maybe some way to validate or authenticate offical government social media accounts? 
  * Find new social media accounts that need to be added to the registry by looking at all links in the page.
  * List of all hyperlinks on the page.  
  * List of all domains that have hyperlinks on the page. 
  * List of all email addresses (both text and in mailto: links) in the page
  * A more radical idea - take over what it does by consuming social_media.json files.  Relevant mainly if there's ever a future need to deprecate it's primary engine.  
* For search.gov:
  * Implement the search scan that Carter built for them internally.
  * Scan for CMS (site-inspector, builtwith API).
  * Have our scan data serve a domain owner to prepare and know that they are ready to move websites or make another major change.
  * Or, have a series of datapoints that get to what they look for each time.  E.g. Is domain of entries the same as the domain. 
  * Scan for last mod date (of the sitemap/robot files?).
  * Scan for and analyze the search.gov snippet? 
  * Search for other major site scanning implementations. 
* For USWDS: 
  * Try to highlight bad, resolving urls to the same end, e.g. www1 and www.
  * Ingest a YML file of their known users to indicate human-verified.
* For login.gov:
  * Presence of a sign in form.
  * Which signup form solution is used.
  * Whether the form employs 2FA.
* For TTS:
  * Which websites use which TTS services.
    * E.g. for federalist, "curl --head https://<URL>" and examining the result for the line that says "X-Server: Federalist".
  * High level numbers - e.g. what percent of each agency's sites have implemented DAP; avg. USWDS total; etc.
  * Incorporate DAP analytics.


## Business Intelligence for TTS Programs
 
#### 21st century idea - MVP scan possibilities 
* a11y
* Same page title?
* Has some search capacity
* More ssl
* library of customer service, analytics third party services
* mobile header?
 
* [Also, if they required implementation reports being in a machine readable, fixed location - we could analyze that report]
 
 
## Best Practices
* More with Lighthouse (list [here](/scans/live/lighthouse.md#details)).
  * Example lighthouse scan [here](https://googlechrome.github.io/lighthouse/viewer/?psiurl=https%3A%2F%2Fwww.gsa.gov); [Scoring methodology](https://github.com/GoogleChrome/lighthouse/blob/main/docs/scoring.md)
* Core Web Vitals (interest by leadership and relevance to Google search results [[note](https://9to5google.com/2020/11/10/google-search-page-speed/)]).
* Performance (perhaps addressed in ^^^). 
* Mobile-friendliness (perhaps addressed in ^^^) - also, note possible IDEA Act dashboard needs.
* A11y: Note that the legislative branch has a specific need, spelled out [here](https://www.congress.gov/bill/116th-congress/house-resolution/756/text#toc-HCE76E2BE29E84D5D8C2611BE41C479D0).  Note that there's a similar effort at https://www.feda11y.com/, run by former Pulse engineer Scott McAllister.  
* The entire redirect path.
* Scan for problematic or un-inclusive language.
* Scan for plainlanguage (there's a variety of potentially scannable items in https://www.plainlanguage.gov/guidelines).
* Scan for a11y, for tts programs as part of their before-you-ship (there's interest).


## Technical Analysis
* Use of CDNs.
* Other things we could look up from DNS lookup that we're already doing.  
* wappalyzer


## Security
* presence of a vulnerability disclosure policy
* DNS record certificate holder: Monitor changes in agency's DNS record certificate holder, and alert agencies if there are changes, which may be a sign of malicious behavior. 
* Reach out to Hillary J., who is now at CISA to get thoughts.  
* Domain certificate transparency scanning (idea -  give a flag to openssl to have it check CT).
* CNAME Hijacking. 
* OWASP - https://github.com/zaproxy/zaproxy.
* HTTPS cert - [example of need](https://www.bloomberg.com/news/articles/2019-12-09/federal-regulations-website-goes-dark-blocking-public-input).
* Mozilla Observatory scans - https://observatory.mozilla.org/analyze/www.gsa.gov.
* Owasp with an eye to detecting ability to redirect (or could be done without owasp) - _[note coverage of this](https://gizmodo.com/a-year-later-u-s-government-websites-are-still-redire-1835336087)_ - a.k.a. Open Redirectors?
* What libraries does a website pull in?  Note that CISA would be interested in this.  
* Glue records?  (note details [here](https://groups.google.com/u/1/a/gsa.gov/g/spotlight/c/b3Kkla4qrbA))

### Privacy
 * Referrer policy (affects what is sent to 3rd parties).

## Policy Compliance
* /foia pages:
  * Presence and characteristics of the pages.
  * Are there possibly standards around XML files at certain locations?
* Privacy officers:
  * more of the material from [these reports](https://www.dhs.gov/sites/default/files/publications/FY%202018%20SAOP%20FISMA%20Metrics-508c.pdf).
  * Presence of PII.
  * Presence of forms. 
  * Form fields (perhaps fed from a manually generated list of URLS).
  * For any of these scans that detect a machine readable file, copy and store in perpetuity the files themselves, so that powers that be can track trends. 
* /socialmediaTOS - Per [this](https://digital.gov/resources/federal-compatible-terms-of-service-agreements/#for-federal-agency-points-of-contact) and [this](https://www.whitehouse.gov/sites/whitehouse.gov/files/omb/memoranda/2013/m-13-10.pdf).
* More from fisma reports, as seen in [these](https://www.dhs.gov/sites/default/files/publications/FY%202018%20SAOP%20FISMA%20Metrics-508c.pdf) [questions](https://www.dhs.gov/publication/fy18-fisma-documents).
* Required links -  About page = “About us OR About”; Contact page = “Contact us”; Accessibility = “Accessibility”; budget/perf = “Budget and Performance”; Equal employment = “No FEAR Act Data”; FOIA = “FOIA or Freedom of Information Act”; Usa.gov link; Privacy = “Privacy Policy”;  IG = “Office of Inspector General”; ?presence of a search bar by searching for the word 'search' (or in a button, or text field?)?

## Other
* Blacklight scans.
* Links to translated sites or other language options 
* Whether a subdomain is a website or a system.
* 3rd party services/performance/? for pages like [this](https://web.archive.org/web/20200716162116/https://www.performance.gov/cx/dashboard/va/vha/).
* 404 pages - Try to use the detection of 404 pages to discover broken links or websites.  For instance, one idea could be to take ever link found in a page and then check links for their status.  
* Well known services hosted by webservers:  [more info here](https://en.wikipedia.org/wiki/List_of_/.well-known/_services_offered_by_webservers) and [here](https://www.iana.org/assignments/well-known-uris/well-known-uris.xhtml).
* /security.txt ?
* Bad SEO/website management in the form of duplicative URLs to the same webpage, e.g. with and without and www., or 2 domains that are CNAMED to the same thing.  
* Data for GSA's privacy dashboard - https://github.com/18f/privacy-dashboard.
* Social media pages: Uncover agency's social media pages for inclusion in the [U.S. Digital Registry](https://digital.gov/services/u-s-digital-registry/).
* HTML Metadata: Uncover HTML metadata, which could help to populate sub-domain scanning capabilities.
* Others from https://policy.cio.gov/.
* Contact information for a website (beyond perhaps what can be found on the [dotgov whois page](https://domains.dotgov.gov/dotgov-web/registration/whois.xhtml)).
* Find phone numbers and email addresses on a page.
* Similar to services like siteimprove (used by gsa.gov team). 
* More from [thinking about involved javascript](https://timkadlec.com/remembers/2020-04-21-the-cost-of-javascript-frameworks/).
* Others possibly could be found in [here](https://github.com/ombegov/policy-v2).
* Any way to derive what the top tasks for sites might be?
* A list of all links on the page, to help with sunsetting websites.
* List of links (or text) in the menu?  list of menu headers? list of links (or hyperlinked text) in the footer? 
* count of h1s, h2s, h3s
* Links that have words 'about', 'contact', etc. in them.
* Readability.
* More from schema.org ?
* More from this [market research](https://docs.google.com/document/d/1hzNRRPL1SiJmw4EpTgXjtaPePnGZ0EFNPRyIWUxV6_Y/edit?pli=1).
* A replacement for statuspage.
* Misc. ideas from Jay  -  CDNs; js Libraries - e.g. what % of the gov us using a (outdated) jQuery; 3rd Party Ads; % of sites that are PHP & Drupal and vulnerable to the drupalgeddon; % of sites that are a CMS (and it would be interesting to know which ones are not); % of sites w/ PDF forms (and tie to Rokus data + DAP usage).
* What % of federal .gov websites are hosted on Code.gov?" and/or What % of websites hosted on code.gov that utilize the USWDS (per code.gov) are correctly scanned by the web scanner?
* Finding new .org, .com, .net federal websites to add to https://github.com/GSA/govt-urls.
* Add a layer to the data to reflect if the result has been human verified (perhaps with a date).
* A fetcher scan: to consume some foundational data that can be integrated into the other scans.
* Finding geospatial tools like https://resources.hud.gov/.
* Add in a layer to offer a real, simple and usable nested list of federal agencies, a la https://github.com/unitedstates/orgchart/tree/master/wikipedia.
* Add a layer of metadata if an agency has a machine-readable websites.yml file at a fixed location that would enable one to filter for that agencies list of websites.

## Other Scopes to Consider Scanning Against
* Run scans against second level domains, subdomains, and top 500 (or) 1000 pages in DAP.  Also, consider CFO act delineations, agency delineations, what else?
* Create individual add-on lists for individual scans that would allow people to append further urls to scan to the target list for that scan.
* Reach out to .mil again to see if they are interested.  Note this [list]([url](https://www.defense.gov/Resources/Military-Departments/DOD-Websites/)).  
* Integrating [the non-.gov and non-.mil websites](https://github.com/GSA/govt-urls/blob/master/2_govt_urls_federal_only.csv).
