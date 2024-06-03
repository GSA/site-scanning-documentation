

### Problem

There's an unmet need for a reliable, canonical, comprehensive directory of federal websites that notes which agency, bureau, and potentially office operates them.  

### Details 

The [Site Scanning program](https://digital.gov/site-scanning), through its [Federal Website Index](https://github.com/GSA/federal-website-index), provides the most an aspect of this by maintaining the most reliable, comprehensive directory of federal websites (i.e. subdomains) .  It uses the .gov registry's canonical [List of  Federal .gov Domains](https://github.com/cisagov/dotgov-data/blob/main/current-federal.csv) to then apply an agency and bureau owner to each website, but this is an imperfect solution, since different burueas within an agency may operate different websites on the same domain.  

Notably, as part of the implementation of [OMB-23-22](https://www.whitehouse.gov/wp-content/uploads/2023/09/M-23-22-Delivering-a-Digital-First-Public-Experience.pdf), agencies generated a one off correction of Site Scanning data that improved the agency and bureau information for 9,000 websites.  Importantly, the memorandum has a requirement that agencies keep this information up to date going forward (See section IV, C, 1 at the bottom of page 31).  

Numerous agencies and stakeholders have a current and perpetual need for this information, a need that remains partially unmet.  In addition to OMB needing it for 21st Century IDEA implementation, the National Archives needs it for its end-of-term website snapshots; the Office of the Federal Register, National Archives, and Government Publishing Office need it for the U.S. Government Manual; USA.gov needs it for its directory; the Site Scanning program needs it to better maintain its website index; and more. It would also be a perpetually useful resource for individual agencies and the public at large.  

**Ideally, the solution employed to meet the upcoming requirement mentioned above can serve everyone's need once and for all.**  

Suggested elements of the directory include: 
- Comprehensive of the Federal government
- Includes all three branches
- Includes the .gov and .mil domains
- Includes non .gov and .mil domain sites (e.g. .com, .org, .edu)
- Employes an agreed upon list of agencies and bureaus both for spelling and consistency
- Includes the ability to describe a third level ownership below the bureau, such as an office or program
- Includes a public/non-public field
- Either initially stored in one known place, or consumed to be available in one known place (e.g. by the Site Scanning program)


### Options 

1) Touchpoints

The [Touchpoints shared service](https://touchpoints.app.cloud.gov/index) is a well-established, ideal solution.  It is freely available to federal agencies, has already been used by hundreds of government users at scores of agencies, is readily customizable, and was already employed at scale for a fabulously similar need, the [U.S. Digital Registry](https://digital.gov/services/u-s-digital-registry/).  The General Services Administration successfully uses Touchpoints for its internal website inventory.  

Modifying Touchpoints to become a complete solution for a cross-government website need would be easy, scalable, and agency-friendly.  

One key feature that would need to be developed would be for the resulting directory to be publicly available as a bulk file.  Right now, Touchpoints data is available via an API, but there's important use cases that would benefit from the complete directory also being downloadable and accessible at a fixed location as a bulk, flat file.  However, this is not a difficult feature to add.  

2) One centralized, agreed-upon file

It would be trivially easy to create and operate the entire index in one location in GitHub.  Either GSA or CISA would be suitable owners and the existing  or https://github.com/cisagov/dotgov-data/ repositories would already be good fits - there's not necessarily a need to look further than one of those places.  

What would be needed is 




Create a central DNS solution 

Touchpoints 

metadata (which)

Centralized file 


Decentralized file 



### Proposal 
