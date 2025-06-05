In order to more efficiently operate the federal web space, it makes sense to analyze the current webspace with an eye to reducing and coalescing them.  This proposal articulates several frameworks to do so and how to use Site Scanning data in the process.  

### Low traffic sites

Digital Analytics Program (DAP) data provides website traffic for much of the federal web presence.

There are several ways to interact with this data.  

1) For a higher level, visual experience, go to https://analytics.usa.gov/visualizations and use the drop down to select an agency.  Then, you can click within the graphic to drill down further and further.  This is a helpful starting point, but likely not good for fine grain analysis.
2) Perhaps the easiest yet still substantive route is to begin at https://analytics.usa.gov/data, then download the [Top Hostnames CSV](https://analytics.usa.gov/data/live/top-100000-domains-30-days.csv) and open it in Sheets or Excel.  There is again an agency dropdown at the top of the page, which allows one to filter for an agency and then download the Top Hostnames CSV specific to that agency.  
3) Any federal employee can gain direct access to the data in DAP [here](https://digital.gov/guides/dap/get-started-with-dap#step-1-register-as-a-dap-user).  Once you gain access, perhaps the most useful page is the [Domains Report](https://analytics.google.com/analytics/web/#/p393249053/reports/explorer?params=_u..nav%3Dmaui&ruid=19233ACB-2A11-4B0A-9D71-E45EBCE91AA3&collectionId=5935400244&r=6668527931).  A sample file from this page that shows traffic data by domain over the past year can be found [here](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/datasets/Domains_Report-DAP-1-Year-6-5-25.csv).  The problem one finds when looking at it is that the long tail of data is _incredibly_ long and the data is very messy.  These aren't faults in the system, but rather a simple fact of the federal web presence and how google analytics snippets get copied around the internet.
4) Take the full [Site Scanning snapshot](https://api.gsa.gov/technology/site-scanning/data/site-scanning-latest.csv) and open it in Sheets or Excel.  Filter the sheet to remove rows that do not have a result in `Pageviews`.  Sort by Pageviews.

With this data, one could pull a list of all sites with less than 500 pageviews in the past month and ask each relevant agency to - within X days - provide a justification for the site's continued operation, clarify if the DAP snippet is not implemented correctly and correct if so, or to deprecate the website.  


Caveats:  

Seasonal changes in traffic are important to factor in.  Does a candidate website have a certain time of year where their usage is focused and thus only a partial view of a year's traffic wouldn't reflect its true use?  The Google Analytics report page allows one to select for the past 12 months but even then a specific candidate should be further inspected to guard against this.   




### Out of date sites 



### Duplicative or overlapping sites 



### Disproportionately Expensive 


### Out of Scope for an Agency



## Related Proposals 

#### Classify Sites 
- Create a new file or overlap with the federal website directory to promulgage a labelling system with these categories:
  - Content, Application, Public Service, Internal, Infrastructure


