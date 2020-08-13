This section documents active and inactive scans that have been built for the Site Scanning program. Each scanner exists as a file in the [scanners folder of the domain-scan project](https://github.com/18F/domain-scan/tree/master/scanners) (and the production scan engine sees which scans to run based on [this section of code](https://github.com/18F/Spotlight/blob/master/scan_engine.sh#L13-L22)).    A list of ideas for future scans to build [can be found here](/scans/candidate-scans.md).  

## Active

* [DAP Scan](/scans/live/DAP.md) - Checks for and analyzes the Digital Analytics Program snippet
* [Lighthouse Scan](/scans/live/lighthouse.md) - Runs numerous website health and best practice check 
* [Page Data Scan](/scans/live/pagedata.md) - Analyzes characteristics of the hosted files themselves
* [Privacy Page Scan](/scans/live/privacy.md) - Analyzes agency privacty policy pages
* [Security Scan](/scans/live/security.md) - Analyzes https and related website security 
* [Sitemap Scan](/scans/live/sitemap.md) - Checks for and analyzes robots.txt and sitemaps.xml files
* [Status Scan](/scans/live/status.md) - Checks for the presence or absence of a webpage or file
* [Third Party Services Scan](/scans/live/third-party.md) - Checks for the use of third party services on a page
* [U.S. Web Design System Scan](/scans/live/uswds.md) - Checks for and analyzes implementation of the US Web Design System. 


## Inactive 

* Accessibility - [[code](https://github.com/18F/domain-scan/blob/lighthouse-scan-initial/scanners/a11y.py)]
* Analytics - [[code](https://github.com/18F/domain-scan/blob/lighthouse-scan-initial/scanners/analytics.py)]
* CSP - [[code](https://github.com/18F/domain-scan/blob/lighthouse-scan-initial/scanners/csp.py)]
* SSLyze - [[code](https://github.com/18F/domain-scan/blob/lighthouse-scan-initial/scanners/sslyze.py)]
* trustymail - [[code](https://github.com/18F/domain-scan/blob/lighthouse-scan-initial/scanners/trustymail.py)]
* USWDS 1.0  - [[code](https://github.com/18F/domain-scan/blob/lighthouse-scan-initial/scanners/uswds.py)]


## Candidates for Future Scans 

* [Running list of ideas for future scans](/scans/candidate-scans.md)
