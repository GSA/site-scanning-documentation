# Status Scan

## Summary

A scan to check each domain for the presence or absence of a file at specific locations, specifically by analyzing the server response code at that location.  Currently checks for the following, where x.gov = the target URL.  

* x.gov
* x.gov/cj
* x.gov/code.json
* x.gov/coronavirus
* x.gov/data
* x.gov/data.json
* x.gov/developer
* x.gov/digitalstrategy
* x.gov/digitalstrategy/FITARAmilestones.json
* x.gov/digitalstrategy/bureaudirectory.json
* x.gov/digitalstrategy/costsavings.json
* x.gov/digitalstrategy/datacenteroptimizationstrategicplan.json
* x.gov/digitalstrategy/governanceboards.json
* x.gov/open
* x.gov/privacy
* x.gov/redirecttest-foo-bar-baz
* x.gov/robots.txt
* x.gov/sitemap.xml


## Details 

### x.gov/

#### Summary

Simply sees if there is a page or file at the initial target URL.  This provides useful perspective when analyzing the other locations (e.g. if there's nothing at x.gov, perhaps there's no need for there to be anything at x.gov/sitemap.xml).  



### x.gov/cj

#### Summary

Detects the presence of a congressional justification page.  

#### Relevant Policy

* "Make your full congressional budget justification materials, including your performance plan submission,
available to the public and post the materials on the Internet at a vanity URL (for example
agencyXYZ.gov/CJ) within two weeks after transmittal of those materials to the Congress." - _[OMB Circular No.A-11](https://www.whitehouse.gov/wp-content/uploads/2018/06/a11.pdf)_

#### Stakeholders
 
* OMB - Assist in the discovey of congressional justification pages.  



### x.gov/code.json

#### Summary

Detects the presence of enterprise code inventories.  

#### Relevant Policy

* "Agencies shall fill out this information based on a metadata schema that OMB will
provide on Code.gov." - _[OMB M-16-21](https://www.whitehouse.gov/sites/whitehouse.gov/files/omb/memoranda/2016/m_16_21.pdf)_
* "Agencies should make the “code.json” available in the root folder of their website (e.g., https://www.agency.gov/code.json)." - _[code.gov](https://code.gov/about/compliance/inventory-code)_

#### Stakeholders

* Code.gov - Detects enterprise code inventories that may have been created but not shared with the code.gov team.  Allows this team to then add these inventories to code.gov harvest list.  
* OMB - Automates a part of the compliance review for OMB M-16-21.  



### x.gov/coronavirus

#### Summary

Detects the presence of a coronavirus information page.  



### x.gov/data

#### Summary

Detects the presence of a data hub.

#### Relevant Policy

* "Any datasets in the agency’s enterprise data inventory that can be made publicly available must be listed at www.[agency].gov/data in a human- and machine-readable format that enables automatic aggregation by Data.gov and other services (known as “harvestable files”), to the extent practicable." - _[OMB M-13-13](https://project-open-data.cio.gov/policy-memo/)_
* "Agencies must create a process to engage with customers, through their www.[agency].gov/data pages and other necessary means, to solicit help in prioritizing the release of datasets and determining the most usable and appropriate formats for release." - _[OMB M-13-13](https://project-open-data.cio.gov/policy-memo/)_
* "Agencies must provide a machine-readable Public Data Listing at
www.[agency].gov/data.json in accordance with the Project Open Data metadata schema and
a human-readable Public Data Listing at www.[agency].gov/data." - _[OMB M-17-06](https://www.whitehouse.gov/sites/whitehouse.gov/files/omb/memoranda/2017/m-17-06.pdf)_
* "Agencies must provide a public two-way feedback mechanism available via
www.[agency].gov/data." - _[OMB M-17-06](https://www.whitehouse.gov/sites/whitehouse.gov/files/omb/memoranda/2017/m-17-06.pdf)_


#### Stakeholders

* OMB - Automates a part of the compliance review for OMB M-13-13 and M-17-06
* External Developers - Open data is a valuable commodity and the ability to readily find government data hubs facilitates its use.  


### x.gov/data.json


#### Summary

Detects the presence of enterprise data inventories.  

#### Relevant Policy

* " A requirement for the head of each agency, in accordance with a procedure established by the Director, to submit for inclusion in the Federal data catalogue maintained under subsection (c) the comprehensive data inventory developed pursuant to subparagraph (C), including any real-time updates to such inventory, and data assets made available in accordance with subparagraph (E) or any electronic hyperlink providing access to such data assets." _[Foundations for Evidence-Based Policymaking Act of 2018](https://www.congress.gov/bill/115th-congress/house-bill/4174/text)_
* "Any datasets in the agency’s enterprise data inventory that can be made publicly available must be listed at www.[agency].gov/data in a human- and machine-readable format that enables automatic aggregation by Data.gov and other services (known as “harvestable files”), to the extent practicable." - _[OMB M-13-13](https://project-open-data.cio.gov/policy-memo/)_
* "To improve the discoverability and usability of data assets, all federal agencies must develop a Public Data Listing, which contains a list of all data assets that are or could be made available to the public. This Public Data Listing, posted at www.[agency].gov//data.json, would typically be a subset of the agency’s Inventory." - _[Supplemental Guidance on the Implementation of M-13-13](https://project-open-data.cio.gov/implementation-guide/)_
* "Agencies must provide a machine-readable Public Data Listing at
www.[agency].gov/data.json in accordance with the Project Open Data metadata schema and
a human-readable Public Data Listing at www.[agency].gov/data." - _[OMB M-17-06](https://www.whitehouse.gov/sites/whitehouse.gov/files/omb/memoranda/2017/m-17-06.pdf)_


#### Stakeholders

* Data.gov - Detects enterprise data inventories that may have been created but not shared with the data.gov team.  Allows this team to then add these inventories to data.gov harvest list.  
* OMB - Automates a part of the compliance review for OMB M-17-06 and M-13-13 


### x.gov/developer


#### Summary
Detects the presence of developer pages and application programming interfaces (APIs).

#### Relevant Policy

* "Agencies must provide their existing and new web APIs and relevant open source
documentation at www.[agency].gov/developer." - _[OMB M-17-06](https://www.whitehouse.gov/sites/whitehouse.gov/files/omb/memoranda/2017/m-17-06.pdf)_
* "Agencies should make data available in multiple formats according to their customer needs. For example, high-volume datasets of interest to developers should be released using bulk downloads as well as Application Programming Interfaces (APIs).” - _[OMB M-13-13](https://obamawhitehouse.archives.gov/sites/default/files/omb/memoranda/2013/m-13-13.pdf)_
* "Ensure all new IT systems follow the open data, content, and web API policy and operationalize agency.gov/developer pages." - _[Digital Government Strategy](https://obamawhitehouse.archives.gov/sites/default/files/omb/egov/digital-government/digital-government.html)_


#### Stakeholders
* api.data.gov - Discover open APIs for inclusion in https://api.data.gov/ for cost savings and improved public services
* OMB - Automates a part of the compliance review for OMB M-17-06 and M-13-13.



### x.gov/digitalstrategy


#### Summary
Detects the presence of a digital strategy.

#### Relevant Policy

* "Each agency must publicly post its governance plan on its Digital Strategy page at
www.[agency].gov/digitalstrategy/ and update this page to reflect the current status of the
agency’s digital governance structure." - _[OMB M-17-06](https://www.whitehouse.gov/sites/whitehouse.gov/files/omb/memoranda/2017/m-17-06.pdf)_
* "Agencies must provide a continually updated Data Publication Process at
www.[agency].gov/digitalstrategy." - _[OMB M-17-06](https://www.whitehouse.gov/sites/whitehouse.gov/files/omb/memoranda/2017/m-17-06.pdf)_
* "Ultimately, this Strategy will ensure that agencies use emerging technologies to serve the public as effectively as possible." - _[Presidential Memorandum -- Building a 21st Century Digital Government](https://obamawhitehouse.archives.gov/the-press-office/2012/05/23/presidential-memorandum-building-21st-century-digital-government)_


#### Stakeholders
* OMB - Automates a part of the compliance review for OMB M-17-06 


### x.gov/digitalstrategy/FITARAmilestones.json


#### Summary
Detects the presence of a FITARA Milestones document.  

#### Relevant Policy

* "Post a “fitaramilestones.json” file to “agency.gov”/digitalstrategy with the following contents." - _[management.cio.gov](https://management.cio.gov/schema/#FITARA)_
* "The DCOI further requires that agencies’ public FITARA Milestones files are updated at their current agencyhomepage.gov/digitalstrategy/FITARAmilestones.json pages to include a minimum of five (5) milestones per fiscal year to be achieved in accordance with the DCOI." - _[management.cio.gov](https://management.cio.gov/schema/#FITARA)_


#### Stakeholders
* OMB - Automates a part of the compliance review for FITARA.  


### x.gov/digitalstrategy/FITARAmilestones.json


#### Summary
Detects the presence of a FITARA Milestones document.  

#### Relevant Policy

* "Post a “fitaramilestones.json” file to “agency.gov”/digitalstrategy with the following contents." - _[management.cio.gov](https://management.cio.gov/schema/#FITARA)_
* "The DCOI further requires that agencies’ public FITARA Milestones files are updated at their current agencyhomepage.gov/digitalstrategy/FITARAmilestones.json pages to include a minimum of five (5) milestones per fiscal year to be achieved in accordance with the DCOI." - _[management.cio.gov](https://management.cio.gov/schema/#FITARA)_


#### Stakeholders
* OMB - Automates a part of the compliance review for FITARA.  



### x.gov/digitalstrategy/bureaudirectory.json


#### Summary
Detects the presence of a Bureau IT Leadership directory.  

#### Relevant Policy

* "Each agency is expected to post a JSON file for their Bureau IT Leadership Directory to the following URL path: agency.gov/digitalstrategy/bureaudirectory.json" - _[management.cio.gov](https://management.cio.gov/schema/#bureaus)_


#### Stakeholders
* OMB - Automates a part of the compliance review for FITARA.  



### x.gov/digitalstrategy/costsavings.json


#### Summary
Detects the presence of an IDC Realized Cost Savings and Avoidance file.   

#### Relevant Policy

* "Post your finished file on your agency’s agency.gov/digitalstrategy/costsavings.json" - _[management.cio.gov](https://management.cio.gov/schema/#savings)_


#### Stakeholders
* OMB - Automates a part of the compliance review for FITARA.  



### x.gov/digitalstrategy/datacenteroptimizationstrategicplan.json


#### Summary
Detects the presence of a Data Center Optimization Initiative Strategic Plan.   

#### Relevant Policy

* "Parts 1 – 5 above are required to be posted publicly in machine-readable JSON format at [agencyhomepage].gov/digitalstrategy/datacenteroptimizationstrategicplan.json." - _[management.cio.gov](https://management.cio.gov/schema/#DCOI)_


#### Stakeholders
* OMB - Automates a part of the compliance review for FITARA and OMB M-19-19.  




### x.gov/digitalstrategy/governanceboards.json


#### Summary
Detects the presence of a CIO Governance Board Membership List.   

#### Relevant Policy

* "Each agency is expected to post a JSON file for their CIO Governance Board Membership List to the following URL path: [agency.gov]/digitalstrategy/governanceboards.json" - _[management.cio.gov](https://management.cio.gov/schema/#governance)_


#### Stakeholders
* OMB - Automates a part of the compliance review for FITARA.  


### x.gov/open


#### Summary
Detects the presence of agency's plans for publishing open data.

#### Relevant Policy

* "Within 60 days, each agency shall create an Open Government Webpage located at http://www.[agency].gov/open to serve as the gateway for agency activities related to the Open Government Directive and shall maintain and update that webpage in a timely fashion." - _[OMB M-10-06](https://obamawhitehouse.archives.gov/sites/default/files/omb/assets/memoranda_2010/m10-06.pdf)_
* "The Open Government Directive requires agencies to maintain an Open Government web
page at www.[agency].gov/open." - _[OMB M-16-16](https://www.whitehouse.gov/sites/whitehouse.gov/files/omb/memoranda/2016/m-16-16.pdf)_

#### Stakeholders
* OMB - Automates a part of the compliance review for OMB M-10-06 and M-16-16 


### x.gov/privacy

#### Summary
Detects the presence of an agency's privacy page.

#### Relevant Policy

* "The agency’s Privacy Program Page must be located at www.[agency].gov/privacy and must be accessible through the agency’s “About” page." - _[OMB M-17-06](https://www.whitehouse.gov/sites/whitehouse.gov/files/omb/memoranda/2017/m-17-06.pdf)_
* "At the discretion of the SAOP, sub-agencies, components, and programs may maintain a sub-agency-, component-, or program-specific privacy program page. If an agency subagency, component, or program uses a domain that is different from the agency’s domain, the sub-agency-, component-, or program-specific privacy program page must be accessible through www.[sub-agency, component, or program domain].gov/privacy. " - _[OMB M-17-06](https://www.whitehouse.gov/sites/whitehouse.gov/files/omb/memoranda/2017/m-17-06.pdf)_

#### Stakeholders
* OMB - Automates a part of the compliance review for OMB M-17-06 (Has an inventory been published in the correct location?).



### x.gov/redirecttest-foo-bar-baz

#### Summary
Detects whether a website properly returns a 404 status code for a page that does not exist.  This is useful in detecting false positives for other URLs (e.g. the resolving page is an HTML page that says 404, but returns a 200 server code).  

### x.gov/robots.txt


#### Summary
Detects the presence of good search engine optimization practices.

#### Relevant Policy

* "Agencies must ensure that all content intended for public use on their website can be indexed
and searched by commonly used commercial search engines." - _[OMB M-17-06](https://www.whitehouse.gov/sites/whitehouse.gov/files/omb/memoranda/2017/m-17-06.pdf)_
* Websites “contains a search function that allows users to easily search content intended for public use." - _[21st Century Idea](https://www.congress.gov/bill/115th-congress/house-bill/5759/text)_



#### Stakeholders
* OMB - Automates a part of the compliance review for OMB M-17-06 and 21st Century IDEA.



### x.gov/sitemap.xml


#### Summary
Detects the presence of good search engine optimization practices.

#### Relevant Policy

* "Agencies must ensure that all content intended for public use on their website can be indexed
and searched by commonly used commercial search engines." - _[OMB M-17-06](https://www.whitehouse.gov/sites/whitehouse.gov/files/omb/memoranda/2017/m-17-06.pdf)_
* Websites “contains a search function that allows users to easily search content intended for public use." - _[21st Century Idea](https://www.congress.gov/bill/115th-congress/house-bill/5759/text)_


#### Stakeholders
* OMB - Automates a part of the compliance review for OMB M-17-06 and 21st Century IDEA.





## Future Plans

* Add searches for: data.x.gov, x.gov/developers, developer.x.gov, developers.x.gov
