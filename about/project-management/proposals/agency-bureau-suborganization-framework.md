
### Conclusion

Proposal #3 below works best.  

* [Final combined file](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/datasets/Agency-Suborganization-List-Combined.csv)
* [Crossmatch of OMB A-11/OPM Fedscope/CISA .gov registry agency/bureau names for comparison](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/datasets/Agency-Bureau_Lists-OMB-OPM-dotgov_crossmatch-2025.csv)

TL;DR Explanation: OMB maintains a consistent agency/bureau dataset as seen in A-11.  OPM maintains a consistent agency/sub-agency dataset as seen in Fedscope.  For our purposes, an agency value can only be from the OMB or the OPM list of 'Agencies'.  A suborganization value can only be from the OMB list of 'Bureaus' or the OPM list of 'Sub-Agencies'. 


Process for hybridizing the OMB and OPM datasets, starting from the crossmatch file above:
- Start with the OMB A-11 agency/bureau list.
- Remove any entries which are not entities.
- Pull in agencies and sub-agency entries that exist in the OPM Fedscope list but not the OMB list.
- In the rare case of agencies with few/no bureaus or sub-agencies (e.g. Energy, State), use the 'govsourced' list of suborganizations in the .gov registry.

Instructions for utilizing the [agency/suborganization list](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/datasets/Agency-Suborganization-List-Combined.csv), when populating a website inventory:  
- Only use values in Column B (Agency) for the `agency` field.
- Only use values in Column C (Suborganization) that correspond with your agency for the `suborganization` field.
- Any office or entity that exists below an established `suborganization` entry should go in the `suborganization2` field.
- If there is a desired suborganization that is not represented in the agency/suborganization list and is parallel with the other entries in that field, contact the Site Scanning team to request it be added to the list of first tier suborganizations.  






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

**Adopt OMB model outright**

* Agency should only be populated with a value from the `agency` column in the [OMB A-11 dataset](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/datasets/Agency-Bureau_Lists-OMB-OPM-dotgov_crossmatch-2025.csv).  
* Only the 15 executive departments should populate the `bureau` column, and they should do so only with a value from the `bureau` values associated with their department in the [OMB A-11 dataset](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/datasets/Agency-Bureau_Lists-OMB-OPM-dotgov_crossmatch-2025.csv).  
* `Suborganization` should be used for any entity below an agency or agency/bureau.



| Agency	 | Bureau, if you're a department	 | Suborganization |
| --- | --- | --- | 
| Dept. of A |  Bureau B | Office A  | 
| Dept. of A | | 	Office K |  
| Agency K |  | 	Office D |  

**Pros**: 
- Adheres closely to one dataset (A-11 Appendix C).

**Cons**:
- Lots of empty `bureau` fields.
- Aligns poorly with current or future .gov registry hierarchy.
- Excludes numerous agencies and sub-agencies that OPM dataset has.  



### Proposal #2

**Adopt OPM model outright**

* Agency should only be populated with a value from the `agency` column in the [OPM Fedscope dataset](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/datasets/Agency-Bureau_Lists-OMB-OPM-dotgov_crossmatch-2025.csv).
* Suborganization should only be populated by a value from the `sub-agency` column in the [OPM Fedscope dataset](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/datasets/Agency-Bureau_Lists-OMB-OPM-dotgov_crossmatch-2025.csv).

**Pros**: 
- Adheres closely to one dataset (OPM Fedscope). 

**Cons**:
- Excludes Legislative, Judicial Branches.
- Excludes numerous agencies and sub-agencies that OMB dataset has.  

### Proposal #3

**Adopt hybrid OMB/OPM model**

* Agency should only be populated with a value from the `agency` column in [this table](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/datasets/Agency-Suborganization-List-Combined.csv).
* Suborganization should only be populated with a value from the `suborganization` column in [this table](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/datasets/Agency-Suborganization-List-Combined.csv).
* Suborganization2 can be populated with anything below a suborganization listed in the `suborganization` column in X table.


| Agency	 | Suborganization | Suborganization2 |
| --- | --- | --- | 
| Dept. of A |  Bureau B | Office A  | 
| Dept. of A | Office K | 	 |  
| Agency K | Office D | 	 |  


**Pros**: 
- Aligns better with .gov registry hierachy.
- Lessens Bureau/Office confusion.
- Looks better and cleaner.

**Cons**:
- Doesn't closely align with either OMB or OPM dataset.  





### Edge Cases and Questions
- What should a department put in its bureau field for an entry that has a suborganization that is not in one of its listed bureaus.
- Should we encourage non-department agencies to populate the bureau field with n/a?







Steps to Combine datasets 
- Lowercase Of, The, And, For




