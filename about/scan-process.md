Scan process [triggered via CircleCI @ 11:45pm ET (2:45 UTC)](https://github.com/18F/Spotlight/blob/211ffaab203985205fdf006262dea68248879656/.circleci/config.yml#L155) against main branch only
- Starts a job called [`scan`](https://github.com/18F/Spotlight/blob/211ffaab203985205fdf006262dea68248879656/.circleci/config.yml#L119)
- Authenticates to Cloud.gov
- Runs [`spawn_scans.sh`](https://github.com/18F/Spotlight/blob/main/spawn_scans.sh) This script takes split domains provided by getdomains.sh and spawns concurrent cloud.gov jobs for each.
    - Runs [`getdomains.sh`](https://github.com/18F/Spotlight/blob/main/getdomains.sh)
    This script fetches all the domains and splits them up into batches that can be used to parallelize the scanning.
        - Retrieves current Federal [Dotgov registry](https://github.com/GSA/data/tree/master/dotgov-domains) and [Pulse](https://github.com/GSA/data/raw/master/dotgov-websites/pulse-subdomains-snapshot-06-08-2020-https.csv) domains data 
        [TODO: PLANS FOR ONGOING PULSE DATA?]
        - Runs [`mergedomainscsv.py`](https://github.com/18F/Spotlight/blob/main/mergedomaincsv.py) This script merges and deduplicates the list of URLs to run scans against
            - Exports URLs in CSV files [limited to 6000 lines](https://github.com/18F/Spotlight/blob/211ffaab203985205fdf006262dea68248879656/getdomains.sh#L8) each into `/tmp/domains.csv` [TODO: DOCUMENT FILENAME CONVENTION (e.g.`*-scan.csv`)]
            - Each CSV file represents a `task` to run on Cloud.gov
        - [Terminate](https://github.com/18F/Spotlight/blob/211ffaab203985205fdf006262dea68248879656/spawn_scans.sh#L10) any active scans that are running (artifact from Lighthouse being huge) _[known issue-link?]_
        - [`run-task`](https://github.com/18F/Spotlight/blob/211ffaab203985205fdf006262dea68248879656/spawn_scans.sh#L22) on cloud.gov:
            - [Sets](https://github.com/18F/Spotlight/blob/211ffaab203985205fdf006262dea68248879656/spawn_scans.sh#L22) 1G memory, 4G disk space for each task
              - Runs [`scan_engine.sh`](https://github.com/18F/Spotlight/blob/main/scan_engine.sh) This script is what gets the list of domains to scan, runs the scanners, collects the data, puts it into s3, and sets how long data is retained.

            - Get list of (whitelisted? flagged?) [`SCANTYPES`](https://github.com/18F/Spotlight/blob/211ffaab203985205fdf006262dea68248879656/scan_engine.sh#L13)
              - [TODO: DOCUMENT INDIVIDUAL SCAN PROCESSES]
            - [Set repo/branch](https://github.com/18F/Spotlight/blob/211ffaab203985205fdf006262dea68248879656/scan_engine.sh#L24) as source  
            - [Set credentials](https://github.com/18F/Spotlight/blob/211ffaab203985205fdf006262dea68248879656/scan_engine.sh#L33) for AWS + Cloud.gov (mapped to ENV VARS) [TODO: DOCUMENT WHERE ENV VARS SET]
            - Checks out `domain-scan`
            - `apt-get` installs a bunch of unneeded stuff _[known issue-link?]_
              - Installs `node `
            - Then runs `getdomains.sh` script again
                - This time we save the `*-scan.csv` files to a temporary directory: `/cache`
            - Run scans
                - For each domain (from `get_domains.sh`)
                  - Domain, then each scantype runs against, then new domain
                - Saved into /cache
            - Loads into cloud.gov ElasticSearch
                - Create initial index > defines destination JSON files
                    - Date and scantype
                - Writes data from `/cache`
            - Cleans up old indices (deletes any scans older than 4 days)
            - Copies JSON from /cache into S3
        - There’s a [rudimentary attempt](https://github.com/18F/Spotlight/blob/211ffaab203985205fdf006262dea68248879656/spawn_scans.sh#L28) to sleep if a task errors, but the sleep is set for 600 (5 hrs). CircleCI kills processes that run longer than 5hrs, so subsequent tasks never run _[known issue-link?]_.
