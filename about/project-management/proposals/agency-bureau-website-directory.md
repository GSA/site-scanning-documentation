

### Problem

There's an unmet need for a reliable, canonical, comprehensive directory of federal websites that notes which agency, bureau, and potentially office operates them.  

### Details 

The [Site Scanning program](https://digital.gov/site-scanning), through its [Federal Website Index](https://github.com/GSA/federal-website-index), provides an aspect of this by maintaining the most reliable, comprehensive directory of federal websites (i.e. subdomains).  It uses the .gov registry's canonical [List of  Federal .gov Domains](https://github.com/cisagov/dotgov-data/blob/main/current-federal.csv) to then apply an agency and bureau owner to each website, but this is an imperfect solution, since different bureaus within an agency may operate different websites on the same domain.  

As part of the implementation of [OMB-23-22](https://www.whitehouse.gov/wp-content/uploads/2023/09/M-23-22-Delivering-a-Digital-First-Public-Experience.pdf), agencies generated a one-off correction of Site Scanning data that improved the agency and bureau information for 9,000 websites.  Importantly, the memorandum has a requirement that agencies keep this information up to date going forward (See section IV, C, 1 at the bottom of page 31).  

Numerous agencies and stakeholders have a current and perpetual need for this information, a need that remains partially unmet.  In addition to OMB needing it for 21st Century IDEA implementation, the National Archives needs it for its end-of-term website snapshots; CISA needs it for its https scanning reports; the Government Publishing Office need it for the U.S. Government Manual; USA.gov needs it for its directory; the Site Scanning program needs it to better maintain its website index; and more. It would also be a perpetually useful resource for individual agencies and the public at large.  

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

What would be needed is simply to:
- Decide on an initial schema
- Populate the file with existing, confirmed information
- Direct agencies to update the file on a regular basis

Permissions for the repository could be expanded to grant 1-2 representatives per agency to have direct edit access and then everyone else could be directed to submit further edits with pull requests.  

Such a single, centralized file could be CSV (for easy downloading into spreadsheets) or YML (for easy reading).  See [here](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/prototypes/federal_websites.csv) and [here](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/prototypes/federal-websites.yml) for examples of what the files could look like.  

A file such as this would be very large, but would still be very manageable by those without software and technical skills.  By having basic norms such as keeping the file alphabetized by agency, then bureau, then website would make the file more usable as well.  

3) Create a decentralized, standardized file

A similar but different approach would be to expand on existing OMB practice by setting a location such as agency.gov/websites.yml or agency.gov/websites.csv to serve as the canonical source for this information in the future.  This follows the success of numerous information collections that agencies are already familiar with and have in place, such as the Open Data Policy (agency.gov/data.json), Open Source Policy (agency.gov/code.json), Digital Government Strategy (agency.gov/digitalstrategy.json), and FITARA (agenct.gov/digitalstrategy/FITARAmilestones.json, etc.).  

Such as file could look like [this](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/prototypes/agency_websites.csv) or [this](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/prototypes/agency_websites.yml).  They could then be crawled, harvested, and combined on a regular occastion.  

One advantage of this model is that it makes agency adoption and responsible upkeep of their list much more visible and directly attritable.   

4) Create a norm around metadata

Agencies should already be applying certain metadata tags to their webpages.  Some, like page title, are considered basic best practices.  Others are useful and desirable but have lower adoption in society (e.g. 'subject' or 'author').  

One possible solution to have reliable agency and bureau ownership information for websites is to promulgate a standard for metadata tags that would serve it.  

For instance, if the 'owner' tag was used in a consistent structure such as `Agency - Bureau`.  A third level could be optional along the lines of `Agency - Bureau - Office`.  So, a website might have a metatag like this: `<meta name='owner' content='Department of Agriculture - Economic Research Service'>`

Or, the keywords tag could be used in such a creative manner like this:  `<meta name='keywords' content='agency:Deparment_of_Agriculture, bureau:Economic_Research_Service'>`

Note [this list](https://gist.github.com/whitingx/3840905) of other common tags as well as [the results of a March 2024 analysis](https://github.com/GSA/site-scanning/issues/869#issuecomment-2009879132) to see which metatags are already used by agencies and how widely they've been adopted.  For instance, only 0.17% of federal websites currently use the owner tag and 11.45% use the keyword tag.  

