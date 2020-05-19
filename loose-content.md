

Assorted loose content and documentation that I need to find a home for...

scan-website.md

## Overview

This project is in the alpha stage.  Version 1.0 will be what we are comfortable sharing widely with other agencies and will mark the transition of the project to the beta stage (where it will likely stay indefinitely).  

## Version History

### v 0.3 

* Added individual pages for each 200 scanner 
* Added a /developer page 
* Added an /about page
* Added JSON and CSV export options 


### v 0.2

* Created a combined website that brought together the different scan results pages and created a combined home.
* Created the 200 scanner search page
* Created the USWDS scanner search page 


### v 0.1

* The initial rough MVP that we threw together to get started.  








Project History







## Summary

#### Current Versions
* 200 Scan - v0.2 is live. We've gotten feedback from stakeholders on it and are working on v0.3.  
* Code.json Scan - v0.2 is live.  We've gotten feedback from stakeholders on it and are working on v0.3.  
* Data.json Scan - v0.2 is live.  We've gotten feedback from stakeholders on it and are working on v0.3.  
* Data Hub Scan - v0.2 is live.  We've gotten feedback from stakeholders on it and are working on v0.3.  
* Developer Hub Scan - v0.2 is live.  We've gotten feedback from stakeholders on it and are working on v0.3.  
* Search Scan - v0.2 is live.  We've gotten feedback from stakeholders on it and are working on v0.3.  
* Privacy Page Scan - v0.2 is live.  We've gotten feedback from stakeholders on it and are working on v0.3.  
* USWDS Scan - v0.2 is live.  We've gotten feedback from stakeholders on it and are working on v0.3.  
* DAP Scan - v0.1 is live.  We're currently getting feedback from stakeholders on it.  
* Third Party Services Scan - v0.1 is live.  We're currently getting feedback from stakeholders on it.  


## Details 


#### 200 Scan 



#### Code.json Scan


#### Data.json Scan  


#### Data Hub Scan   


#### Developer Hub Scan 


#### Search Scan 


#### Privacy Page Scan 


#### USWDS Scan 


#### DAP Scan 


#### Third Party Services Scan 








### Prototypes

- [**200 scanner**](https://site-scanning.app.cloud.gov/search200/) - Checks domains for the presence or absence of a file at a specific location, specifically by analyzing the server response code at that location, such as x.gov/code.json, x.gov/data.jason, x.gov/data, x.gov/developer, x.gov/digitalstrategy, x.gov/open, x.gov/privacy, x.gov/robots.txt, x.gov/sitemap.xml
- [**U.S. Web Design System**](https://site-scanning.app.cloud.gov/searchUSWDS/) - Checks domains for the presence or absence of U.S. Web Design System (USWDS) components and USWDS version in use.



## Milestones

| Rank          | Priority      | Goal          | Measure       |
| ------------- | ------------- |-------------  | ------------- |
| 1 | 1  | Data prototype returns data stakeholder(s) find useful and can take action on  | 1. Data - Discover data to incorporate on data.gov; show agency compliance with OPEN Data law; 2. APIs - Discover APIs to incorporate on API.data.gov; show agency compliance with White House Memos  |
| 2  | 2  | Prototype is built and documented to make it extensible and replicable  | Individual can either stand-up their own copy or add their own scan  |
| 3  | 2  | Path to scale prototype (if successful) is in place  | Recommendations for 10x phase III funding; recommendations for future scans; lessons learned; long-term data storage recommendations|







This section documents scans that are active in the Site Scanning program. Scans that are no longer active [can be found here](https://github.com/18F/site-scanning/tree/master/docs/scanners/inactive). A list of candidate scans [can be found here](https://github.com/18F/site-scanning/blob/master/docs/candidate-scans.md).

* [200 Scanner](https://github.com/18F/site-scanning/blob/master/docs/scanners/200.md)
* [U.S. Web Design System](https://github.com/18F/site-scanning/blob/master/docs/scanners/uswds.md)

### Links to Live Scans

* [Scans Search Home](https://site-scanning.app.cloud.gov/)
* [USWDS Scanner](https://site-scanning.app.cloud.gov/searchUSWDS/)
* [200 Scanner](https://site-scanning.app.cloud.gov/search200/)




[Need to reconcile the below with [this PR](https://github.com/18F/Spotlight/pull/235/files?short_path=f4f345e#diff-f4f345ecfbfad8b4a5e7f07760103195)]

# U.S. Web Design System (USWDS) Scanner

## Summary
A [scan](https://site-scanning.app.cloud.gov/searchUSWDS/) to check each domain for the presence or absence of a USWDS component (i.e. font, style sheet) and the version in use of USWDS.

Specifically, the scan [searches for](https://github.com/18F/domain-scan/blob/tspencer/200scanner/scanners/uswds2.py#L36-L123): presence of `-usa` class in the style sheets, `uswds` in HTML, `.usa-` in HTML, `favicon-57.png` (the USWDS flag) on a website, the fonts used by USWDS (current and former versions) - `Public Sans`, `Source Sans`, and `Merriweather` — `uswds` or `uswds version` or `flavicon-57.png` in CSS. It also searches for the presence of HTML tables, although it uses those as a negative indicator that a site is using USWDS.

* USWDS adoption
* USWDS configuration

## Details

This scanner uses the presence of various elements as votes for or against a site employing USWDS. The use of USWDS is not binary — it's possible to employ limited aspects of the USWDS, since it amounts to a sort of a toolkit — so in practice we shouldn't say whether a site does or does not use USWDS, but instead how "USWDS-y" it is. The effect of this is that a count is returned, rather than a yes/no. The highest counts are around 150, and the floor is set at 0. The mode count is 0. Different elements are weighted differently, e.g. the appearance of the `Source Sans` or `Merriweather` fonts is worth less than the appearance of the `Public Sans` font, because the former two are commonplace, while the latter is bespoke for USWDS.

Scoring is performed slightly differently on the presence of `usa-*` CSS classes — those tags could reasonably appear as few as 10 times or as many as 100+, so those are tallied and the recorded count is based on the square root of the count, e.g. 36 becomes 6, 64 becomes 8, etc. (This is then multiplied by 5, weighting this metric highly.) The idea is to reduce count mobility as the count increases.

There is one scanned-for element that _reduces_ the counts — the presence of `<table>` in the HTML. Every table found on the home page is worth -10 points. At present, no sites using USWDS have a table on their home page.

### USWDS adoption

#### Summary
Detects whether USWDS is in use on an agency website.

#### Relevant Policy
"An executive agency that creates a website or digital service that is intended for use by the public, or conducts a redesign of an existing legacy website or digital service that is intended for use by the public, shall ensure to the greatest extent practicable that any new or redesigned website, web-based form, web-based application, or digital service has a consistent experience - _[21st Century Integrated Digital Experience Act](https://www.congress.gov/bill/115th-congress/house-bill/5759/text)_

#### Stakeholders
* OMB - Automates a part of the compliance review for [21st Century Integrated Digital Experience Act](https://www.congress.gov/bill/115th-congress/house-bill/5759/text)

#### Sample Data File

TBA

### USWDS configuration

#### Summary
Detects whether USWDS is in use on a government website and, if so, what version.

#### Relevant Policy
"An executive agency that creates a website or digital service that is intended for use by the public, or conducts a redesign of an existing legacy website or digital service that is intended for use by the public, shall ensure to the greatest extent practicable that any new or redesigned website, web-based form, web-based application, or digital service has a consistent experience - _[21st Century Integrated Digital Experience Act](https://www.congress.gov/bill/115th-congress/house-bill/5759/text)_

#### Stakeholders
* OMB - Automates a part of the compliance review for [21st Century Integrated Digital Experience Act](https://www.congress.gov/bill/115th-congress/house-bill/5759/text)

#### Sample Data File

TBA

#### Other Notes
* [Human curated list of USWDS sites](https://designsystem.digital.gov/getting-started/showcase/all/)



#### Version Tracking


##### v 0.3

* Added organization field
* Implemented [2nd pass at counting rubric](https://github.com/18F/domain-scan/pull/315)

##### v 0.2

* Fixed bug that was wrongly associating 404 and 500 server codes with 200
* Added domaintype and agency 
* Refined the counting model

##### v 0.1

* The initial rough MVP that we threw together to get started.



