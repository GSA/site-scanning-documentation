
### Conclusion

* [Final combined file](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/datasets/Agency-Suborganization-List-Combined.csv)
* [Crossmatch of OMB A-11/OPM Fedscope/CISA .gov registry agency/bureau names](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/datasets/Agency-Bureau_Lists-OMB-OPM-dotgov_crossmatch-2025.csv)
* 


Process for selecting agency and suborganization names:
- Start with the OMB A-11 agency/bureau list.
- Remove any entries which are not entities.
- Pull in agencies and sub-agency entries that exist in the OPM Fedscope list but not the OMB list.
- In the rare case of agencies with few/no bureaus or sub-agencies (e.g. Energy, State), use the govsourced list of suborganizations in the .gov registry.

Instructions for utilizing the agency/suborganization list, when populating a website inventory:  
- Only use values in Column B (Agency) for the `agency` field.
- Only use values in Column C (Sub-organization) that correspond with your agency for the `sub-organization` field.
- Any office or entity that exists below an established `sub-organization` entry should go in the `sub-organization2` field.
- If there is a desired sub-organization that is not represented in the agency/sub-organization list and is parallel with the other entries in that field, contact the Site Scanning team to request it be added to the list of first tier sub-organizations.  






-------------------

### Problem

How to line draw between `agency`, `bureau`, `office`, and `suborganization`.  

### Current State

* .gov Registry - Utilizes two levels, `organization` and `suborganization`.  "We define a suborganization as any entity (agency, bureau, office) that falls under the overarching organization."  Example [data](https://github.com/cisagov/dotgov-data/blob/main/current-federal.csv).  
* OMB - A-11 contains an appendix that tracks utilizes two levels, `agency` and `bureau`.  Example [data](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/datasets/omb_bureau_codes-2025.csv).  
* Site Scanning - Pulls in the two level data from the .gov registry but then renames it `agency` and `bureau` respectively. [Example data](https://api.gsa.gov/technology/site-scanning/data/site-scanning-latest.csv
). 
* OPM - Agency, Sub-Agency - Utilizes two levels, `agency` and `sub-agency`.  [Example data](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/datasets/OPM-AGY-9-25.csv).  


### Proposal #1

* Agency should only be populated with a value from the `agency` column in X table.
* Only the 15 executive departments should populate the `bureau` column, and they should do so only with a value from the `bureau` values associated with their department in X table.  
* `Suborganization` should be used for any entity below an agency or agency/bureau.
* Deprecate the use of `office` in this effort as it is informal and less versitile/partially in conflict with `suborganization`.



| Agency	 | Bureau, if you're a department	 | Suborganization |
| --- | --- | --- | 
| Dept. of A |  Bureau B | Office A  | 
| Dept. of A | | 	Office K |  
| Agency K |  | 	Office D |  


### Proposal #2

* Agency should only be populated with a value from the `agency` column in X table.
* Suborganization should only be populated with a value from the `suborganization` column in X table.
* Suborganization2 can be populated with anything below a suborganization listed in the `suborganization` column in X table.


| Agency	 | Suborganization | Suborganization2 |
| --- | --- | --- | 
| Dept. of A |  Bureau B | Office A  | 
| Dept. of A | Office K | 	 |  
| Agency K | Office D | 	 |  





### Proposal #3

* Start with the OMB list, fail over to OPM when necessary, and then rarely fail over to what agencies have crowdsourced already by way of the .gov registry information.



### Proposal #4

* Adopt the OPM dataset outright.
* Depreate use of `Bureau`








### Edge Cases and Questions
- What should a department put in its bureau field for an entry that has a suborganization that is not in one of its listed bureaus.
- Should we encourage non-department agencies to populate the bureau field with n/a?







Steps to Combine datasets 
- Lowercase Of, The, And, For




