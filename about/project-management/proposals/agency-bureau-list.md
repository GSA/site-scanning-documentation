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


#### Notes
- ACUS report "[Mapping the Contours of the Federal Government](https://www.acus.gov/sites/default/files/documents/EXCERPT_ABA_Spring2013_final.pdf)"
- [Link to worksheet with combined and processed data (work in progress)](https://github.com/GSA/site-scanning-documentation/raw/refs/heads/main/about/project-management/datasets/Agency_Bureau%20Lists%20-%20Working%20Notes.xlsx)

## Analysis of Options

- OMB is the leading candidate.
  - It's list of agencies is very good, though it uses the following in the agency slot in ways that are problematic:  District of Columbia, International Assistance Programs, Judicial Branch, Legislative Branch, Other Commissions and Boards, and Other Defense Civil Programs.  Also, oddly, it gives bureaus to FDIC and GSA similarly to how it does departments but not other agencies.  Reasonable solutions to these would be to remove the DC fields; remove the FDIC and GSA bureaus, and promote from bureau to agency the entries under International Assistance Programs, Judicial Branch, Legislative Branch, and Other Defense Civil Programs.  
  - Departments have bureaus in a way that usually looks good.  The exceptions to this though are Defense and Energy, which skimp in a way that is doesn't fit as well.
  - The bureau breakdown for the Department of Defense will be unintuitive to most.  I would instead promote the 4 that they list as alternatives.  
- NARA is a strong competitor.
  - It's generally very good and handles Departments very well, including Defense and Energy. The following hold Agency slots and the entitites therein would be best promoted from the Bureau to Agency fields: Boards Commissions and Committees, Independant Agencies, Judicial Branch, Legislative Branch, Legislative Commission, and Wholly-owned Government Corporation.
  - There's a small number of obscure agencies that aren't included, but that's okay.
  - Includes territorial governments when other datasets don't but they could be easily excluded.  
  - In a few cases, they add some extras (like United States or U.S.) but not too often or really more than any other dataset.
- OPM is the third main competitor.
  - Includes a nice extra layer by describing independent agencies as large, medium, or small and also staff sizes.
  - Includes many more bureaus within departments than other sources do.
  - Promotes Army, Navy, and Air Force to their own Departments with Bureaus.
  - Assigns Bureaus to many agencies in a way that the other datasets do not.
  - Includes abbreviations in the name fields.
  - Adds some extras (like United States or U.S.).
  - In a number of cases, severely abbreviates the agency name instead of listing it out.  



|  Source | Type  | Counts | Advantages  |  Disadvantages | 
|  --- | ---  | --- | ---  |  --- | 
|  OMB  |  Primary | 143 Agencies, 253 Bureaus; With proposed change: 189, 191 | Authoritative, good use of exact names  |  Some entities in agency field not agencies; overly descriptive of 2 agences; under descriptive of 2 agencies | 
|   NARA | Curated  | 51, 278; With proposed change: 173, 156 |  Very intuitive |  Some entities in agency field not agencies; missing a few very small entities; includes territorial governments; adds informal content to some names | 
|  OPM  |  Primary | 120, 526 | Authoritative; More expansive; available as a static file/API  | Has extra characters that need removing; all caps; sometimes abbreviates names | 
|  Federal Register  |  Primary | 233, 203 | Authoritative  |   | 
|  ECFR  | Curated  | 153, 163 |   | Limited in Scope  | 
|  Regulations.gov  | Curated  | 326 |   |  Some duplication; doesn't distinguish between agencies and bureaus | 
|  US Government Manual | Curated  | 95 |  Straightforward; available as a static file | Limited in scope, doesn't distinguish between agencies and bureaus  | 
|  USA.gov  |  Curated | 607 |  High quality, good curation | Doesn't distinguish between agencies and bureaus; is perhaps overly inclusive  | 
|  USAspending.gov  | 108 Curated  |  |   |   | 
|  Get.gov  |  Primary | 148, 578  | Agency-provided  |  Useful for other purposes but includes substantailly more subcomponents beyond agencies and bureau; contains duplicates  | 
|  M-23-22  |  Curated | 67, 412  |  Agency-provided |  Useful for other purposes but includes substantailly more subcomponents beyond agencies and bureaus; not comprehensive | 
|  MySales  | Primary   | 1179 |  Super comprehensive | Includes many subcomponents beyond agencies and bureaus   | 
|   LDA |  Primary | 248 |   | Abbreviates; has acronyms in name   | 
|  ACUS  |  Curated | 96, 184 | High quality, good curation  |  Missing a number of entities; unclear when last updated | 
| GAO   | Curated  | 72  |  Offers alternate names | Informal, limited scope; offers several names sometimes, and doesn't distinguish agencies and bureaus  | 
|   CISA | Curated  | 102  | Straightforward  |  Informal, not fully comprehensive and doesn't distinguish agencies and bureaus | 


## Practical Scenarios


1. Convert the OMB dataset into a CSV and maintain and use it as is.
2. Convert the OMB dataaset into a CSV, make and document discrete improvements, and use it.
3. Request NARA to host source file, or manually convert it into a CSV and use it as it is.
4. Convert the NARA dataset into a CSV, make and document discrete improvements, and use it.
5. Use the OPM file directly
6. Take the OPM file, make and document discrete improvements, and use it.  



**_Ongoing notes below_:**


#### Substantial questions to work out....

- For each ABCDE agency, does it make sense to include a bureau ABCDE (the same name again) so that any entries that are at the agency level and not part of a subcomponent have the bureau field populated?  Or should it be empty?  Or something generic like `------` or `agency level`?
- What should we think of as bureaus - I think the closest thing to a consensus is that bureaus are only within Departments and are lined drawn by some different rubrics.  

## Observations 

- No one dataset is perfect.  I'm going to try and make notes on each.  
- Also, there should be an overlay with agency flagship sites.
- Outside of departments, less, but inside departments, offices are bureaus too.  everything formal tends to agree, except nara.  in that way, nara is better, right?  this is less the case with commerce though.  
  - omb works for ag, commerce, ed, hhs, 
  - ?? defense, energy,
  - omb includes some ?bureaus? that aren't, e.g. allowances.  

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








