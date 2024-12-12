The first dozen fields in [Site Scanning data](https://github.com/GSA/site-scanning-documentation/blob/main/data/Site_Scanning_Data_Dictionary.csv) can be thought of as fundamentally trying to address what is being looked at.  Notably, they include these fields:  

| name	| description | example result |
| --- | --- | ---- | 
| Target URL	| URL scanned (Note that the `Target URL` and `Target URL - Base Website` are the same)| blog.usaid.gov  |
| Target URL - Base Domain	| Base Domain of the Target URL| usaid.gov   |
| Target URL - Top Level Domain| 	Top Level Domain of the Target URL|  .gov  |
| Final URL	| Final URL that resolves after any redirects [301, 302, etc.]|  https://www.usaid.gov/stories  |
| Final URL - Base Domain| 	Base Domain of the Final URL|  usaid.gov  |
| Final URL - Top Level Domain	| Top Level Domain of the Final URL| .gov  | 
| Final URL - Base Website	| Base Website of the Final URL|  www.usaid.gov  |

With these fields, we attempt to make clear what exactly is being analyzed, both from an initial loading perspective and what resolves in the end.  The Base Domain, Base Website, and Top Level Domain fields are derived from the Target URL and Final URL to facilitate sorting and analysis.  

A few issues that this model has are: 
- No one field works perfectly as an identifier for websites.  As part of [some related efforts](https://github.com/GSA/site-scanning-documentation/blob/main/about/project-management/proposals/dropping-www.md), the Site Scanning team is moving to adopt the following for this role: 'the hostname or fully qualified domain name, with `www.` removed'.
- The Target URL field is a bit misleading since it is actually not a URL but what is combined with `https://` to generate the target URL.
- There's an inbalance between the Target URL and Final URL fields, what with the Final URL having a Base Website.  
- `Target URL` and `Final URL` are used as adjectives for several dozen fields but they have proved a bit clunky and unintuitive to our end users.

We have been researching different taxonomies to address some of these issues.  The leading contender at the moment is this:


| name	| description | example result |
| --- | --- | ---- | 
| Target URL	| URL scanned | https://blog.usaid.gov  |
| Target Website	| Website of the Target URL | blog.usaid.gov  |
| Target Base Domain	| Base Domain of the Target URL | usaid.gov   |
| Target Top Level Domain | 	Top Level Domain of the Target URL |  .gov  |
| Final URL	| Final URL that resolves after any redirects [301, 302, etc.]|  https://www.usaid.gov/stories  |
| Final Website*	| Website of the Final URL, with `www.` removed if present |  usaid.gov  |
| Final Base Domain | 	Base Domain of the Final URL |  usaid.gov  |
| Final Top Level Domain	| Top Level Domain of the Final URL | .gov  | 


We believe that this model has some advantages: 
- The Final Website field could reliably serve as the website identifier within Site Scanning data.
- The consistent URL/Website/Base Domain/Top Level Domain structure provides greater symmetry between the Target and Final sets of fields.
- Target URL becomes more accurate and there is a pivot away from Target URL and Final URL as adjectives and towards Target and Final.
- One downside is the awkward but necessary caveating of Final Website to indicate that it is the resulting hostname _sans `www.`_.  Note that Target Website does not have a similar caveat because we are moving towards a Federal Website Index/Target URL list that strips all `www.` from the start anyway.


A third model we've recently considered is this: 


| name	| description | example result |
| --- | --- | ---- | 
| Site ID	| The hostname of the Scanned URL, with `www.` removed if present  | usaid.gov | 
| Initial URL | The URL that is initially loaded | https://blog.usaid.gov  |
| Initial Base Domain	| Base Domain of the Initial URL | usaid.gov   |
| Initial Top Level Domain | 	Top Level Domain of the Initial URL |  .gov  |
| Scanned URL	| The final URL that resolves after any redirects, which is then scanned |  https://www.usaid.gov/stories  |
|  Base Domain | 	Base Domain of the Scanned URL |  usaid.gov  |
|  Top Level Domain	| Top Level Domain of the Scanned URL | .gov  | 


A hybrid of the two could look like this:  

| name	| description | example result | example result 2 | 
| --- | --- | ---- |  ---- |
| Site Name	| The hostname of the Scanned URL, with `www.` removed if present  | usaid.gov |  18f.gsa.gov |
| Initial URL	| URL scanned | https://blog.usaid.gov  | https://18f.gov |
| Initial Domain	| Domain of the Initial URL | blog.usaid.gov  | 18f.gov |
| Initial Base Domain	| Base Domain of the Initial URL | usaid.gov   | 18f.gov |
| Initial Top Level Domain | 	Top Level Domain of the Initial URL |  .gov  | .gov |
| Scanned URL	| Final URL that resolves after any redirects, which is then scanned|  https://www.usaid.gov/stories  | https://18f.gsa.gov |
| Domain	| Domain of the Scanned URL |  www.usaid.gov  | 18f.gsa.gov |
| Base Domain | 	Base Domain of the Scanned URL |  usaid.gov  | gsa.gov |
| Top Level Domain	| Top Level Domain of the Scanned URL | .gov  |  .gov |



