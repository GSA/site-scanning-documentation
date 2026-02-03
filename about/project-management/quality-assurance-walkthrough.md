# v2 

### Creation of source files 

- Confirm which source files are currently being utilitized ([list](https://github.com/GSA/federal-website-index/blob/main/builder/src/main.ts#L50-L77), [links](https://github.com/GSA/federal-website-index/blob/main/builder/src/config/source-list.config.ts))
- Confirm that they are present in the website index
- Confirm how many entries each source file provides to the website index ([report](https://github.com/GSA/federal-website-index/blob/main/data/site-scanning-target-url-list-analysis.csv))


### [Creation of the Site Scanning website index](https://github.com/GSA/federal-website-index/blob/main/process/index-creation.md)
- Review the analysis report and ...  ([report](https://github.com/GSA/site-scanning-analysis/blob/main/reports/target-url-list.csv))

### Scanning 


### S3 snapshot generation 


### Subsequent snaphot generation 


### Reports generation 




# v1 

# Overview 

| Step | Standard | How to Analyze | 
| -- | -- | -- | 
| Index Assembly | Comprehensive list of seed lists | Search for and integrate more datasets | 
| Index Assembly | Index properly Assembled | Ensure combining, dedupping, removal of `wwww.`, and removal of non-current/non-federal | 
| Index Assembly | Filter label applied properly | Analyze what is filtered and what isn't and make changes | 
| Scan | Every site gets scanned | Ensure that all sites in the index and in the scan data | 
| Scan | Every scan completes | Analyze scan data | 






## Target URL List creation 

#### Gathering

* [Source Files](https://github.com/GSA/federal-website-index/blob/main/builder/config.py) - [Domains](https://github.com/cisagov/dotgov-data/blob/main/current-federal.csv) | [DAP](https://analytics.usa.gov/data/live/sites-extended.csv) | [Pulse](https://raw.githubusercontent.com/GSA/data/master/dotgov-websites/pulse-subdomains-snapshot-06-08-2020-https.csv) | [Other](https://github.com/GSA/federal-website-index/blob/main/data/dataset/other-websites.csv) | [OMB](https://resources.data.gov/schemas/dcat-us/v1.1/omb_bureau_codes.csv)  
* [Snapshots of Source Files Used in Most Recent Build](https://github.com/GSA/federal-website-index/tree/main/data/snapshots) - [Domains](https://github.com/GSA/federal-website-index/blob/main/data/snapshots/gov.csv) | [DAP](https://github.com/GSA/federal-website-index/blob/main/data/snapshots/dap.csv) | [Pulse](https://github.com/GSA/federal-website-index/blob/main/data/snapshots/pulse.csv) | [Other](https://github.com/GSA/federal-website-index/blob/main/data/snapshots/other.csv)
  * Do the entries look right when skimmed?  
  * Are there inconsistencies, e.g. agency/organization in the domain registry? 

#### Assembly 

* Datasets are combined
  * Does the [snapshot](https://github.com/GSA/federal-website-index/blob/main/data/snapshots/combined.csv) look right when skimmed?  
  * Does the number of entries in the [snapshot]((https://github.com/GSA/federal-website-index/blob/main/data/snapshots/combined.csv)) equal to the sum of each source file ([analysis report](https://github.com/GSA/federal-website-index/blob/main/data/site-scanning-target-url-list-analysis.csv))?   

* List is dedupped 
  * Does the [snapshot](https://github.com/GSA/federal-website-index/blob/main/data/snapshots/combined-dedup.csv) look right when skimmed?  
  * Does the [snapshot](https://github.com/GSA/federal-website-index/blob/main/data/snapshots/combined-dedup.csv) and the [removed list](https://github.com/GSA/federal-website-index/blob/main/data/snapshots/dedup-removed.csv) add up in size to the [previous snapshot](https://github.com/GSA/federal-website-index/blob/main/data/snapshots/combined.csv) ([analysis report](https://github.com/GSA/federal-website-index/blob/main/data/site-scanning-target-url-list-analysis.csv))?  

* Ignore list is applied 
  * Does the [snapshot](https://github.com/GSA/federal-website-index/blob/main/data/snapshots/remove-ignore.csv) look right when skimmed?  
  * Are there entries in the [snapshot](https://github.com/GSA/federal-website-index/blob/main/data/snapshots/remove-ignore.csv) that we would like to have the [ignore list](https://github.com/GSA/federal-website-index/blob/main/criteria/ignore-list.csv) filter out?  If so, how could the ignore list be modified to do that.  
  * Are there entries in the [removed list](https://github.com/GSA/federal-website-index/blob/main/data/snapshots/ignored-removed.csv) that we wish the [ignore list](https://github.com/GSA/federal-website-index/blob/main/criteria/ignore-list.csv) hadn't filtered out?  If so, how could the ignore list be modified to do that?  
  * Does the [snapshot](https://github.com/GSA/federal-website-index/blob/main/data/snapshots/remove-ignore.csv) and the [removed list](https://github.com/GSA/federal-website-index/blob/main/data/snapshots/ignored-removed.csv) add up in size to the [previous snapshot](https://github.com/GSA/federal-website-index/blob/main/data/snapshots/combined-dedup.csv) ([analysis report](https://github.com/GSA/federal-website-index/blob/main/data/site-scanning-target-url-list-analysis.csv))?

* Nonfederal are removed, resulting in the Target URL list
  * Does the [resulting file](https://github.com/GSA/federal-website-index/blob/main/data/site-scanning-target-url-list.csv) look right when skimmed? 
  * Does the [resulting file](https://github.com/GSA/federal-website-index/blob/main/data/site-scanning-target-url-list.csv) and the [removed list](https://github.com/GSA/federal-website-index/blob/main/data/snapshots/nonfederal-removed.csv) add up in size to the [previous snapshot](https://github.com/GSA/federal-website-index/blob/main/data/snapshots/remove-ignore.csv) ([analysis report](https://github.com/GSA/federal-website-index/blob/main/data/site-scanning-target-url-list-analysis.csv))? 

* The completed Target URL list 
  * Are there any empty cells in the file outside of the agency code, bureau, and bureau code columns ([analysis report](https://github.com/GSA/site-scanning-analysis/blob/main/reports/target-URL-list.csv))? 
  * Are any of the values in the [analysis report](https://github.com/GSA/site-scanning-analysis/blob/main/reports/target-URL-list.csv) unusually different from [recent history](https://github.com/GSA/site-scanning-analysis/commits/main/reports/target-URL-list.csv)? 


## After the scans complete

* Does the number of results in the primary snapshot ([analysis report](https://github.com/GSA/site-scanning-analysis/blob/main/reports/snapshot-primary.csv)) equal the number of urls that returned a 2xx server code in the all snapshot ([analysis report](https://github.com/GSA/site-scanning-analysis/blob/main/reports/snapshot-all.csv))?
* In the [all snapshot](https://api.gsa.gov/technology/site-scanning/data/weekly-snapshot-all.csv), do any records with a non-2xx final_url_status_code appear to be live and thus should have returned a 2xx code? 
* In the [all snapshot](https://api.gsa.gov/technology/site-scanning/data/weekly-snapshot-all.csv), do any records with a failing scan status appear to be live and thus should have completed? 
  * Note - in particular, analyze and think about each error type.  
  * [Proposal: filter out certain mimetypes (e.g. JSON, XML) from the primary snapshot as well. If done, we should add a similar step to ^^^]
* Are there certain fields in either snapshot which should not have any empty cells (if so, note them here)? 

## For individual fields...

* Looking for incorrect redirect info:
  * False negative examples: http://spsweb.jpl.nasa.gov
  * Consider doing a one off pass at capturing the redirect chains
* What else...?

API

* Do the number of records shown in the [endpoint](https://api.gsa.gov/technology/site-scanning/v1/websites?API_KEY=DEMO_KEY) (meta: totalItems, at the bottom) equal the number of records in the target URL list [analysis report](https://github.com/GSA/site-scanning-analysis/blob/main/reports/target-URL-list.csv)? 
* What is the oldest entry? 

(more [here](https://github.com/GSA/site-scanning/issues/356#issuecomment-1423076180))
