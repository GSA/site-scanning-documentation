# Lighthouse Scan

## Summary

Lighthouse is actually a collection of scans that cover a range of performance, accessibility, SEO, and best practice topics. 

## Details 

Published by Google as an open source project in support of better websites, Lighthouse is an engine that offers dozens of different scans (called audits in the Lighthouse world), each of which measures and gives suggestions on a discrete aspect of website performance, PWA implementation, best practices, and accessibility.  One chooses which audits to run when setting up Lighthouse.  The list of available options can be found [here](https://web.dev/learn/#lighthouse), and the code for each audit [here](https://github.com/GoogleChrome/lighthouse/tree/master/lighthouse-core/audits).   In our case, we are running these audits, in order to discern certain performance and accessibility information:  

```
    'color-contrast',
    'font-size',
    'image-alt',
    'input-image-alt',
    'performance-budget',
    'tap-targets',
    'timing-budget',
    'total-byte-weight',
    'unminified-css',
    'unminified-javascript',
    'uses-text-compression',
    'viewport',
    'speed-index' 
```


## Report Pages

* [Spotlight 2.0 Performance Report](https://federalist-05e4f538-b6c2-49a0-a38c-262ad093ad6d.app.cloud.gov/site/18f/spotlight-ui/performance)

## Direct Data Links

* [Scan Data (JSON)](https://site-scanning.app.cloud.gov/api/v1/scans/lighthouse/)
* [Scan Data (CSV)](https://site-scanning.app.cloud.gov/api/v1/scans/lighthouse/csv/)
* [Scan Data for a Particular Website (e.g. 18f.gov)](https://site-scanning.app.cloud.gov/api/v1/scans/lighthouse/18f.gov)

#### Relevant Policy

* Section 508 requirements (there are many)
* SEO requirements (there are many)
* Mobile-friendliness requirements (there are many) 

