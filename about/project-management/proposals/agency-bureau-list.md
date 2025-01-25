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
- What should we think of as bureaus - I think the closest thing to a consensus is that bureaus are only within Departments and are lined drawn by some different rubrics.  



#### Notes
- ACUS report "[Mapping the Contours of the Federal Government](https://www.acus.gov/sites/default/files/documents/EXCERPT_ABA_Spring2013_final.pdf)"
- Link to combined data



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

## Analysis of Options

- OMB is the leading candidate.
  - It's list of agencies is very good, though it uses the following in the agency slot in ways that are problematic:  District of Columbia, International Assistance Programs, Judicial Branch, Legislative Branch, and Other Defense Civil Programs.  Also, oddly, it gives bureaus to FDIC and GSA similarly to how it does departments but not other agencies.  Reasonable solutions to these would be to remove the DC fields; remove the FDIC and GSA bureaus, and promote from bureau to agency the entries under International Assistance Programs, Judicial Branch, Legislative Branch, and Other Defense Civil Programs.  
  - Departments have bureaus in a way that usually looks good.  The exceptions to this though are Defense and Energy, which skimp in a way that is doesn't fit as well.
- NARA is a strong competitor.
  - It's generally very good and handles Departments very well, including Defense and Energy. The following hold Agency slots and the entitites therein would be best promoted from the Bureau to Agency fields: Boards Commissions and Committees, Independant Agencies, Judicial Branch, Legislative Branch, Legislative Commission, and Wholly-owned Government Corporation.
  - There's a small number of obscure agencies that aren't included, but that's okay.
  - In a few cases, they add some extras (like United States or U.S.) but not too often or really more than any other dataset.
- OPM is the third main competitor.
  - Includes a nice extra layer by describing independent agencies as large, medium, or small and also staff sizes.
  - Includes many more bureaus within departments than other sources do.
  - Promotes Army, Navy, and Air Force to their own Departments with Bureaus.
  - Assigns Bureaus to many agencies in a way that the other datasets do not.
  - Includes abbreviations in the name fields.
  - Adds some extras (like United States or U.S.).
  - In a number of cases, severely abbreviates the agency name instead of listing it out.  



|  Source | Type  | Notes | Advantages  |  Disadvantages | 
|  --- | ---  | --- | ---  |  --- | 
|  OMB  |  Primary |  |   |   | 
|   NARA | Curated  |  |   |   | 
|  OPM  |  Primary |  |   | Has extra characters that need removing; all caps;   | 
|  Federal Register  |  Primary |  |   |   | 
|  ECFR  | Curated  |  |   |   | 
|  Regulations.gov  | Curated  |  |   |   | 
|  US Government Manual | Curated  |  |   |   | 
|  USA.gov  |  Curated | High quality, good curation, but doesn't distinguish between agencies and bureaus  |   |   | 
|  USAspending.gov  | Curated  |  |   |   | 
|  Get.gov  |  Primary | Useful for other purposes but includes substantailly more subcomponents beyond agencies and bureaus |   |   | 
|  M-23-22  |  Curated | Useful for other purposes but includes substantailly more subcomponents beyond agencies and bureaus; not comprehensive |   |   | 
|  MySales  | Primary   | Includes many subcomponents beyond agencies and bureaus |   |   | 
|   LDA |  Primary |  |   | Abbreviates; has acronym;   | 
|  ACUS  |  Curated |  |   |   | 
| GAO   | Curated  | Informal, offers several names sometimes, and doesn't distinguish agencies and bureaus |   |   | 
|   CISA | Curated  | Informal, not fully comprehensive and doesn't distinguish agencies and bureaus |   |   | 












