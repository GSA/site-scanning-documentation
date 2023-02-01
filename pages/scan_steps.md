
This is a description of the step-by-step technical process by which we 'scan' each Target URL.  

* Order of scans 
  * For each scan, order of operations 
    * For each operation - a human readable but technical description of what happens and what data fields are written
    * For each operation - a link to the source code 
  * For each scan, a link to the source code  
* Link to the order of scans  


First off, before any scans take place, the process of ingesting the target URL list into the database populates the following fields: 
* Target URL
* Target URL - Base Domain 
* Target URL Base Domain - Agency Owner	
* Target URL Base Domain - Bureau Owner	
* Target URL Base Domain - Branch	
* Source List - Federal .Gov Domains	
* Source List - Digital Analytics Program	
* Source List - pulse.cio.gov Snapshot	
* Source List - Other	



When scanning commences, [this core file](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/core-scanner.service.ts#L31) dictates which scans are run.  Due to the nature of the code base, the scans run asynchronously (i.e. they don't necessarily run in the order they are written in the code). Each scan operates separately and don't talk to each other.  

The primary scan loads a 



    urlScan,
    dapScan,
    seoScan,
    thirdPartyScan,
    uswdsScan,
    loginScan,
    
    

* The technical details of how each scan operates can be found in the following locations: 
  * [primary](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/pages/primary.ts)  (and then [here](https://github.com/GSA/site-scanning-engine/tree/main/libs/core-scanner/src/scans))
  * [notFound](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/pages/not-found.ts)
  * [robotsTxt](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/pages/robots-txt.ts)
  * [sitemapXml](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/pages/sitemap-xml.ts)
  * [dns](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/pages/dns.ts)






Key file - https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/core-scanner.service.ts






for the other four - scan source code is in - https://github.com/GSA/site-scanning-engine/tree/75d5b532c556291353b3dd73fbc4fd2fa3b4a214/libs/core-scanner/src/pages


For the primary scan, the target URL is loaded by puppeteer into a headless chrome browser.   


url scans -  https://github.com/GSA/site-scanning-engine/blob/75d5b532c556291353b3dd73fbc4fd2fa3b4a214/libs/core-scanner/src/scans/url-scan.ts#L21-L29
it's being passed the http response that's being received by the browser and then pulls out these figures.  


NOTE - the fields that were in the target URL list are put into the database when things are ingested the first time.  same with source fields  

for dap, we capture the outbound requests that take place.  




For the robotsTXT scan, 

...

For the sitemapxml scan,  

...

For the notFound scan,  

...
doesn't use puppeteer - uses an https service that is passed through to it.  

random url suffix is generated at this point - https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/pages/not-found.ts#L13-L14

For the dns scan, 

...

doesn't use puppeteer - uses a node.js library 

