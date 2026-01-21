### Digital Analytics Program (DAP) Scan
The [DAP scan](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/scans/dap.ts) checks if a website reports its statistics to the federal Data Analytics Program, which collects data from government sites. It also provides additional details like script settings and Google Analytics IDs.

#### What We Report:
- `dapDetected`: Tells if the DAP script or a specific Google Analytics property was found.
- `dapParameters`: Lists the settings used in the DAP script.
- `dapVersion`: Shows the version of the DAP script, if detected.
- `gaTagIds`: Lists all Google Analytics tags found in the site's outgoing requests.

#### How We Check:
- **Build GA Tag List:**
    - Look at all outgoing requests to find Google Analytics tags. We check URLs and any data sent through forms, then list the tags we find.
- **Find DAP Script Candidates:**
    - Search through outgoing requests to see if we can find the DAP script or a specific Google Analytics ID. Save potential matches for closer inspection.
- **Analyze Candidates:**
    - Examine the potential matches to get detailed information and find the best one.
- **Choose the Best Match:**
    - Check each candidate to see which one best fits the criteria, starting with the most specific and moving to broader checks.
- **Report Results:**
    - Once the analysis is complete, we provide the final results.