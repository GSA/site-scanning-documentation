
## Updating the digital.gov pages

* File a pull request to [this repo](https://github.com/GSA/digitalgov.gov/tree/main/content/guides/site-scanning).  A preview can be seen at `https://federalist-ecc58765-2903-48b3-920c-5d93318ad084.app.cloud.gov/preview/gsa/open-gsa-redesign/NAME-OF-BRANCH/api/site-scanning-api/`.  When the pull request is ready, comment on it to that effect and add Sara Cope as a reviewer.  They should get to it soon but if a while goes by (~a week), ask over in #digitalgov to make sure it's on their radar.  

## Updating the api docs

* File a pull request to [this repo](https://github.com/GSA/open-gsa-redesign/blob/master/_apidocs/site-scanning-api.md).  A preview can be seen at `https://federalist-64fd1e70-2b76-44eb-96ef-4bc40b4b3bac.app.cloud.gov/preview/18f/site-scanning-query-builder/NAME-OF-BRANCH/`.  When the pull request is ready, comment on it to that effect and email api.ciss@gsa.gov with a link to the PR to ask them to merge.

## Refresh everything in the system

Below is the order in which to [trigger actions](https://github.com/GSA/site-scanning-documentation/blob/main/pages/schedule.md) so as to rebuild everything.  Unless otherwise specified, wait 5 minutes in between each action.  

* Fetch security data
* Build federal website index
* Ingest federal website index
* Scan websites
* Wait 12 hours 
* Produce snapshots
* Produce accessibility details snapshot
* Analyze snapshots and target URL list
* Generate agency-specific snapshots
* Generate unique websites list


## Debug/analyze the ingest process
* Note: The ingest process itself is super fast, so there's not really a need to track it's progress to see if it's done.  
* To find where the ingest process broke, log into logs.fr.cloud.gov and go to [this page](https://logs.fr.cloud.gov/app/dashboards#/view/0a3c90f0-70ac-11ec-9ac9-d17def83cfd7?_g=(filters:!(),refreshInterval:(pause:!t,value:0),time:(from:'2022-06-28T00:29:00.000Z',to:'2022-06-29T00:29:30.000Z'))&_a=(description:'Experimenting%20with%20a%20dashboard%20for%20site%20scanner',filters:!(('$state':(store:appState),meta:(alias:!n,disabled:!f,index:'logs-app*',key:'@cf.app',negate:!f,params:(query:site-scanner-consumer),type:phrase),query:(match_phrase:('@cf.app':site-scanner-consumer)))),fullScreenMode:!f,options:(hidePanelTitles:!f,useMargins:!t),query:(language:kuery,query:''),timeRestore:!f,title:'Site%20Scanner%20Summary',viewMode:view)).  Each of the colors on those graphs is a worker. 

## Debug/analyze the scan process
* Log into logs.fr.cloud.gov and go to [this page](https://logs.fr.cloud.gov/app/dashboards#/view/0a3c90f0-70ac-11ec-9ac9-d17def83cfd7?_g=(filters:!(),refreshInterval:(pause:!t,value:0),time:(from:'2022-06-28T00:29:00.000Z',to:'2022-06-29T00:29:30.000Z'))&_a=(description:'Experimenting%20with%20a%20dashboard%20for%20site%20scanner',filters:!(('$state':(store:appState),meta:(alias:!n,disabled:!f,index:'logs-app*',key:'@cf.app',negate:!f,params:(query:site-scanner-consumer),type:phrase),query:(match_phrase:('@cf.app':site-scanner-consumer)))),fullScreenMode:!f,options:(hidePanelTitles:!f,useMargins:!t),query:(language:kuery,query:''),timeRestore:!f,title:'Site%20Scanner%20Summary',viewMode:view)). The scans finishing = a queue of zero.  
* In order to debug a specific URL's scan results, search the logs for that URL.

## Template checklist for new fields
* Look for most recent issues [here](https://github.com/search?q=repo%3AGSA%2Fsite-scanning+checklist+for+new+fields&type=issues).

## Checklist for Notifying users about upcoming breaking changes
-  Look up email addresses from API users for the past 3 months
-  Note known snapshot consumers (currently, just search.gov)
-  Message them with the time and nature of the upcoming changes
-  Add a banner to the API documentation

## Other miscellaneous system changes 
* Change when the weekly export takes place: [edit this line](https://github.com/GSA/site-scanning-engine/blob/5ae7b3a16d047c65796f5b73b69399f971aeb920/vars-prod.yml#L12)
* Reorder the CSV columns: [edit this file](https://github.com/GSA/site-scanning-engine/blob/main/libs/snapshot/src/snapshot.service.ts)
* [Deploy new code](https://github.com/GSA/site-scanning-engine/blob/main/docs/deployment.md)


