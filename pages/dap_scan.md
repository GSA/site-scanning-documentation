### Digital Analytics Program (DAP) Scan
The [DAP scan](https://github.com/GSA/site-scanning-engine/blob/main/libs/core-scanner/src/scans/dap.ts) takes all outbound requests made from a page and analyzes them to determine if a valid DAP script candidate can be identified. While analyzing these requests we also collect some additional information such as `dap_parameters`, `dap_version`, and `ga_tag_ids`.

#### Values Returned:
- `dapDetected`: A true/false value that denotes whether a valid DAP script candidate could be located within the outbound requests.
- `dapParameters`: All parameters being passed to the DAP script.
- `dapVersion`: If a DAP script version can be identified it will be populated here.
- `gaTagIds`: A comma delimited list of all GA tags found in the outbound requests.

#### Scan Steps:
- **Build GA Tag List:**
    - All outbound requests are checked for the presence of Universal (UA) and G4 tags. We check the URL and also any POST request values. We then return a comma delimited list of tags found.
- **Identify DAP Script Candidates:**
    - We iterate through the list of outbound requests and try to determine if a DAP script can be identified. We look for the presence of the `Universal-Federated-Analytics-Min.js` script file as well as the presence of the `G-CSLL4ZEK4L` property ID.
    - When looking through the requests we check the URLS and POST data for any reference to the script or the GA tag. If either the script or tag are found we save these as a potential candidate and return this list of candidates for further analysis.
- **Further Analyze Candidates:**
    - Now that we have narrowed down the outbound requests to only those that are potential DAP script candidates we can further analyze the requests and pull out the data we need to narrow down our list to one `Best` candidate.
    - During this analysis we collect the `request body`, `url`, `url parameters`, `postData`, and `dap version`. These values will be used in the next step to determine the best candidate.
- **Determine Best Candidate:**
    - All of the candidates are run through a list of checks to determine which one meets the requirements to be a `best` candidate. The checks become less strict as we go.
    - Checks:
        1. Does the candidate contain the `Universal-Federated-Analytics-Min.js` script and also have a version number?
        2. Does the candidate contain the `G-CSLL4ZEK4L` property ID and a version number?
        3. Does the candidate have a version number?
        4. Does the candidate contain the `Universal-Federated-Analytics-Min.js` script, but NO version number?
        5. Does the candidate contain any of the items above individually (version OR script OR GA tag)?
    - Going through these checks in order we determine which candidate is our `best` match. Check 1 being the best match and 5 being the final match check.
- **Return our results:**
    - Once all of the above steps are complete we return the results.