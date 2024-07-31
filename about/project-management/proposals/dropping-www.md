Add link in here - https://github.com/GSA/site-scanning-snapshots/tree/main/other/misc


## Problem

We have historically treated x.gov and www.x.gov as distinct websites.  This is formally correct but is unintuitive to many people since, in practice, the two almost always function are used interchangeably.  As a result, we often have agencies asking why both are included and saying that the result is duplicative data.  

Also, CISA's [HTTPS scan data](https://github.com/GSA/federal-website-index/blob/main/data/dataset/cisa_https.csv) is maintained with no `www.` prefixes.  Each of the 100k domains that are scanned are actually scanned 4 times (http://x.gov; http://www.x.gov; https://x.gov; and https://www.x.gov) since the https/hsts requirements apply equally to all 4 variants, but their data structure resolves around target URLs without `www.`.  This makes integration with our data incomplete, since we cannot easily align Target URLs that begin with `www.` to their corresponding CISA scan data.  

## Proposal

Consider changing our [Federal Website Index](https://github.com/GSA/federal-website-index), which we use as the Target URL list for scanning, so that `www.` is dropped from any target URLs that have it.  This _should_ simplify the conversation about what what is being targeted so that we don't have to differentiate between www.x.gov and x.gov, would reduce what is often thought of as duplication, and would allow for easier matching of CISA scan data with our Target URL list.  

Specifically, what we would likely do is continue [assemblying the Federal Website Index in the same fashion](https://github.com/GSA/federal-website-index/blob/main/process/index-creation.md), but add a step at the end to drop `www.` from the start of any Target URLs and do a final deduplication step.  We would also remove a step earlier in the index creation process that takes the list of federal .gov domains and re-adds them with `www.` at the beginning.  

## Details 

The biggest problem with this change would be losing scan data for the non-trivial number of sites that won't load without `www.`.  Though it's considered a bad practice, quite a number of webpages won't load if `www.` isn't included and as a result, scan entries for which we are currently getting useful data will start failing and will not allow for scanning until and unless the team that operates it changes the site's configuration to not require `www.` at the beginning.  Though this is a loss, it would be nice to motivate that change.  

We want to quantify the impact this change would have on Site Scanning data, specificly how much scan data for users will be lost by this change.  Moreso though, we should think of this in terms of 'what is the best way to think of the federal web presence?.'  Is Federal Website Index that is always stripped of `www.` the cleanest way to think of this, or is a sometimes more complicated and conflicting list that includes some urls with `www.` and others without superior?  

For perspective, as of June 28, 2024, 3181 of 28803 target URLs in the Federal Website Index begin with `www.`.  Of those, 1438 have two periods (e.g. www.x.gov) and might be thought of as the classic use of `www.`.  The other 1743 target URLs that begin with `www.` have that before 1 or more subdomains (e.g. www.x.y.gov).   

#### Experiment 

To quantify the impact this change would have, we have run a one-off experimental scan that: 
- Take existing Federal Website Index.
- Manually remove www. from any target URLs 
- Dedup the list
- Use [the resulting list](https://github.com/GSA/federal-website-index/blob/03ea1dec092f57d0c78899963c3e1f545929b67c/data/test/site-scanning-target-url-list-sans-www-dedupped-6-12-24.csv) as a one off target URL list
- Code 4 new fields that result from taking a target URL, prepending www. to it, loading it:
  - www_final_url - the final URL that results
  - www_status_code - the http status code that results
  - www_scan_status - the status of this scan
  - www_same - whether the final_url and www_final_url fields are the same
- Generate a one off snapshot of all of the normal data in a snapshot with these four fields added in at the end.

The resulting scan data can be seen here.  XXXXXXXXXX-add link-XXXXXXXXXXXXXX

#### Analysis of Results

The dataset includes 26163 target URLs.  However, for an unknown reason, the `www. scan` did not run on 325 target URLs and thus don't have data in the four new fields, so I'm removing them from consideration.

We realized that the best way to think of this issue is by thinking of this matter in two buckets: 
- Target URLs that are straightforward second level domains (e.g. x.gov)
- Target URLs that have subdomains (e.g. x.y.gov and x.y.z.gov)

To distinguish these buckets, we've created a new column of data that counts the number of periods in the target URL.  This is useful because there's different expectations for each bucket, and certain standards and behavior can perhaps more reasonably be proposed.  

Bucket 1:  

* Of the 25838 target URLs at issue, 1409 are straightforward second level domains (only 1 period in the target URL).  
* Of these, 1162 return the same HTTP status code when scanned without and with `www.`
  * This is ideal.  
* 247 return different HTTP status codes depending on if there's a `www.`
  * This is not good.  For any x.gov, one would expect it to behave the same whether a user typed `x.gov` or `www.x.gov` in their browser.
  * 72 work without a www, but not with.  (e.g. x.gov resolves but www.x.gov does not)
  * 162 work with www, but not without.  (e.g. www.y.gov resolves but y.gov does not)
  * (13 others don't resolve either with or without but fail in different ways.)
 
From a user-experience perspective, both the groups of 72 and 162 groups would resolve this.  It's common to assume that `www.` would neither be required nor breaking, and it's a straightfoward change to implement.  

_For the purposes of this proposal though, the most noticable effect will be that 162 target URLs that are currently being scanned and have robsut results in the Site Scanning data will begin breaking and won't return results until their teams update the sites to not require `www.`._

A less important but still noteworthy trend to note is whether the target URL arrives at an identical final URL, regardless of if `www.` is used or not.  As a matter of canonicalization, it's important that x.gov and www.x.gov both resolve _to the same URL._  

* Of the 1162 Target URLs that return the same HTTP status code either way, 809 are live (in the sense that a 200 or 202 status code is returned).
  * Interestingly, only 134 of those have idential Final URLs.
  * In other words, 675 resolve to different URLs depending on whether `www.` is used.
  * Offhand, this is quite bad.  In most of these cases, it's simply a matter of a trailing `/` being added in one of the two cases (e.g. the two final URLs are https://www.x.gov and https://www.x.gov/).  Specifically, 536 of the 675 act this way.  As best as I can tell, there's no problem with this behavior.
  * There are, however, 139 that appear to resolve to different URLs.  In most of these cases, it's a matter that the one doesn't redirect to the other (e.g. x.gov resolves to https://x.gov and www.x.gov resolves to https://www.x.gov).  This would seem to be counter to technical norms and should be corrected.  
  * There are even a few of the 139 sites where x.gov and www.x.gov resolve to entirely different pages, which is really not good at all and should be corrected.  

Technical standards would say that both x.gov and www.x.gov should resolve and one should redirect to the other.  To my knowledge, there's not a best practice of which version should be the canonical URL.  In the federal .gov scene though, most redirect to the `www.` version.  Specifically, 544 of the 1162 redirect from x.gov to www.x.gov, while 101 redirect from www.x.gov to x.gov. 


Bucket 2:  

A bit messier is the second bucket.  It's not common to see websites use `www.` before another subdomain (e.g. `www.x.y.gov) and I would suggest that it's not a great practice.  In my opinion, it feels unintuitive and unnecessary.  That said, I'm not aware of it being technologically problematic and indeed, at least one major agency [explicitly requires it](https://digital.va.gov/web-governance/?_search=naked#awb-oc__377).  Regardless, we want to quantify the impact that the proposal under consideration will have on Site Scanning data.

Of 24,429 target URLs that have a subdomain (2+ periods), 10,331 have the same HTTP status code. 
- Of those 10,331, 1576 return 200 status codes both with and without www.
- The other 8755 fail both with and without www.

The 8755 are not unexpected.  On any given day, of the roughly 28,000 target URLs that are scanned, only 15-16,000 are live.  

The 1576 are notable in seemingly being sites whose subdomains resolve whether a `www.` is included before them or not.  It's worth noting that only 211 of these resolve to identical final URLs, but the vast majority of the other 1365 that don't are again a matter of a trailing slash being added.  

The 14,098 target URLs that have subdomains and return different status codes depending on if there's a `www.` or not are where the substance of this bucket lies though.
- Of them 10,466 work without a www but not when one is added (work = 200/202 status code).  This would seem to be normal and expected behavior.  
- 1265 work with `www.` included. but not without. 
- (2367 fail in either case but in different ways)

_The 1265 are important because they are sites whose scan results would be lost in this proposed change (e.g. www.x.y.gov is currently being scanned and returning data, but when we switch to scanning x.y.gov, the scan will fail because the URL will not load).  Notably, I'm not confident that agencies would readily change this configuration even when it is brought to their attention because it isn't clear that their setup violates industry standards._


## Summary of Analysis

Currently, we successfully generate scan data for about 16,000 websites.  Implementing this change would likely cause roughly 1427 (162+1265) websites to begin failing our scans and no longer generating data.  This is about 8-9%.  This would improve by roughly 1% as agencies addressed the first bucket of 162 domains that require `www.` for a second level domain to load, but realistically, even with engagement across all of these topic areas, my guess is that we would lose insight into about 5% of the federal web presence.  This is a significant cost, though it is balanced against the substantial benefit outlined at the start of this memo.  

#### Notes
- www.youthrules.gov is still in the target URL list by accident
