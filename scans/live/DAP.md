# DAP Scan

## Summary

The Digital Analytics Program is a shared service that offers website analytics to federal agencies and pools the resulting data to then provide [a cross-government view of webtraffic](https://analytics.usa.gov). A website participates by [adding a code snippet](https://digital.gov/guides/dap/add-your-site-dap/) to its webpages, which this scan then detects in order to see which sites have implemented DAP.  

## Details 

The DAP scan looks for the presence of the code snippet in a target URL's source code.  It indicates whether the snippet is present or not present, enabling one to see the status of DAP implementation for an indvidual website, a complete domain, or an entire agency's web presence.  In addition, it is possible to customize the DAP snippet with any number of parameters.  The scan checks for those and includes any that it finds in the scan results.  

## Report Pages

* [Spotlight 2.0 Analytics Report](https://federalist-05e4f538-b6c2-49a0-a38c-262ad093ad6d.app.cloud.gov/site/18f/spotlight-ui/analytics)

## Direct Data Links

* [Scan Data (JSON)](https://site-scanning.app.cloud.gov/api/v1/scans/dap/)
* [Scan Data (CSV)](https://site-scanning.app.cloud.gov/api/v1/scans/dap/csv/)
* [Scan Data for a Particular Website (e.g. 18f.gov)](https://site-scanning.app.cloud.gov/api/v1/scans/dap/18f.gov)


## Relevant Policy

* "All agencies must participate in the General Service Administration’s (GSA) Digital Analytics Program (DAP) and deploy the DAP tracking code on all public facing agency websites." - _[OMB Memo M-17-06](https://www.whitehouse.gov/sites/whitehouse.gov/files/omb/memoranda/2017/m-17-06.pdf)_
* "All new websites must ... Employ the use of web analytics in partnership with the GSA Digital Analytics Program (DAP);" - _[Policies for Dot Gov Domain Issuance for Federal Agency Public Websites (2015)](https://obamawhitehouse.archives.gov/sites/default/files/omb/egov/memo/policies-for-dot-gov-domain-issuance-for-federal-agency-public-websites.pdf)_

## Data Quality Reviews

* [June 2020 Review](https://github.com/18F/site-scanning-documentation/blob/master/scans/qa_analysis/dap-scan-6-20.md)
