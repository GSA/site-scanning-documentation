I almost thought that [OPM Federal Agencies List dataset](https://www.opm.gov/about-us/open-government/Data/Apps/Agencies/) would be the best option for a consistent list and naming convention to use, as outlined below. However, it has several issues with it.  Most of them could be addressed with discrete modifications, sourced from the [OMB Agency/Bureau code list](https://bidenwhitehouse.archives.gov/wp-content/uploads/2018/06/a11.pdf#page=849).  But most critically, the dataset has not been kept up to date to an unknown degree.  

- [Vanilla OPM Agency/Subelement List](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/datasets/Agency-Bureau_List-OPM.csv)
- [Proposed Modified Agency/Subelement List](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/datasets/Agency-Bureau_List-OPM-modified.csv)

## Advantanges

- The dataset comes from an authoritative source and is available as a machine-readable file.
- Comparisons of the dataset against alternatives show it to have a good balance between being comprehensive but not overly inclusive.  


## Disadvantages 

- The dataset is out of date and does not include recently created agencies and name changes.  
- The names are in all caps.
- There's currently a bug that causes names that have a hyphen to drop everything after that character.
- The Army, Navy, and Air Force are framed as peers of Defense instead of subcomponents.
- Legislative and Judicial agencies are not included.
- Agencies without subelements repeat the agency name in that field.
- No Department of Energy subelements.  


## Alternatives 
- OMB List of Agency and Bureau Codes - [OMB Circular A-11, Appendix C](https://bidenwhitehouse.archives.gov/wp-content/uploads/2018/06/a11.pdf#page=849)
- _(Others listed [here](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/proposals/agency-bureau-list.md#details))_

## Possible Users

- Site Scanning
- dotgov.gov
- Digital Analytics Program

## Workflow
- Take the [bulk XML file](https://www.opm.gov/about-us/open-government/Data/Apps/agencies/agencies.xml) that OPM provides.
- Remove extraneous columns, leaving only `name` and `agency_subelement`.  
- Use the `=proper()` function to correct casing.
- Move `Department Of The Air Force`, `Department Of The Army`, `Department Of The Navy` under `Department Of Defense`.  In other words, delete the rows that have those as `Agency` and add three rows under Defense for them.
- Add in agencies that were created since the dataset was last updated (details below).
- Make miscellaneous casing corrections (details below).  



## Details of Suggested Edits to OPM dataset

- Casing corrections:
  - Lowercase the `S` in `Department of Labor - Women'S Bureau`
  - Uppercase the `H` and `S` in `Department of Homeland Security - Dhs Headquarters`
  - National Aeronautics And Space Administration	Headquarters, Nasa...

## Possible Other Edits to OMB dataset to consider

- Correct agency names that are impacted by the hyphen bug (details below).
- Correct agency names that are impacted by the hyphen bug 
- Add in agencies that were created since the dataset was last updated 
- Make miscellaneous casing corrections 
- Lowercase `Of`, `And`, etc. 
