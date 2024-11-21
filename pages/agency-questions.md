

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

## Can I request a new scan?  

Please!!  Every scan field that the Site Scanning program currently offers came into existence because a program or agency requested it.  Please check out our [Stakeholder Experience page](https://github.com/GSA/site-scanning-documentation/blob/main/about/stakeholder-experience.md) for perspective on how the team operates and  email [site-scanning@gsa.gov](mailto:site-scanning@gsa.gov) anytime!  


## Can I run Site Scanning against more pages on my websites or against internal sites?  

The hosted Site Scanning program is focused on scanning the homepage of public-facing federal websites for the foreseeable future.  That said, it's very straightforward to run a local instance of the Site Scanning engine off of a personal computer and laptop and when you do so, you can target and generate data for any webpages that you and your computer have access to.  Installation directions [can be found here](https://github.com/GSA/site-scanning-engine?tab=readme-ov-file#table-of-contents), but also feel free to contact the Site Scanning team at [site-scanning@gsa.gov](mailto:site-scanning@gsa.gov) if you have questions about how to do this yourself.  
