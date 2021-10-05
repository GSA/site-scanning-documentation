
## Updating the digital.gov pages

* File a pull request to [this repo](https://github.com/GSA/digitalgov.gov/tree/main/content/guides/site-scanning).  A preview can be seen at `https://federalist-ecc58765-2903-48b3-920c-5d93318ad084.app.cloud.gov/preview/gsa/open-gsa-redesign/NAME-OF-BRANCH/api/site-scanning-api/`.  When the pull request is ready, comment on it to that effect and add Sara Cope as a reviewer.  They should get to it soon but if a while goes by (~a week), ask over in #digitalgov to make sure it's on their radar.  

## Updating the api docs

* File a pull request to [this repo](https://github.com/GSA/open-gsa-redesign/blob/master/_apidocs/site-scanning-api.md).  A preview can be seen at `https://federalist-64fd1e70-2b76-44eb-96ef-4bc40b4b3bac.app.cloud.gov/preview/18f/site-scanning-query-builder/NAME-OF-BRANCH/`.  When the pull request is ready, comment on it to that effect and email api.ciss@gsa.gov with a link to the PR to ask them to merge.  

## Updating the Target URL list
* Overwrite [this file](https://github.com/GSA/data/blob/master/dotgov-websites/site-scanning/current-federal-subdomains.csv) with the new CSV
* Log into cloud.gov in the terminal
* Run `./cloudgov-run-ingest.sh` at the bash prompt



