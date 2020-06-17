

## Goal 

Compare the DAP scan data results against the [participating websites export](https://analytics.usa.gov/data/live/sites.csv) on analytics.usa.gov.  

## Method

For this analysis, I'm going to just focus on the GSA agency, a medium sized agency with a large number of websites.  

1. Take the pulse subdomain list (the same https.json file which is currently used by the Site Scanning program for its target URLs), take the [participating websites export](https://analytics.usa.gov/data/live/sites.csv) on analytics.usa.gov, and combine them.    Filter to just GSA.  
2. Go to the [v1.0 spotlight website](https://spotlight.app.cloud.gov/), go to the[DAP report page](https://spotlight.app.cloud.gov/search200/dap/), filter for GSA, and export the results as a CSV.  
3. Remove extraneous columns from both datasets and then put them side by side in [a google spreadsheet](https://docs.google.com/spreadsheets/d/1fjQ5J-Hp9bvfxz9zNqlKoOZEmSad2-S5kUrpp55dfWs/edit#gid=1643437513), align them, and analyze the results.  

## Results  

* The DAP scan results for GSA lists 896 websites. DAP is detected on 368 of them and not detected on 528.
* From analytics.usa.gov, there are 903 websites.  DAP is detected on 285 of them and not detected on 618.  
* 833 URLS directly match on both scans.  Another 19 match except that on the DAP scan results they have a `www.` and on the analytics.usa.gov export, it's stripped out.  So, 852 line up just right.  
* Of the remaining 44 in the DAP scan, 31 are duplicates b/c they have a `www.` in addition to the `x.gov` that is in both datasets already.  Another 12 are inaccessible or do not resolve. Only 1 (`usability.gov`) is in the DAP scan and not in the analytics.usa.gov export.  This is b/c it's listed as a GSA domain in the .gov domain dataset, but as HHS in the pulse subdomain report. That's b/c this just [changed recently](https://github.com/GSA/data/commit/8cf96f091a593fb5106fb2848a8fb23726ace7ed#diff-38fa226fb0b3f7a8f1ff74774ad831b4) and the pulse subdomain list is older.   
* There are 51 in the analytics.usa.gov export that are not in the DAP scan results.  Of these, 42 are internal, inaccessible urls from login.gov, identitysandbox.gov, and itdashboard.gov.  I assume that either the pulse subdomain generation results changed at some point, or the DAP scan is ignoring them b/c they are inaccessible.  Their absence in the DAP scan is not problematic.  There were, however, 9 that resolve and should have been in the DAP scan results but weren't.  
* Focusing on the 852 websites that aligned between the two datasets, there are 183 that both detect DAP and 421 that both say it's missing.  In other words, the scans are in agreement for 604.  
* There are 161 that the DAP scan says has DAP, whereas analytics.usa.gov says it does not.  There are 87 where the DAP scans says it does not, but analytics.usa.gov say that it does.  
* 

Of those, DAP scan detects DAP on 337.  Of those analytics.usa.gov concurs on 178 and does not concur on 159.  

SS would detect yes correctly: redirect, if no traffic in last 14 days 



No, not in the analytics.usa.gov dataset because this URL is duplicative to the non-www URL that is in both datasets	Double check the DAP presence result.  Consider whether this record shouldn't be in the results at all.  	This entry is likely a complete duplicate and can be ignored.  



the analytics.usa.gov export only shows hostnames. So if ask.gsa.gov/1 has DAP and ask.gsa.gov doesn't, you still see ask.gsa.gov in the analytics.usa.gov export.  But the DAP team is okay with it being indicated DAP, no.  


note the difference in the methodology, that SS looks at a literal URL.  
https://github.com/18F/analytics-reporter/blob/master/reports/usa.json#L360


## Analysis

* We shouldn't be including redirect in results.  
* Generally speaking, if the DAP scan detects DAP and analytics.usa.gov, the site scanner is finding legitimate DAP code.  
* Generally speaking, if DAP scan isn't detecting DAP and analytics.usa.gov does, it's for a good reason.  


## Goals for Data improvement

* Decide whether to have both `x.gov` and `www.x.gov` in the results.  
* Think about why the 12 domains that don't resolve are still in the results and if they shouldn't be.  
* Research why the 9 URLs that weren't in the DAP scan results, but still resolve were missing.  
* maybe we should only be showing data for final URLs, not initial ones.  
* From Tim, if the target URL redirects to a new subdomain, it shouldn't be in the scan results.  e.g. 18f.gov
* Need to include final url and redirect notes in this dataset.  

