

## 1. Everything We Can Find

The first step of creating the Federal Website Index is combining every url of every data source we're using.  The result is about 35k urls and a snapshot of this can be found [here](https://github.com/GSA/federal-website-index/blob/main/data/snapshots/combined.csv).

## 2. Deduplicate

The next step of creating the Federal Website Index is deduping the combined list.  The result is about 31k urls and a snapshot of this can be found [here](https://github.com/GSA/federal-website-index/blob/main/data/snapshots/combined-dedup.csv).  A snapshot of the urls that are removed can be seen [here](https://github.com/GSA/federal-website-index/blob/main/data/snapshots/dedup-removed.csv).  

## 3. Ignore List Applied To Remove Non-Public Sites

The next step of creating the Federal Website Index is filtering out websites that either of [these](https://github.com/GSA/federal-website-index/blob/main/criteria/ignore-list-begins.csv) [filters](https://github.com/GSA/federal-website-index/blob/main/criteria/ignore-list-contains.csv) catch.  The goal of these filters is to remove websites that are not intended for the public (e.g. staging sites, login pages to internal systems, etc.).  The remaining list is about 29k urls and a snapshot of it can be found [here](https://github.com/GSA/federal-website-index/blob/main/data/snapshots/remove-ignore-contains.csv).  A snapshot of the urls that are removed can be seen [here](https://github.com/GSA/federal-website-index/blob/main/data/snapshots/ignored-removed-begins.csv) (begins) and [here](https://github.com/GSA/federal-website-index/blob/main/data/snapshots/ignored-removed-contains.csv) (contains).  

## 4. Non-Federal And Non-.Gov URLs Removed

The final step in the creation of the Federal Website Index is filtering out any websites that don't have a base domain that is a federal .gov domain.  Namely, this removes any state/local/tribal websites and any non-.gov websites (e.g. .mil, .edu).  The final result is about 27k urls and can be found [here](https://github.com/GSA/federal-website-index/blob/main/data/site-scanning-target-url-list.csv). **This is what the Site Scanning engine scans.**  A snapshot of the urls that are removed can be seen [here](https://github.com/GSA/federal-website-index/blob/main/data/snapshots/nonfederal-removed.csv).  

-----
At this point, the Site Scanning engine analyzes the Federal Website Index and captures data about each URL.  A snapshot of this data can be seen [here](https://api.gsa.gov/technology/site-scanning/data/weekly-snapshot-all.csv) and is referred to as the 'All' snapshot.  
-----

## 5. Inactive Sites Removed

The Site Scanning data is filtered to only show live sites (`Final URL - Live = TRUE`).  The final result is about 14k urls, can be found [here](https://api.gsa.gov/technology/site-scanning/data/weekly-snapshot.csv), and is referred to as the 'Primary' snapshot.  This is most often what users consult when looking at Site Scanning data.  

## 6. Deduplicate Final URLs

The 'Primary' snapshot is then filtered to remove rows that have the same Final URL in order to create the 'Unique Final URL' snapshot.  The final result is about 12k urls and can be found [here](https://github.com/GSA/site-scanning-analysis/blob/main/unique_website_list/results/weekly-snapshot-unique-final-urls.csv).  A snapshot of the URLs that are removed can be seen [here](https://github.com/GSA/site-scanning-analysis/blob/main/unique_website_list/results/removed-final-urls.csv).  

## 7. Deduplicate Final Websites

The 'Unique Final URL' snapshot is then filtered to remove rows that have the same `Final URL - Base Website' in order to create the 'Unique Final Website' snapshot.  The final result is about 10k urls and can be found [here](https://github.com/GSA/site-scanning-analysis/blob/main/unique_website_list/results/weekly-snapshot-unique-final-websites.csv).  A snapshot of the URLS that are removed can be seen [here](https://github.com/GSA/site-scanning-analysis/blob/main/unique_website_list/results/removed-final-url-websites.csv).  






