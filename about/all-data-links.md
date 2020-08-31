
## Existing Endpoints


/api/v1/
/api/v1/date/{date}/domains/
/api/v1/date/{date}/domains/{domain}/
/api/v1/date/{date}/domains/{domain}/{scantype}/
/api/v1/date/{date}/lists/{scantype}/agencies/
/api/v1/date/{date}/lists/{scantype}/domaintypes/
/api/v1/date/{date}/lists/{scantype}/values/{field}/
/api/v1/date/{date}/lists/{scantype}/values/{field}.{subfield}/
/api/v1/date/{date}/scans/
/api/v1/date/{date}/scans/{scantype}/
/api/v1/date/{date}/scans/{scantype}/{domain}/
/api/v1/domains/
/api/v1/domains/{domain}/
/api/v1/domains/{domain}/{scantype}/
/api/v1/lists/dates/
/api/v1/lists/{scantype}/agencies/
/api/v1/lists/{scantype}/domaintypes/
/api/v1/lists/{scantype}/values/{field}/
/api/v1/lists/{scantype}/values/{field}.{subfield}/
/api/v1/meta/
/api/v1/scans/
/api/v1/scans/{scantype}/
/api/v1/scans/{scantype}/{domain}/ 


## Examples, reordered

_Unless otherwise mentioned, the data is from the most recent date._


* Swagger -  https://site-scanning.app.cloud.gov/api/v1/  
* Meta -  https://site-scanning.app.cloud.gov/api/v1/meta/  
  
  
* All scanning data - https://site-scanning.app.cloud.gov/api/v1/domains/  
* All scanning data for one website - https://site-scanning.app.cloud.gov/api/v1/domains/18f.gov/  
* DAP scan data for one website - https://site-scanning.app.cloud.gov/api/v1/domains/18f.gov/dap/  
* All DAP scan data - https://site-scanning.app.cloud.gov/api/v1/scans/dap/  
* DAP scan data for one website - https://site-scanning.app.cloud.gov/api/v1/scans/dap/18f.gov/  
* All scanning data from a certain date - https://site-scanning.app.cloud.gov/api/v1/date/08-30-2020/domains/  
* All scanning data for one website from a certain date - https://site-scanning.app.cloud.gov/api/v1/date/08-30-2020/domains/18f.gov/  
* DAP scanning data for one website from a certain date - https://site-scanning.app.cloud.gov/api/v1/date/08-30-2020/domains/18f.gov/dap/  
* All DAP scan data from a certain date - https://site-scanning.app.cloud.gov/api/v1/date/08-30-2020/scans/dap/  
* DAP scan data from a certain date for one website - https://site-scanning.app.cloud.gov/api/v1/date/08-30-2020/scans/dap/18f.gov/  
   
    
* List of dates for which there is scan data - https://site-scanning.app.cloud.gov/api/v1/lists/dates/  
* List of agencies represented in the DAP scan data - https://site-scanning.app.cloud.gov/api/v1/lists/dap/agencies/  
* List of domaintypes (branches) represented in the DAP scan data - https://site-scanning.app.cloud.gov/api/v1/lists/dap/domaintypes/  
* List of data fields in the DAP scan data - https://site-scanning.app.cloud.gov/api/v1/lists/dap/values/data/  
* List of data subfields in the 'dap_detected' in the data field in the DAP scan data - https://site-scanning.app.cloud.gov/api/v1/lists/dap/values/data.dap_detected  
* List of active scans - https://site-scanning.app.cloud.gov/api/v1/scans/  
* List of agencies represented in the DAP scan data from a certain date - https://site-scanning.app.cloud.gov/api/v1/date/08-30-2020/lists/dap/agencies/  
* List of domaintypes (branches) represented in the DAP scan data from a certain date- https://site-scanning.app.cloud.gov/api/v1/date/08-30-2020/lists/dap/domaintypes/  
* List of data fields in the DAP scan data on a certain date- https://site-scanning.app.cloud.gov/api/v1/date/08-30-2020/lists/dap/values/data/  
* List of data subfields in the 'dap_detected' in the data field in the DAP scan data from a certain date- https://site-scanning.app.cloud.gov/api/v1/date/08-30-2020/lists/dap/values/data.dap_detected  
* List of active scans from a certain date - https://site-scanning.app.cloud.gov/api/v1/date/08-30-2020/scans/  

