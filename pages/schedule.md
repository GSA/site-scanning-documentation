# Site Scanning Schedule

This document contains the schedule of when automated processes take place, as well as notes on how they operate.

## Build federal website index

**When:** Wednesday, 10 PM UTC

**GitHub Action specification:** https://github.com/GSA/federal-website-index/blob/main/.github/workflows/build-list.yml

[Manually Run GitHub Action](https://github.com/GSA/federal-website-index/actions)

**Notes:** This action builds the target URL list using [this list of sources](https://github.com/GSA/federal-website-index/blob/main/builder/config.py) and [these instructions](https://github.com/GSA/federal-website-index/blob/main/builder/__main__.py) and saves it [here](https://github.com/GSA/federal-website-index/blob/main/data/site-scanning-target-url-list.csv), along with an analysis file containing metadata about the list creation process [here](https://github.com/GSA/federal-website-index/blob/main/data/site-scanning-target-url-list-analysis.csv). Various snapshot files are generated at each step of the build process in order to serve as breadcrumbs and are saved [here](https://github.com/GSA/federal-website-index/tree/main/data/snapshots).

## Scan websites

**When: Daily at 12:10 AM UTC**

**GitHub Action specification:** https://github.com/GSA/site-scanning-engine/blob/main/.github/workflows/enqueue-scans.yml

[Manually Run GitHub Action](https://github.com/GSA/site-scanning-engine/actions)

**Notes:** This action prompts the scanning engine to add every website in the database to the scanning queue.

## Ingest federal website index

**When:** Thursday, 9 PM UTC

**GitHub Action specification:** https://github.com/GSA/site-scanning-engine/blob/main/.github/workflows/ingest.yml

[Manually Run GitHub Action](https://github.com/GSA/site-scanning-engine/actions)

## Analyze snapshots and target URL list

**When: Thursday, 10 PM UTC**

**GitHub Action specification:** https://github.com/GSA/site-scanning-analysis/blob/main/.github/workflows/generate-all-analysis.yml

[Manually Run GitHub Action](https://github.com/GSA/site-scanning-analysis/actions)

**Notes:** This action creates three analysis reports in [this directory](https://github.com/GSA/site-scanning-analysis/tree/main/reports). These reports analyze: (1) the target URL list, (2) the "primary" snapshot that contains all live sites scanned, and (3) the "all" snapshot that contains all sites scanned.

## Produce snapshots

**When:** Sunday, 12 AM UTC

**GitHub Action specification:** https://github.com/GSA/site-scanning-engine/blob/main/.github/workflows/create-snapshot.yml

[Manually Run GitHub Action](https://github.com/GSA/site-scanning-engine/actions)

**Notes:** This action produces the CSV and JSON snapshots of the site scanning engine's most recent scan.

## Generate unique websites list

**When:** Monday, 12 AM UTC

**GitHub Action specification:** https://github.com/GSA/site-scanning-analysis/blob/main/.github/workflows/generate-unique-website-list.yml

[Manually Run GitHub Action](https://github.com/GSA/site-scanning-analysis/actions)

**Notes:** This action produces a list of unique final websites found in the primary snapshot.
