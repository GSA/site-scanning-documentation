This is a list of individual report pages that _could_ be built using Site Scanning data.  This is a brainstorming page and all ideas are welcome.  

The list of report pages that have alreadby been built and are active is [here](/presentation-layers#active).  Feel free to suggest further ideas by [editing this page](https://github.com/18F/site-scanning-documentation/edit/master/presentation-layers/candidate-report-pages.md), [filing an issue](https://github.com/18F/site-scanning/issues) or emailing us at site-scanning@gsa.gov.  




## For TTS Programs

### DAP team
* analytics.usa.gov/participation to offer some metrics and help demonstrate who hasn't implemented DAP that needs to.  

### USWDS

* Table with all of the individual scores broken out and sortable
* Mashup USWDS scores with Mobile Friendliness, Pagespeed Insights, Accessibility, etc. 

## TTS Digital Council 
* A USWDS dashboard for a list of websites maintained in a YML file like [this](https://github.com/GSA/machine-readable-TTS/blob/master/data/websites.yml) - [issue](https://github.com/18F/Spotlight/issues/650)
* A DAP dashboard for a list of websites maintained in a YML file like [this](https://github.com/GSA/machine-readable-TTS/blob/master/data/websites.yml) - [issue](https://github.com/18F/Spotlight/issues/649)


## For OMB

* 21st Century IDEA dashboard
* /digitalstrategy pages for CFO Act agencies, etc.
* List of /digitalstrategy pages that aren't for CFO Act agencies, etc.


## GSA Digital Council 
* A USWDS dashboard for a list of websites maintained in a YML file like [this](https://github.com/GSA/machine-readable-TTS/blob/master/data/websites.yml)
* A DAP dashboard for a list of websites maintained in a YML file like [this](https://github.com/GSA/machine-readable-TTS/blob/master/data/websites.yml) 

## General Agency Use

#### Basic Inventory 
* A page that lists the domains owned by an agency.  
* A page that lists the domains owned by an organization within an agency.  
* A page that lists the subdomains owned by an agency.  
* A page that lists the subdomains owned by an organization.  
* A page that lists the subdomains of a domain.  

#### Advanced Inventory 1

The envisioned mashup would be a table.  Optional functionality would include exporting as a CSV, filtering, sorting, and searching.  

* A page that lists the domains owned by an agency, whether they are live, whether they redirect, and if so, where they redirect to. ([Example](/presentation-layers/wireframes/agency-domains-advanced-inventory-1.md))
* A page that lists the domains owned by an organization within an agency, whether they are live, whether they redirect, and if so, where they redirect to.  
* A page that lists the subdomains owned by an agency, whether they are live, whether they redirect, and if so, where they redirect to.  
* A page that lists the subdomains owned by an organization, whether they are live, whether they redirect, and if so, where they redirect to.  
* A page that lists the subdomains of a domain, whether they are live, whether they redirect, and if so, where they redirect to.  

#### Advanced Inventory 2

The same as Advanced Inventory 1, with further columns appended with specified further metadata from another YML file ([example](https://github.com/GSA/machine-readable-TTS/blob/master/data/websites.yml)).  ([Example](/presentation-layers/wireframes/agency-domains-advanced-inventory-2.md))

#### Advanced Inventory 3 

By Agency, domain, status, DAP, pageload time, what else? 


#### DAP Participation 1

The envisioned mashup would be a table.  Optional functionality would include exporting as a CSV, filtering, sorting, and searching.  

* A page that lists the domains owned by an agency and whether they have DAP on them.   
* A page that lists the domains owned by an organization within an agency and whether they have DAP on them.  
* A page that takes X specific domains and indicates whether they have DAP on them.  
* A page that lists the subdomains owned by an agency and whether they have DAP on them.  
* A page that lists the subdomains owned by an organization and whether they have DAP on them.  
* A page that lists the subdomains of a domain and whether they have DAP on them.  
* A page that takes X specific subdomains and indicates whether they have DAP on them.  

#### DAP Participation 2

The same as DAP Particpation 2, with further columns appended with specified further metadata from another YML file ([example](https://github.com/GSA/machine-readable-TTS/blob/master/data/websites.yml)). 


#### USWDS Implementation 1

The envisioned mashup would be a table.  Optional functionality would include exporting as a CSV, filtering, sorting, and searching.  

* A page that lists the domains owned by an agency and what their USWDS analysis count is.   
* A page that lists the domains owned by an organization within an agency and what their USWDS analysis count is.  
* A page that takes X specific domains and what their USWDS analysis count is.  
* A page that lists the subdomains owned by an agency and what their USWDS analysis count is.  
* A page that lists the subdomains owned by an organization and what their USWDS analysis count is.  
* A page that lists the subdomains of a domain and what their USWDS analysis count is.  
* A page that takes X specific subdomains and what their USWDS analysis count is.  

#### USWDS Implementation 2

The same as USWDS Particpation 2, with further columns appended with specified further metadata from another YML file ([example](https://github.com/GSA/machine-readable-TTS/blob/master/data/websites.yml)). 

## Other

* Create a powerful data querying interface, a la kabana (more details [here](https://github.com/18F/Spotlight/issues/321))
* Create a lightweight browser extension that presented information about the website one was on.  ([issue](https://github.com/18F/Spotlight/issues/409))
* Create a powerful per-domain view, so that you can search or filter for a specific website and get all/many of the results from the different scans for that websites.  (more notes on this [here](https://github.com/18F/Spotlight/issues/448))
* Same as the above, but for a domain, all of the websites.  

