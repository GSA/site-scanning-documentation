

## Goal 

Compare the DAP scan data results against the [participating websites export](https://analytics.usa.gov/data/live/sites.csv) on analytics.usa.gov.  

## Method

For this analysis, I'm going to just focus on the GSA agency, a medium sized agency with a large number of websites.  

1. Take the pulse subdomain list (the same https.json file which is currently used by the Site Scanning program for its target URLs), take the [participating websites export](https://analytics.usa.gov/data/live/sites.csv) on analytics.usa.gov, and combine them.    Filter to just GSA.  
2. Go to the [v1.0 spotlight website](https://spotlight.app.cloud.gov/), go to the[DAP report page](https://spotlight.app.cloud.gov/search200/dap/), filter for GSA, and export the results as a CSV.  
3. Remove extraneous columns from both datasets and then put them side by side in [a google spreadsheet](https://docs.google.com/spreadsheets/d/1fjQ5J-Hp9bvfxz9zNqlKoOZEmSad2-S5kUrpp55dfWs/edit#gid=1643437513), align them, and analyze the results.  

## Observations  

* The DAP scan results for GSA lists 896 websites. DAP is detected on 368 of them and not detected on 528.
* From analytics.usa.gov, there are 903 websites.  DAP is detected on 285 of them and not detected on 618.  
