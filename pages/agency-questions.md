

## What are the criteria for inclusion in the Federal Website Index, and thus the Site Scanning data?  

* Public (i.e. accessible over the public internet)
* Operating on a [federally-owned .gov domain](https://github.com/cisagov/dotgov-data/blob/main/current-federal.csv)
* Is a human-readable 'document' (e.g. HTML, TXT), not a machine-readable 'data file' (e.g. XML, JSON, CSV)
* Is not a staging or development website
* Is not an API endpoint, email server, or asset server
* Is not an authentication page to an otherwise non-public site


## A public federal .gov website is missing from the the Site Scanning Data.  How can I add it?  

Please email [site-scanning@gsa.gov](mailto:site-scanning@gsa.gov) with any websites that are missing that you think should be added!  After confirming that they meet the criteria for inclusion, we will add them to [this file](https://github.com/GSA/federal-website-index/blob/main/data/dataset/other-websites.csv), which will ensure that they are ingested in the weekly index rebuilding.   

## You include a website which should be filtered out.  How can I have it removed from the Site Scanning data?  

Please email [site-scanning@gsa.gov](mailto:site-scanning@gsa.gov) with any websites that you think should be removed, along with a few words as to why.  After confirming that they meet the criteria for exclusion, we will then add them to [this file](https://github.com/GSA/federal-website-index/blob/main/criteria/ignore-list-begins.csv), which will ensure that they are filtered out in the weekly index rebuilding.  
