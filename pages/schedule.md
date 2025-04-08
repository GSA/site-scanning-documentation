# Site Scanning Schedule

This document contains the schedule of when automated processes take place, as well as notes on how they operate.  (Note the recommended order for rebuilding [here](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/team-workflows.md#refresh-everything-in-the-system).)

## Build federal website index

**When:** Daily, 10 PM UTC

**GitHub Action specification:** https://github.com/GSA/federal-website-index/blob/main/.github/workflows/build-list-js.yml

[Manually Run GitHub Action](https://github.com/GSA/federal-website-index/actions/workflows/build-list-js.yml)

**Notes:** This action builds the target URL list using [this list of sources](https://github.com/GSA/federal-website-index/blob/main/builder/src/config/source-list.config.ts) and [these instructions](https://github.com/GSA/federal-website-index/blob/main/builder/src/main.ts) and saves it [here](https://github.com/GSA/federal-website-index/blob/main/data/site-scanning-target-url-list.csv), along with an analysis file containing metadata about the list creation process [here](https://github.com/GSA/federal-website-index/blob/main/data/site-scanning-target-url-list-analysis.csv). Various snapshot files are generated at each step of the build process in order to serve as breadcrumbs and are saved [here](https://github.com/GSA/federal-website-index/tree/main/data/process-snapshots).

## Ingest federal website index

**When:** Daily, 10:15 PM UTC

**GitHub Action specification:** https://github.com/GSA/site-scanning-engine/blob/main/.github/workflows/ingest.yml

[Manually Run GitHub Action](https://github.com/GSA/site-scanning-engine/actions/workflows/ingest.yml)

## Fetch security data

**When:** Daily, 10:30 PM UTC

**GitHub Action specification:** https://github.com/GSA/site-scanning-engine/blob/main/.github/workflows/fetch-security-data.yml

[Manually Run GitHub Action](https://github.com/GSA/site-scanning-engine/actions/workflows/fetch-security-data.yml)

**Notes:** This action fetches data concerning https and hsts usage from a publically hosted [CSV file](https://raw.githubusercontent.com/GSA/federal-website-index/main/data/dataset/cisa_https.csv).

## Scan websites

**When: Daily at 12:10 AM UTC**

**GitHub Action specification:** https://github.com/GSA/site-scanning-engine/blob/main/.github/workflows/enqueue-scans.yml

[Manually Run GitHub Action](https://github.com/GSA/site-scanning-engine/actions/workflows/enqueue-scans.yml)

**Notes:** This action prompts the scanning engine to add every website in the database to the scanning queue.

## Produce snapshots

**When:** Daily, 12:00 PM UTC

**GitHub Action specification:** https://github.com/GSA/site-scanning-engine/blob/main/.github/workflows/create-snapshot.yml

[Manually Run GitHub Action](https://github.com/GSA/site-scanning-engine/actions/workflows/create-snapshot.yml)

**Notes:** This action produces the CSV and JSON snapshots of the site scanning engine's most recent scan.

## Produce accessibility details snapshot

**When:** Daily, 12:15 PM UTC

**GitHub Action specification:** https://github.com/GSA/site-scanning-engine/blob/main/.github/workflows/create-a11y-snapshot.yml

[Manually Run GitHub Action](https://github.com/GSA/site-scanning-engine/actions/workflows/create-a11y-snapshot.yml)

**Notes:** This action produces JSON snapshot containing accessibility-related violation details from the site scanning engine's most recent scan.


## Analyze snapshots and target URL list

**When: Daily, 1:00 PM UTC**

**GitHub Action specification:** https://github.com/GSA/site-scanning-analysis/blob/main/.github/workflows/generate-all-reports.yml

[Manually Run GitHub Action](https://github.com/GSA/site-scanning-analysis/actions)

**Notes:** This action creates three analysis reports in [this directory](https://github.com/GSA/site-scanning-analysis/tree/main/reports). These reports analyze: (1) the target URL list, (2) the "primary" snapshot that contains all live sites scanned, and (3) the "all" snapshot that contains all sites scanned.


## Generate unique websites list

**When:** Daily, 2:00 PM UTC

**GitHub Action specification:** https://github.com/GSA/site-scanning-analysis/blob/main/.github/workflows/generate-unique-website-list.yml

[Manually Run GitHub Action](https://github.com/GSA/site-scanning-analysis/actions)

**Notes:** This action produces a list of unique final websites found in the primary snapshot.

## Generate agency-specific snapshots

**When:** Daily, 2:15 PM UTC

**GitHub Action specification:** https://github.com/GSA/site-scanning-snapshots/blob/main/.github/workflows/save-agency-slices.yml

[Manually Run GitHub Action](https://github.com/GSA/site-scanning-snapshots/actions)

**Notes:** This action produces a set of snapshots for each agency here: https://github.com/GSA/site-scanning-snapshots/tree/main/by_agency.

## Generate IDEA report

**When:** Tuesday, 12 AM UTC

**GitHub Action specification:** https://github.com/GSA/site-scanning-analysis/blob/main/.github/workflows/generate-idea-report.yml

[Manually Run GitHub Action](https://github.com/GSA/site-scanning-analysis/actions)

**Notes:** This action produces a report containing counts and percentages of DAP and USWDS use.

## Archive Snapshots

**When:** Monthly, 12 AM UTC

**GitHub Action specification:** https://github.com/GSA/site-scanning-snapshots/blob/main/.github/workflows/archive-snapshot.yml

[Manually Run GitHub Action](https://github.com/GSA/site-scanning-snapshots/actions)

**Notes:** This action archives the "all" snapshot on the first day of each month.


# Unscheduled but available

- Rescan stale (older than 3 days) results - [Action](https://github.com/GSA/site-scanning-engine/actions/workflows/requeue-stale-scans.yml)
- Scan a single URL (likely has to be a url already in the site index) - [Action](https://github.com/GSA/site-scanning-engine/actions/workflows/enqueue-site.yml)
- Enqueue a limited number of URLs - [Action](https://github.com/GSA/site-scanning-engine/actions/workflows/enqueue-limited-scans.yml)
- Enqueue scans that previously timed out - [Action](https://github.com/GSA/site-scanning-engine/actions/workflows/queue-primary-timeouts.yml)
