## Problem

Both for the [website directory project](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/proposals/agency-bureau-website-directory.md) as well as several other projects, there's a need to have a consistent, agreed upon list of federal agencies and bureaus that can be used as the reference dataset.  The need is mainly to bring about a consistent spelling, capitalization, and punctuation within a given project but also would help to promote consistency across projects.  

## Proposal 

Take various existing agency/bureau lists and compare them to see if any one of them would be the best suited for this purpose out of the box, or what modifications would be needed for it to serve this purpose.  

## Details 

To begin with, I'm assembling currently available resources.  Below are descriptions of them (though if anyone knows of others, let me know!!).  

- [OMB Circular A-11, Appendix C](https://www.whitehouse.gov/wp-content/uploads/2018/06/a11.pdf#page=849)
- [NARA list of agencies that are subject to the Federal Records Act](https://www.archives.gov/records-mgmt/appraisal/work-group-all.html)
  - [NARA list of agencies that are not subject to the Federal Records Act](https://www.archives.gov/records-mgmt/agency/non-fra)
-  [Agencies and organization Information in the .gov Registry](https://github.com/cisagov/dotgov-data/blob/main/current-federal.csv)
-  Modifications to the agency/organization information in Action #2 of agency implementation of OMB 23-22 (agency clarifications to .gov registry information as applied to subdomains)
-  [eCFR list of agencies](https://www.ecfr.gov/agencies)
-  [CISA list of Federal Civilian Executive Branch Agencies](https://www.cisa.gov/news-events/directives/federal-civilian-executive-branch-agencies-list)
-  [GSA MySales list of agencies and bureaus](https://mysales.fas.gsa.gov/htm/agencybureaucodes.htm)
-  [USASpending.gov list of agencies](https://www.usaspending.gov/agency)
-  [Lobbying Disclosure Act form list of agencies and bureaus](https://lda.congress.gov/ld/help/default.htm?turl=Documents%2FAppNames.htm)
-  [GAO list of agencies](https://www.gao.gov/agencies/all-agencies)
-  [Federal Register list of agencies](https://www.federalregister.gov/agencies)
-  [regulations.gov list of participating and non-participating agencies](https://www.regulations.gov/agencies)
-  [OPM list of federal agencies](https://www.opm.gov/about-us/open-government/Data/Apps/Agencies/)
-  [USA.gov list of agencies](https://www.usa.gov/agency-index)
-  [ACUS Sourcebook of US Executive Agencies Data](https://www.acus.gov/appendix/sourcebook-data)
-  [US Government Manual Org Chart/List of Boards, Commissions, and Committees/Agency Acronyms](https://www.usgovernmentmanual.gov/).


#### Substantial questions to work out....

- For each ABCDE agency, does it make sense to include a bureau ABCDE (the same name again) so that any entries that are at the agency level and not part of a subcomponent have the bureau field populated?  Or should it be empty?  Or something generic like `------` or `agency level`?



#### Notes
- ACUS report "[Mapping the Contours of the Federal Government](https://www.acus.gov/sites/default/files/documents/EXCERPT_ABA_Spring2013_final.pdf)"
- Link to combined data



## Observations 

- No one dataset is perfect.  I'm going to try and make notes on each.  
- Also, there should be an overlay with agency flagship sites.  



Analysis: 
- Agency Count
- Bureau Count
- Comprehensiveness
- Observations

General Recommendations:
- Do not include US, U.S., United States, of the United States, etc. in the name.
- Do not use a comma to reorder the name in order to promote alphabetization (e.g. `Acme, Offie of`)
- Spell out words like `and` instead of using symbols
- Do not abbreviate
- Do not include parenthetical additions

## Analysis of Options


|  Source | Type  | Notes | Advantages  |  Disadvantages | 
|  --- | ---  | --- | ---  |  --- | 
|  OMB  |  Primary |  |   |   | 
|   NARA | Curated  |  |   |   | 
|  OPM  |  Primary |  |   | Has extra characters that need removing; all caps;   | 
|  Federal Register  |  Primary |  |   |   | 
|  ECFR  | Curated  |  |   |   | 
|  Regulations.gov  | Curated  |  |   |   | 
|  US Government Manual | Curated  |  |   |   | 
|  USA.gov  |  Curated |  |   |   | 
|  USAspending.gov  | Curated  |  |   |   | 
|  Get.gov  |  Primary |  |   |   | 
|  M-23-22  |  Curated |  |   |   | 
|  MySales  | Primary   |  |   |   | 
|   LDA |  Primary |  |   | Abbreviates; has acronym;   | 
|  ACUS  |  Curated |  |   |   | 
| GAO   | Curated  |  |   |   | 
|   CISA | Curated  |  |   |   | 




OMB Circular A-11, Appendix C
NARA list of agencies that are subject to the Federal Records Act
NARA list of agencies that are not subject to the Federal Records Act
Agencies and organization Information in the .gov Registry
Modifications to the agency/organization information in Action #2 of agency implementation of OMB 23-22 (agency clarifications to .gov registry information as applied to subdomains)
eCFR list of agencies
CISA list of Federal Civilian Executive Branch Agencies
GSA MySales list of agencies and bureaus
USASpending.gov list of agencies
Lobbying Disclosure Act form list of agencies and bureaus
GAO list of agencies
Federal Register list of agencies
regulations.gov list of participating and non-participating agencies
OPM list of federal agencies
USA.gov list of agencies
ACUS Sourcebook of US Executive Agencies Data
US Government Manual Org Chart/List of Boards, Commissions, and Committees/Agency Acronyms.







