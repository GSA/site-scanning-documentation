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

#### Relevant Policy

* Section 508 requirements (there are many)
* SEO requirements (there are many)
* Mobile-friendliness requirements (there are many) 

