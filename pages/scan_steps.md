
This is a description of the step-by-step technical process by which we 'scan' each Target URL.  

* Order of scans 
  * For each scan, order of operations 
    * For each operation - a human readable but technical description of what happens and what data fields are written
    * For each operation - a link to the source code 
  * For each scan, a link to the source code  
* Link to the order of scans  


Key file - https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/core-scanner.service.ts

The scans listed there don't necessarily run in order (it's async - https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/core-scanner.service.ts#L27) 


https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/core-scanner.service.ts#L27

there's five scans - notFound, primary, robotsTxt, sitemapXml, dns.  

They are completely separate from each other and don't talk to each other.  


for the primary scan - the source code is in https://github.com/GSA/site-scanning-engine/tree/75d5b532c556291353b3dd73fbc4fd2fa3b4a214/libs/core-scanner/src/scans, but first here - https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/pages/primary.ts

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

