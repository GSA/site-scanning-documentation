
### Summary 

This document serves as a place to map out the proposed design and functionality of an overhauled [Site Scanning API](https://open.gsa.gov/api/site-scanning-api/).  Anyone should feel free to suggest ideas or ask questions below, or to file a pull request with proposed changes.  

### Resources


* [GSA API Standards](https://github.com/GSA/api-standards)  
* [18F API Standards](https://github.com/18F/api-standards) _[Secondary to the GSA standards]_  
* [Current API Documentation](https://open.gsa.gov/api/site-scanning-api/)

### General Thoughts 

* The fundamental unit of measurement is the Target URL (i.e. one of the 25,000 subdomains)
* It should be possible to query by base domain of target URL, base domain of final URL, redirect status, agency, website category [staging, etc.]
  * In other words, the most common filter options, not the more rare edge cases we can think of.  
* 


### Tasks

Filter results by 

https://github.com/18F/site-scanning-documentation/blob/main/about/website-data.md

### Data in an API Call

...

### Proposed Design 

Base URL: https://api.gsa.gov/technology/site-scanning/v1/  

* 
* 
* 
* 



### Other Ideas

...


### Questions 

* Should each data call contain all data fields for that Target URL?  Or should there be a way to call in X or Y set of data fields (e.g. expanded basic data, /something data, basic scan results, details of each scan results)

