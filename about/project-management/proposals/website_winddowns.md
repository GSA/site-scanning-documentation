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

We've investigated three methods for doing this, two of which are still active and available but only one of which is possibly useful.  

#### Old `lastmod` dates

Virtually every website should have a sitemap.xml and a common if not required metatag in sitemaps is the `lastmod` field.  The `sitemap_xml_lastmod` field in Site Scanning data captures the most recent lastmod date in a sitemap.  In a recent scan, 1354 sites have results for this field.  Of those: 1017 have lastmod dates from 2025, 110 from 2024, 71 from 2023; 33 from 2022, 26 from 2021, 14 from 2020, 62 from the 2010s, and 6 from the 2000s. 

At a minimum, sites with lastmod dates in the 2000s and 2010s could reasonable be put to their respective agencies with the question of whether the sites are still needed.  

#### Unchanging hash marks for website homepages and sitemaps

A more powerful indicator has been running since roughly Feb 20, 2025.  One could take the [2-20-25 snapshot](https://api.gsa.gov/technology/site-scanning/data/archive/csv/weekly-snapshot-2025-02-20T12:01:58.490Z.csv) and compare the `page_hash` and `sitemap_xml_page_hash` fields (columns AE and CF) and then the current snapshot and determine whether the homepage and/or sitemap have changed in any way.  This is not likely useful enough for the purposes of identifying stale websites since the data only goes back 4 months, but over time will increasingly become so.  Underlying it though is a judgment call of when an unchanging website is indicative of something greater.  Is that threshold a year?  Two?  Regardless, the resulting list should be run by the relevant agencies to request that the clarify if the site is still needed and to justify so/briefly explain why it has not changed any if so.  

#### Other date-based metafields

There's a variety of other metatags that could be helpful, such as `revised`, `date`, or `last-modified`, however a 2024 analysis found that these and other potentially useful tags are profoundly under-used ([exact stats here](https://github.com/GSA/site-scanning/issues/869#issuecomment-2009879132)). As a result, these fields are not likely to be of use, though it's worth having thought through their potential use.  


### Duplicative or overlapping sites 

At the moment, I believe that our best means of approaching this is to take the below cut of Site Scanning data and use AI tools to analyze them at scale and suggest where there's substantial overlap in the substance of any sites.  

The complete Site Scanning dataset should be trimmed down by: 
- Removing non-live sites
- Removing redirects
- Collapsing any Open Graph titles or descriptions into the title and description columns if the respective cell is empty.
- Collapsing the www_title into the title field if the latter cell is empty.  
- Removing all columns but: title, description, keyword, domain, base_domain, agency, bureau

A snapshot of the 6-10-25 scan data cut to the above specifications can be found [here](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/datasets/website-metadata-6-10-25.csv).  

GSA currently has two sets of AI resources available to staff:  chat.gsa.gov and the Gemini integration directly in Google Suite.  The latter is convenient as it can be used direction in sheets.  However, my attempts with it so far have been unproductive as it seems to only be engaging this data characters in cells in the sheet, not as representations of websites beyond the sheet.  For example, 'which of these sites are duplicative of each other?' only returns exact analysis of whether any fields are the exact same for any sites.  So far, I can't get it to think a bit more abstractly about what these rows convey.  

The other resource we have access to is chat.gsa.gov, which currently offers claude and meta AI engines.  One initial blocker is that our implementation limits the filetypes that can be uploaded for a prompt to PDFs, documents, and image files.  Spreadsheet files cannot be uploaded, which limits our ability to get it to interpret the associated title/description/keyword metadata.  

I've tried to circumvent this by just taking the column of domains and saving it as [a txt file to upload](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/datasets/website-list-6-10-25.txt).  This worked but the ensuing analysis didn't actually look at the websites themselves over the internet.  Rather, it just looked at the domains themselves and basically grouped those on the same base domain as potentially duplicative.  

At this time, this effort hasn't proven fruitful, but within the near future, the tools available to us may change and improve and better enable this.  

### Ideas for other models 

Here's a running list of other potential frameworks for tackling this issue.  They would need further research on feasibility and practical application.  

- Disproportionately Expensive
- Out of Scope for Agency


## Related Proposals 

### Classify Sites 

- Create a new file or overlap with the [federal website directory](https://github.com/GSA/federal-website-directory/blob/main/us-government-website-directory.csv) to promulgate a labeling system with these categories:
  - Content, Application, Public Service, Internal, Infrastructure
- This could then populate a new tag field in Site Scanning, and be used to significantly improve the mapping of the federal web presence.   

### Proactive Curation

Another approach would be to employ a central authority to coordinate a cross-government editorial engagement that convenes agencies to cooperatively map out a unified, integrated federal web presence and drive agencies to then fit into it.  This could allow a turn away from the utterly distributed, one-might-say schizophrenic web presence that currently exists and could lead to the reduction of duplicative websites.  

