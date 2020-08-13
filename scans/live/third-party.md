# Third Party Services Scan

## Summary

This scan checks to see what third party websites and services are called from a specific .gov webpage.  

## Details 

The third party services scan loads the target URL and detects which other websites are called during page load.  Common examples include Google Analytics or integrated feedback tools like Foresee or Qualtrics, but there's an enormous list of third party services that are available for a federal agencies to integrate into their websites.  Depending on the service, there's various privacy, performance, and functionality implications for the visitor.  

## Report Pages

* [Spotlight 2.0 Third Party Links Report](https://federalist-05e4f538-b6c2-49a0-a38c-262ad093ad6d.app.cloud.gov/site/18f/spotlight-ui/critical-components)
* [Spotlight 1.0 Third Party Services Report](https://site-scanning.app.cloud.gov/search200/third_parties/)

## Direct Data Links

* [Scan Data (JSON)](https://site-scanning.app.cloud.gov/api/v1/scans/third_parties/)
* [Scan Data (CSV)](https://site-scanning.app.cloud.gov/api/v1/scans/third_parties/csv/)
* [Scan Data for a Particular Website (e.g. 18f.gov)](https://site-scanning.app.cloud.gov/api/v1/scans/third_parties/18f.gov)

## Source Code 

* [GitHub](https://github.com/18F/domain-scan/blob/master/scanners/third_parties.py)


## Relevant Policy

* "Additionally, all domains should ... Encourage the use of gathering customer feedback to make improvements;" - _[Policies for Dot Gov Domain Issuance for Federal Agency Public Websites (2015)](https://obamawhitehouse.archives.gov/sites/default/files/omb/egov/memo/policies-for-dot-gov-domain-issuance-for-federal-agency-public-websites.pdf)_
* "Federal agencies using web measurement and customization technologies in a manner subject to Tier 1 or Tier 2 are authorized to use such technologies so long as the agencies ... (2) provide clear and conspicuous notice in their online Privacy Policy citing the use of such technologies, as specified in Attachment 3 ..." - _[[OMB-M-10-22](https://obamawhitehouse.archives.gov/sites/default/files/omb/assets/memoranda_2010/m10-22.pdf)]_




