The Site Scanning program maintains a number of automated processes that, together, generate useful data.  The basic flow of these events are as follows: 

- Each week, a comprehensive list of public federal .gov websites is assembled as the [Federal Website Index](https://github.com/GSA/federal-website-index/blob/main/data/site-scanning-target-url-list.csv).
  - [Process description](), including details about the sources used, how the list is combined, and which criteria are used to remove entries.
  - [Snapshots from each step in the assembly process](https://github.com/GSA/federal-website-index/tree/main/data/snapshots#readme), including which URLs are removed and which remain.  
  - [Data dictionary](https://github.com/GSA/site-scanning-documentation/blob/main/data/Target_URL_List_Data_Dictionary.csv) for the Federal Website Index.
  - A report for the assembly process, and a report about the finisheed Index are 
- Every day, the Federal Website Index is scanned by loading each target URL in a virtual browser and noting the results.  This information is the primary Site Scanning data.
  - [Scanning process description](), including what criteria are used to create each field of data.
  - [Data dictionary](https://github.com/GSA/site-scanning-documentation/blob/main/data/Site_Scanning_Data_Dictionary.csv) for the Site Scanning data
- The resulting information is stored in a database that is [queryable via API](https://open.gsa.gov/api/site-scanning-api/), but each week, a series of static snapshot of the data is generated and [made available](https://open.gsa.gov/api/site-scanning-api/#download-the-data-directly) as CSV and JSON files.
  - The ['All' snapshot](https://api.gsa.gov/technology/site-scanning/data/weekly-snapshot-all.csv) includes every URL in the Federal Website Index.  
  - The ['Primary' snapshot](https://api.gsa.gov/technology/site-scanning/data/weekly-snapshot.csv) is a subset of the initial snapshot and includes only live URLs.  This is likely the best starting point for most users.
  - 
  - 

- After these snapshots are generated, a series of reports are run that analyze or pull information out of them 
- [Schedule for the above processes is the schedule](https://github.com/GSA/site-scanning-documentation/blob/main/pages/schedule.md) for the above, automated processes.
- 



https://github.com/GSA/federal-website-index  

Needed: 
* Update each index's readme links
* process describing the index creation.
* update the data download links in the api docs
expand the rep dataset to include the target url list creation process 
* finish adding links to https://github.com/GSA/federal-website-index/tree/main/data/snapshots#readme
