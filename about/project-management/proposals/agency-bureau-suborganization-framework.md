
### Conclusion

* [Crossmatch of OMB A-11/OPM Fedscope/CISA .gov registry agency/bureau names](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/datasets/Agency-Bureau_Lists-OMB-OPM-dotgov_crossmatch-2025.csv)
* 

-------------------

### Problem

How to line draw between `agency`, `bureau`, `office`, and `suborganization`.  

### Current State

* .gov Registry - Utilizes two levels, `organization` and `suborganization`.  "We define a suborganization as any entity (agency, bureau, office) that falls under the overarching organization."
* OMB -
* Site Scanning -
* OPM - Agency, Sub-Agency - 


### Proposal #1

* Agency should only be populated with a value from the `agency` column in X table.
* Only the 15 executive departments should populate the `bureau` column, and they should do so only with a value from the `bureau` values associated with their department in X table.  
* `Suborganization` should be used for any entity below an agency or agency/bureau.
* Deprecate the use of `office` in this effort as it is informal and less versitile/partially in conflict with `suborganization`.


The above guidelines serve to align these inventories with currently used OMB agency and bureau codes and will enable much better interoperability across numerous programs.  


### Proposal #2

* Adopt the OPM dataset outright.
* Depreate use of `Bureau`




### Edge Cases and Questions
- What should a department put in its bureau field for an entry that has a suborganization that is not in one of its listed bureaus.
- Should we encourage non-department agencies to populate the bureau field with n/a?


