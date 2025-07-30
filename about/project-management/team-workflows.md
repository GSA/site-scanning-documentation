
## Updating the digital.gov pages

* Log in [here](https://cms.digital.gov/user/login), and then go [here](https://cms.digital.gov/guides/site-scanning/technical-details#content-start).  Edit in the top right corner under local tasks.  

## Updating the api docs

* File a pull request to [this repo](https://github.com/GSA/open-gsa-redesign/blob/master/_apidocs/site-scanning-api.md).  A preview can be seen at `https://federalist-64fd1e70-2b76-44eb-96ef-4bc40b4b3bac.app.cloud.gov/preview/18f/site-scanning-query-builder/NAME-OF-BRANCH/`.  When the pull request is ready, comment on it to that effect and email api.ciss@gsa.gov with a link to the PR to ask them to merge.

## Refresh everything in the system

Below is the order in which to [trigger actions](https://github.com/GSA/site-scanning-documentation/blob/main/pages/schedule.md) so as to rebuild everything.  Unless otherwise specified, wait 5 minutes in between each action.  

* Build federal website index
* Ingest federal website index
* Fetch security data
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

## Check New Relic
- Go [here](https://one.newrelic.com/synthetics/monitor-overview/MjQ4NDc2N3xTWU5USHxNT05JVE9SfGViOTBjODUzLTFiYjktNDc5Yy04ZTEzLTk0YmM3NTUxMzFmOA?account=2484767&duration=1800000&state=a2c88aef-f325-027f-0460-5f92caba855e) and log on with single-sign on.  

## Template checklist for new fields
* Look for most recent issues [here](https://github.com/search?q=repo%3AGSA%2Fsite-scanning+checklist+for+new+fields&type=issues).

## Checklist for Notifying users about upcoming breaking changes
-  Note the contacts of identified stakeholders [here](https://docs.google.com/spreadsheets/d/14fTk_ri-aVvJms-mxDcfvLEDKaESP2EIRxAKkqO0fCw/edit?gid=197836991#gid=197836991)
-  Look up email addresses from API users for the past 3 months
-  Note other known snapshot consumers (currently, just search.gov)
-  Message them with the time and nature of the upcoming changes
-  Add a banner to the API documentation

## Other miscellaneous system changes 
* Change when the weekly export takes place: [edit this line](https://github.com/GSA/site-scanning-engine/blob/5ae7b3a16d047c65796f5b73b69399f971aeb920/vars-prod.yml#L12)
* Reorder the CSV columns: [edit this file](https://github.com/GSA/site-scanning-engine/blob/main/libs/snapshot/src/snapshot.service.ts)
* [Deploy new code](https://github.com/GSA/site-scanning-engine/blob/main/docs/deployment.md)


