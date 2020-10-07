
### Summary 

This document serves as a place to map out the proposed design and functionality of an overhauled [Site Scanning API](https://open.gsa.gov/api/site-scanning-api/).  Anyone should feel free to suggest ideas or ask questions below, or to file a pull request with proposed changes.  

### Resources


* [GSA API Standards](https://github.com/GSA/api-standards)  _[Note especially #7]_
* [18F API Standards](https://github.com/18F/api-standards) _[Secondary to the GSA standards]_  
* [Current API Documentation](https://open.gsa.gov/api/site-scanning-api/)

### General Thoughts 

* The fundamental unit of measurement is the Target URL (i.e. one of the 25,000 subdomains)
* It should be possible to query by base domain of target URL, base domain of final URL, redirect status, agency, website category [staging, etc.]
  * In other words, the most common filter options, not the more rare edge cases we can think of.  
* The fundamental noun of the API should be `websites`. 
* Ensure the API Standards, including the [Other Considerations](https://github.com/GSA/api-standards#other-considerations).


### Tasks

Filter results by 

https://github.com/18F/site-scanning-documentation/blob/main/about/website-data.md

### Data in an API Call

...

### Proposed Design 

Base URL: https://api.gsa.gov/technology/site-scanning/v1/  

* `/websites` - Paginated return of all websites with the 8-15 'basic website data' fields included
* `/websites/datacategory` _[Where datacategory indicates which set of further data fields]_ - Paginated return of all websites with the basic data fields as well as with a set of the further data fields (see question 1 below).  
  * `datacategory` options = `expanded-general`, `locations`, `what else?`
* `/websites/targeturl/` _[Where targeturl indicates a specific Target URL]_ - The 'basic website data' fields for the target URL, e.g. `18f.gsa.gov`
* `/websites/targeturl/datacategory` - The 'basic website data' fields for the target URL that also includes a set of further data fields. 

**Query Options:**  

...


### Questions 

* Should each data call contain all data fields for that Target URL?  Or should there be a way to call in X or Y set of data fields (e.g. expanded basic data, /something data, basic scan results, details of each scan results, programs (e.g. dap, uswds, what else)) 
* If we had a /websites level to the API, should we have an (e.g.) /agencies level.  If so, what data fields would it have?
* Should we include in an API return for the basic data a data field that indicates that there's more data and links off to it.  

### Other Ideas

...

