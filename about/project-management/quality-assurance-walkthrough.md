

## Target URL List creation 

#### Gathering

* [Source Files](https://github.com/GSA/federal-website-index/blob/638457d7c486a1337a8ebb624da9b4912e8a1b4c/builder/config.py) - [Domains](https://raw.githubusercontent.com/cisagov/dotgov-data/main/current-federal.csv) | [DAP](https://github.com/GSA/federal-website-index/blob/638457d7c486a1337a8ebb624da9b4912e8a1b4c/builder/config.py) | [Pulse](https://raw.githubusercontent.com/GSA/federal-website-index/main/data/snapshots/1-13-22/pulse-subdomains-snapshot-06-08-2020-https.csv) | [Other](https://github.com/GSA/federal-website-index/blob/638457d7c486a1337a8ebb624da9b4912e8a1b4c/data/dataset/other-websites.csv) | [OMB](https://resources.data.gov/schemas/dcat-us/v1.1/omb_bureau_codes.csv)  
* [Snapshots of Source Files Used in Most Recent Build](https://github.com/GSA/federal-website-index/tree/main/data/snapshots) - [Domains](https://github.com/GSA/federal-website-index/blob/main/data/snapshots/gov.csv) | [DAP](https://github.com/GSA/federal-website-index/blob/main/data/snapshots/dap.csv) | [Pulse](https://github.com/GSA/federal-website-index/blob/main/data/snapshots/pulse.csv) | [Other](https://github.com/GSA/federal-website-index/blob/main/data/snapshots/other.csv)

#### Assembly 

* Datasets are combined
  * Does the [snapshot](https://github.com/GSA/federal-website-index/blob/main/data/snapshots/combined.csv) look right when skimmed?  
  * Does the number of entries equal to the sum of each source file ([analysis report](https://github.com/GSA/federal-website-index/blob/main/data/site-scanning-target-url-list-analysis.csv))?   

* List is dedupped 
  * Does the [snapshot](https://github.com/GSA/federal-website-index/blob/main/data/snapshots/combined-dedup.csv) look right when skimmed?  
  * Does the [snapshot](https://github.com/GSA/federal-website-index/blob/main/data/snapshots/combined-dedup.csv) and the [removed list](https://github.com/GSA/federal-website-index/blob/main/data/snapshots/dedup-removed.csv) add up in size to the [previous snapshot](https://github.com/GSA/federal-website-index/blob/main/data/snapshots/combined.csv) ([analysis report](https://github.com/GSA/federal-website-index/blob/main/data/site-scanning-target-url-list-analysis.csv))?  


* When we review the snapshots of what is removed at each stop, do they jibe with what remains?  

## Initial Primary Scan 

* Looking for incorrect redirect info:
  * False negative examples: http://spsweb.jpl.nasa.gov
  * Consider doing a one off pass at capturing the redirect chains


(more [here](https://github.com/GSA/site-scanning/issues/356#issuecomment-1423076180))
