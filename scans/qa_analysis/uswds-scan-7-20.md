
## Goal 

Analyze the quality of the USWDS scan data results by having a human check them manually.  

## Method

For this analysis, the USWDS team took an export of the scan data and: 

1) For every positive result (a total score above 50), they manually analyzed it to see if they agree with the results.  

Note: I don't believe that the team then looked to see if they had any examples of websites that they knew had implemented USWDS but that were showing up in our scans as not having it (e.g. false negatives in our data).  However, as discussed below, I'm not sure there was a need to do that at this point.  

## Results  

* The USWDS scan identified 580 websites (that had a total score above 50).  
* 242 were redirects 
* 161 were websites that had USWDS but that they already knew about.  
* 77 were 'noncanonical' (duplicative with another URL that is the same page)
* 56 were staging/dev
* 27 were good finds (websites that had USWDS that they hadn't known about)
* 16 were Search.gov CNAMEs


## Analysis

* The good news is that there didn't seem to be any false positives (scan says there's USWDS when there's not).  
* Results that have a version number are very accurate.  
* The team noted that `-usa` is actually a pretty generic snippet and doesn't do much for indicating USWDS status, but it's not skewing 


## Goals for Data improvement

* Add redirect status and final URL to the data fields (this is the most immediate and actionable) 
* Consider maintaining a central YML file of known staging/non-websites.  Alternatively, weigh taking previously generated `ignore` logic and applying it as another field for 'likely not a website'.  
* Consider them hosting a YML file of known, human-confirmed users. 
* Consider them creating a more obscure string that we could search for instead of the formula currently used (possibly from a new SVG file). 

