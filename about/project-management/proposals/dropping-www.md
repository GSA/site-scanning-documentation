## Problem

We have historically treated x.gov and www.x.gov as distinct websites.  This is formally correct but is unintuitive to many people since, in practice, the two almost always function are used interchangeably.  As a result, we often have agencies asking why both are included and saying that the result is duplicative data.  

Also, CISA's [HTTPS scan data](https://github.com/GSA/federal-website-index/blob/main/data/dataset/cisa_https.csv) is maintained with no `www.` prefixes.  Each of the 100k domains that are scanned are actually scanned 4 times (http://x.gov; http://www.x.gov; https://x.gov; and https://www.x.gov) since the https/hsts requirements apply equally to all 4 variants, but their data structure resolves around target URLs without `www.`.  This makes integration with our data incomplete, since we cannot easily align Target URLs that begin with `www.` to their corresponding CISA scan data.  

## Proposal

Consider changing our [Federal Website Index](https://github.com/GSA/federal-website-index), which we use as the Target URL list for scanning, so that `www.` is dropped from any target URLs that have it.  This _should_ simplify the conversation about what what is being targeted so that we don't have to differentiate between www.x.gov and x.gov, would reduce what is often thought of as duplication, and would allow for easier matching of CISA scan data with our Target URL list.  

Specifically, what we would likely do is continue [assemblying the Federal Website Index in the same fashion](https://github.com/GSA/federal-website-index/blob/main/process/index-creation.md), but add a step at the end to drop `www.` from the start of any Target URLs and do a final deduplication step.  We would also remove a step earlier in the index creation process that takes the list of federal .gov domains and re-adds them with `www.` at the beginning.  

## Details 

The biggest problem with this change would be losing scan data for the non-trivial number of sites that won't load without `www.`.  Though it's considered a bad practice, quite a number of webpages won't load if `www.` isn't included and as a result, scan entries for which we are currently getting useful data will start failing and will not allow for scanning until and unless the team that operates it changes the site's configuration to not require `www.` at the beginning.  Though this is a loss, it would be nice to motivate that change.  


Problems: 




