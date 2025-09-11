## Sept 2025 Update 

- [2025 A-11 Agency/Bureau Codes Table](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/datasets/omb_bureau_codes-2025.csv) (Derived from [here](https://www.whitehouse.gov/wp-content/uploads/2025/08/a11.pdf#page=715))
- [2025 A-11 Agency/Bureau Codes Table - Flattened](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/datasets/Agency-Bureau_List-OMB-2025.csv)
- [2025 A-11 Agency/Bureau Codes Table - With Proposed Changes](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/datasets/Agency-Bureau_List-OMB-modified-2025.csv)

========================

One of the two best solutions for applying a consistent agency/bureau listing would be to employ [OMB's agency/bureau code list](https://bidenwhitehouse.archives.gov/wp-content/uploads/2018/06/a11.pdf#page=849).  

* [Vanilla OMB Agency/Bureau List](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/datasets/Agency-Bureau_List-OMB.csv)
* [Proposed Modified Agency/Bureau List](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/datasets/Agency-Bureau_List-OMB-modified.csv)
* [Crossmatch of current dotgov agency/bureau entries against the proposed modified list](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/datasets/Agency-Bureau_Lists--OMB-dotgov_crossmatch.csv)

## Advantages
- The dataset comes from an authoritative source.
- The dataset is up to date (July 2024).
- The dataset spans all three branches.
- Dataset is already used by the [Project Open Data schema](https://resources.data.gov/resources/dcat-us/), data.gov, and agency enterprise data inventories.  

## Disadvantages 
- The dataset is available via PDF and must be converted to a machine-readable format.
- It is sometimes overly-inclusive of what many would consider a 'bureau', especially in the use of 'catch all' entries like 'other' or 'allowances'.  At the same time, this field is sometimes under-utilized, with entities that many would think of as bureaus not being included, especially in the Department of Energy.  


## Alternatives 
- OPM's [Federal Agencies dataset](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/proposals/opm-agency-list.md)
- (Others listed [here](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/proposals/agency-bureau-list.md#details))

## Workflow
- Take a recent copy of [OMB circular A-11, Appendix C](https://bidenwhitehouse.archives.gov/wp-content/uploads/2018/06/a11.pdf#page=849).
- Convert the table into a spreadsheet format.
- Remove the current bureaus listed for the Department of Defense and replace them with the entities listed at [the end of Appendix C](https://bidenwhitehouse.archives.gov/wp-content/uploads/2018/06/a11.pdf#page=861): Navy, Marine Corps; Army; Air Force; Defense-wide.  Remove `--Military Programs` from the DoD agency name.
- Remove bureau entries for GSA and FDIC.
- Promote the bureau entries for the following entries up to agency level:  `International Assistance Programs`, `Judicial Branch`, `Legislative Branch`, and `Other Defense Civil Programs`.  


### Possible Other Edits to OMB dataset to consider


- Remove non-bureau catch all bureau entries, e.g. `Other` and `Allowances`.
  - USDA - Buildings and Facilities
  - USDA - Executive Operations
  - Commerce - Departmental Management
  - Education - Departmental Management
  - Energy - Departmental Administration
  - Energy - Energy Programs
  - Energy - Environmental and Other Defense Activities
  - HHS - Allowances
  - HHS - Departmental Management
  - DHS - Analysis and Operations
  - DHS - Management Directorate
  - DHS - Science and Technology (or should this be renamed?)
  - HUD - Housing Programs
  - HUD - Housing Supply
  - HUD - Management and Administration
  - HUD - Policy Development and Research
  - DOJ - General Administration
  - DOJ - Interagency Law Enforcement
  - DOJ - Departmental Management
  - State - Other
  - State - International Commissions
  - State - International Organizations and Conferences
  - Interior - Department-Wide Programs
  - Interior - Departmental Offices
  - Interior - Insular Affairs (or should be renamed?)
  - Treasury - Departmental Offices
  - Treasury - Fiscal Service (or should be renamed?)
  - Treasury - Interest on the Public Debt
  - DOT - Maritime Administration
  - VA - Benefits Programs
  - EOP - Unanticipated Needs
- Remove agency repeated at bureau level?
- Rename agencies by changing U.S. to United States
- Consider renaming agencies by removing superflous `United States `
- Add in entities that are commonly thought of as agencies, e.g. FERC.
  - DOD?







