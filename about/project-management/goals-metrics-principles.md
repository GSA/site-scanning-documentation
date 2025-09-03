

## Goals

- Build and maintain the most complete, accurate index of federal, public websites.
- Scan those websites daily in order to generate a variety of useful data for known stakeholders.

### Internal program measures of success 

* Sites and repositories are current and all links work
* Scans are running daily
* Data quality had been analyzed and future steps for improvement are planned out 
* Primary stakeholders are caught up with and know next steps

## External program metrics 
* Website traffic  
* Data downloads 
* API calls
* Number of stakeholders being served 
* Number of estimated labor hours saved 

_Draft tracker spreadsheet [here](https://docs.google.com/spreadsheets/d/1rOU4jmFy5YhW_DTCf9E8wA-olUfM0Fye960qL43HqZo/edit?pli=1#gid=0)_

## Principles

- We work [in the open](https://github.com/GSA/site-scanning/issues).
- We only collect information that is available to anyone over the public internet.
- The program's products are machine-readable data files that are made publicly available, either as [static flat files or queryable APIs](https://digital.gov/guides/site-scanning/data/).
- We do not make presentation layers.
- We only design and build scans in response to user needs articulated by known stakeholders.
- All scans run against the complete [Federal Website Index](https://github.com/GSA/federal-website-index/blob/main/data/site-scanning-target-url-list.csv).
- If a scan is no longer needed or used by a known stakeholder, we deprecate it.
- We follow the [stakeholder experience](https://github.com/GSA/site-scanning-documentation/blob/main/about/stakeholder-experience.md).
- We prioritize reliability and accuracy of scans that we have launched.
- Our focus is on current data. Though scan data is [snapshotted to an archive repo](https://github.com/GSA/site-scanning-snapshots/tree/main/snapshots) once a month, our system is ruthlessly focused on best providing current data and not on being a warehouse for historical data.

## Internal Reliability Metrics
- All Target URLs included in Site Scanning data
- Number/Percent of scans completed
- Fields populated
- Total time of scanning

## Internal Engineering Principles
- Keep actions discrete and finite
- Fail gracefully
- If an action fails, the end result file should just not update
