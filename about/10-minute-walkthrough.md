## Background

There's roughly 280 US Federal agencies and they operate about 25,000 websites on 1,200 domains.  The Site Scanning program serves to make available an increasing range useful data about those websites.  

* Here's the [ program website](https://digital.gov/site-scanning).  
* Here's [some history of earlier government-wide scanning efforts](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/project-history.md) that informed this program's creation.  


## Understanding the model 

The first part of the project begins by assembling as complete as possible a list of the URLs of public, federal websites.  This involves gathering numerous public datasets and combining then filtering them.  The methodology of this process [is documented here](https://github.com/GSA/federal-website-index), along with the resulting website index itself.  Relevant terminology is [defined here](https://github.com/GSA/site-scanning-documentation/blob/main/pages/terms.md).  

The site scanning engine then uses this index as a list of URLs to target for analysis.  

The process for deciding what analysis to do and thus what scans to build is [documented here](https://github.com/GSA/site-scanning-documentation/blob/main/about/stakeholder-experience.md).  Current stakeholders for the data are [described here](https://github.com/GSA/site-scanning-documentation/blob/main/about/stakeholders.md).  

More information about how the program operates can be found in the program's [documentation repository](https://github.com/GSA/site-scanning-documentation).  

## The Website Data

The website data can be accessed via API ([documentation here](https://open.gsa.gov/api/site-scanning-api/)) or via [bulk download](https://digital.gov/guides/site-scanning/data/).  

Details on what data fields are available can be found in the [data dictionary](https://github.com/GSA/site-scanning-documentation/blob/main/data/Site_Scanning_Data_Dictionary.csv).  

## Potential Future Scans 

Active user research and iterative development is ongoing.  User interviews and the experience of the wider Technology Transformation Services team has built up [a substantial list of ideas for further development](https://github.com/GSA/site-scanning-documentation/blob/main/pages/candidate-scans.md).  

The [decision process that has informed which scans have been built so far](https://github.com/GSA/site-scanning-documentation/blob/main/about/stakeholder-experience.md) remains in use to decide which prioritize which scans to build in order to expand the data that is available about these websites.  


## How to Engage Us Further

* Feel free to email the team at [site-scanning@gsa.gov](mailto:site-scanning@gsa.gov).  
* Questions, bug reports, or suggestions are always welcome in the [program's issue tracker](https://github.com/GSA/site-scanning/issues).
