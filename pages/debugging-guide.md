The following is a step by step means to looking for where bad data might come into the process and be incorporated in the final site scanning data files.  



Analysis 
* Review [the original datasets themselves](https://github.com/GSA/federal-website-index/blob/main/builder/config.py) that are combined in order to generate the target URL list.  One can look at the original source files or at [snapshots of them](https://github.com/GSA/federal-website-index/tree/main/data/snapshots) which were generated the last time that the target URL list was updated, in case the source files have changed in the interim.  
* Think through the [formal order and logic](https://github.com/GSA/federal-website-index/blob/main/builder/main.py) which which the original datasets are then combined, dedupped, and trimmed in order to form the target URL list.  
  * Then, look at [the snapshot files](https://github.com/GSA/federal-website-index/tree/main/data/snapshots) which were generated at each step during the last build in order to look for the introduction of errors.  




Rebuilding
