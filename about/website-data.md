
## Proposed Data to be Gathered for each Website 

**[Bold = proposed for basic data]**

* **Scan date/time (when data is written)**
* **Count**
* **Target URL**
* **Base Domain of Target URL**
* **Final URL** 
* **Base Domain of Final URL**
* **Whether Final URL is live**
* **Whether the Target URL Redirects**
* Whether the Final URL has the same base domain as the Target URL
* Whether the Final URL has the same base website as the Target URL
* **Agency Owner of Target URL Base Domain**
* Office Owner of Target URL Base Domain 
* Branch (of government)
* Server Status Code of the Target URL
* Server Status Code of the Final URL
* Redirect Path 
* Server Codes at Each Step of the Redirect Path 
* Website Type, e.g. Agency Website/Bureau Website/etc.  (derived from a static separate dataset)
* URL Category, e.g. Staging/Not-A-Website/etc. (derived from a static separate dataset)
* OMB Agency/Bureau Code (derived from a static separate dataset)
* Customer of X TTS service, e.g. Search.gov, Data.gov, Code.gov, Login.gov, DAP, USWDS, api.data.gov, feedback analytics, etc. (derived from a static separate dataset)
* Is Target URL/redirecttest-foo-bar-baz live? 
* File size of the Final URL
* SEO components of Final URL - og date, unique title, Main element
* Whether DAP is detected at the Final URL
* What DAP parameters are detected at the Final URL

  
  
for 16 /somethings,   
  
* Final URL for x.gov/something
* Base Domain of Final URL for x.gov/something
* Whether Final URL is live for x.gov/something
* Whether the Target URL Redirects for x.gov/something
* Whether the Final URL has the same base domain as the Target URL for x.gov/something
* Whether the Final URL has the same base website as the Target URL for x.gov/something
* Server Status Code of the Target URL for x.gov/something
* Server Status Code of the Final URL for x.gov/something
* Redirect Path for x.gov/something
* Filesize of the Final URL 
* MIMEtype of the Final URL
  
For the 7 JSON /somethings.   
* how many objects are in them  
  
For the /sitemap.xml  
* number of items   
* number of pdf urls   
* ? (following into other sitemaps)?
  
For the /robots.txt  
* crawl delay   
* sitemap locations   
  
  
For the /data.json   
* conforms_to  
  
  
For the /code.json   
* measurementtype  
* version  
  
  
## Under consideration 

* Some things more along the lines of the federal org chart...
* human verified DAP?
* human verified USDWS (unnecc b/c of dataset of known users...) 
* human verified etc, etc. 
* number of datasets, releases in data.json/code.json 
* content length?
* Go ahead and think about other active scans now or no?




## Considered but rejected
* Agency Owner of Final URL Base Domain 
* Office Owner of Final URL Base Domain 
* Canonical URL
* Alternative URLs
* Program Code?




## To Consider 

* Add a 'Terms' section to this page.
* Should status scanner use final urls for x.gov in x.gov/something?
* Should Agency Website/Bureau Website be aligned to final or target url? 
* Should the dataset revolve around target urls or final urls - target
* Whether to scan for and analyze http/https/www/non-www for every target URL.  Answer: no. 
* Consider whether to incorporate the agency website/bureau code/tts customer/etc data fields in the subdomain generation process or in the scans.  
* Does 'Whether the Final URL has the same base website as the Target URL' make sense?  


### To Consider, 2
* https always? there's 3k http
* www always? there's 1.7k www
* Decide whether to have both x.gov and www.x.gov in the results? Etc. 


