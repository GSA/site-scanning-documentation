

## 1. Everything We Can Find

The first step of creating the Federal Website Index is combining every url of every data source we're using.  The result is about 35k urls and a snapshot of this can be found [here](https://github.com/GSA/federal-website-index/blob/main/data/snapshots/combined.csv).

## 2. Deduplicate

The next step of creating the Federal Website Index is deduping the combined list.  The result is about 31k urls and a snapshot of this can be found [here](https://github.com/GSA/federal-website-index/blob/main/data/snapshots/combined-dedup.csv).  

## 3. Ignore List Applied To Remove Non-Public Sites

The next step of creating the Federal Website Index is filtering out websites that either of [these](https://github.com/GSA/federal-website-index/blob/main/criteria/ignore-list-begins.csv) [filters](https://github.com/GSA/federal-website-index/blob/main/criteria/ignore-list-contains.csv) catch.  The goal of these filters is to remove websites that are not intended for the public (e.g. staging sites, login pages to internal systems, etc.).  The remaining list is about 29k urls and a snapshot of it can be found [here](https://github.com/GSA/federal-website-index/blob/main/data/snapshots/remove-ignore.csv).  

## 4. Non-Federal And Non-.Gov URLs Removed

The final step in the creation of the Federal Website Index is filtering out any websites that don't have a base domain that is a federal .gov domain.  Namely, this removes any state/local/tribal websites and any non-.gov websites (e.g. .mil, .edu).  The final result is about 27k urls and can be found [here](https://github.com/GSA/federal-website-index/blob/main/data/site-scanning-target-url-list.csv). **This is what the Site Scanning engine scans.**








