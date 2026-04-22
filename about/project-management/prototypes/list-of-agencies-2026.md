
- [Latest OMB A-11, Appendix C (August 2025)](https://www.whitehouse.gov/wp-content/uploads/2025/08/a11.pdf)
- [PDF trimmed to relevant pages](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/datasets/agency-list/2026/a11-August-2025-trimmed.pdf)
- [Converted to a CSV](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/datasets/agency-list/2026/A11-August-2025.csv)
- **[Edited for clarity](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/datasets/agency-list/2026/A11-August-2025-edited.csv)**
- [OPM Federal Workforce data explorer](https://data.opm.gov/explore-data/analytics/workforce-size-and-composition)
- **[Export of Department, Agency, and Subagency data - combined](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/datasets/agency-list/2026/OPM-Federal_workforce_by_appointment_type_data-03-10-2026.csv)**
- [CISA .gov Registry export](https://github.com/cisagov/dotgov-data/blob/main/current-federal.csv)

Methodology:  
- Start with the OMB A-11 agency/bureau list ([link](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/datasets/agency-list/2026/A11-August-2025.csv)).
- Make a variety of tidying edits ([link](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/datasets/agency-list/2026/A11-August-2025-edited.csv)). 
- Remove any entries which are not entities.
- Pull in agencies and sub-agency entries that exist in the OPM Fedscope list but not the OMB list.
- In the rare case of agencies with few/no bureaus or sub-agencies (e.g. Energy, State), use the 'govsourced' list of suborganizations in the .gov registry.



Questions - for some, should there be no branch? 
