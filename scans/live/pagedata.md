# Page Data Scan

## Summary

This scan checks certain locations for a range of file characteristics.  


## Details 

Specifically, the page data scan searches the target URL for: 

* server response code
* final url
* whether the final url is in the same domain
* MIMEtype
* content_length
* opendata_conforms_to
* codegov_measurementtype

## Report Pages

* [Spotlight 1.0 Code.json Report](https://site-scanning.app.cloud.gov/search200/200-codejson/?200page=/code.json&mimetype=application/json)
* [Spotlight 1.0 Data.json Report](https://site-scanning.app.cloud.gov/search200/200-data.json/?200page=/data.json&mimetype=application/json)
* [Known code.json locations Report](https://cg-bbe64741-a601-484f-bc3b-e8eef3c28590.app.cloud.gov/site/18f/site-scanning-dashboard/codegov/)
* [Known data.json locations Report](https://cg-bbe64741-a601-484f-bc3b-e8eef3c28590.app.cloud.gov/site/18f/site-scanning-dashboard/datagov/)

## Direct Data Links

* [Scan Data (JSON)](https://site-scanning.app.cloud.gov/api/v1/scans/pagedata/)
* [Scan Data (CSV)](https://site-scanning.app.cloud.gov/api/v1/scans/pagedata/csv/)
* [Scan Data for a Particular Website (e.g. 18f.gov)](https://site-scanning.app.cloud.gov/api/v1/scans/pagedata/18f.gov)

## Future Plans 

* Pull out further actionable data from the machine readable files (e.g. points of contact for the data.json files?)
