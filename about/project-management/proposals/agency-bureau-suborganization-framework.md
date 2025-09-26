
### Conclusion

* [Crossmatch of OMB A-11/OPM Fedscope/CISA .gov registry agency/bureau names](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/datasets/Agency-Bureau_Lists-OMB-OPM-dotgov_crossmatch-2025.csv)
* 

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


### Proposal #2

* Adopt the OPM dataset outright.
* Depreate use of `Bureau`

### Proposal #3 

* Start with the OMB list, fail over to OPM when necessary, and then rarely fail over to what agencies have crowdsourced already by way of the .gov registry information.  






### Edge Cases and Questions
- What should a department put in its bureau field for an entry that has a suborganization that is not in one of its listed bureaus.
- Should we encourage non-department agencies to populate the bureau field with n/a?







Steps to Combine datasets 
- Lowercase Of, The, And, For




