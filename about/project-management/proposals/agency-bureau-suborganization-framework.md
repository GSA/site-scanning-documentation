### Problem

How to line draw between `agency`, `bureau`, `office`, and `suborganization`.  

### Current State

* .gov Registry -
* OMB -
* Site Scanning - 


### Proposal

* Agency should only be populated with a value from the Agency column in this table.
* Only the 15 executive departments should populate the Bureau column, and they should do so only with a value from the Bureau values associated with their department in this table.  
* `Suborganization` should be used for any entity below an agency or agency/bureau.
* Deprecate the use of `office` in this effort as it is informal and less versitile/partially in conflict with `suborganization`.

The above guidelines serve to align these inventories with currently used OMB agency and bureau codes and will enable much better interoperability across numerous programs.  


### Edge Cases and Questions
- What should a department put in its bureau field for an entry that has a suborganization that is not in one of its listed bureaus.
- Should we encourage non-department agencies to populate the bureau field with n/a?


