
This document is to memorialize internal project procedures.  Other agencies or teams not at GSA are free to adopt them as well, but don't have to in order to use the software.  


### GitHub Tokens!!!

This guide outlines the steps to generate a GitHub personal access token (PAT) with permissions to create issues in repositories.  This isn't needed for most of the github actions we use though.  

### Step-by-Step Instructions

1. **Sign in to GitHub**
   - Go to [https://github.com/login](https://github.com/login) and sign in to your account.

2. **Navigate to Developer Settings**
   - In the top-right corner of any page, click your profile photo, then click **Settings**.
   - In the left sidebar, click **Developer settings**.

3. **Create a Personal Access Token**
   - Click **Personal access tokens** > **Tokens (classic)**
   - Click **Generate new token**.

4. **Configure Token Settings**
   - **Name** your token (e.g., `smoke-test-token`).
   - Set an **expiration date** (recommended).
   - Select **repo** scope if using classic tokens:
     - Check the `repo` checkbox to include all repository permissions.
   - Ensure **`repo:issues`** permission is included to allow issue creation.

5. **Generate and Save the Token**
   - Click **Generate token** at the bottom of the form.
   - **Copy** the token immediately and store it securely. You won't be able to see it again.

6. **Update GitHub Actions Secret**
   - Navigate to the `site-scanning-analysis` repository.
   - Click on **Settings** > **Secrets and variables** > **Actions**.
   - Find the secret named `ISSUE_TOKEN`. Click the pencil icon to **edit** it.
   - **Paste** the new token in the value field and click **Update secret**.


### GitHub Access 


##### Site Scanning 

The System owner and current project developers need commit rights to Site Scanning project repositories ([here](https://github.com/GSA/site-scanning-engine) and [here](https://github.com/18F/site-scanning-query-builder).  The system owner (currently Gray Brooks) manages this access, granting access to new project developers when they come onboard and removing access when they leave.  

Specifically, current developers are managed as the `FAS - TTS - Solutions - Site Scanning` team in the GSA GitHub organization.   

Both of the adding and removing processes should be initiated by creating an issue in the project's [issue tracker](https://github.com/GSA/site-scanning/issues).  Any one can create the issue, but the system owner should be the one who addresses and closes it. They directly track the presence and departure of staff, but also receive a monthly separation report to ensure that departing staff are tracked and addressed.  


These accounts are created for developers that need access to contribute code and deploy apps.

1. [Create an account](https://github.com/) with GitHub and [enable multi factor authentication](https://github.com/blog/1614-two-factor-authentication).
2. Make sure you have [gitseekrets](https://github.com/18F/laptop/tree/master/seekret-rules) installed on your Mac or in your virtualbox, if that is where you do your development. (If you are a Windows only user, you can be exempt from this requirement while the windows version is in development.) 
3. Then, you will want to contact the system owner, currently Gray Brooks. In that message, include your name, the name of your supervisor, confirm you have two-factor authentication on and have installed gitseekrets. 
4. The system owner will confirm the GSA identity of the applicant, and signal approval in the ticket. 
5. The system owner will then add the GitHub handle for the new member to the `FAS - TTS - Solutions - Site Scanning` GitHub team in the GSA organization and close the ticket.
 
### Cloud.gov Access 

The System owner and current project developers need cloud.gov access to Site Scanning.  The system owner (currently Gray Brooks) manages this access, granting access to new project developers when they come onboard and removing access when they leave.  They directly track the presence and departure of staff, but also receive a monthly separation report to ensure that departing staff are tracked and addressed.  

Specifically, current developers are [granted](https://cloud.gov/docs/apps/managing-teammates/) OrgManager rights to `gsatts-sitescan`.  

Both of the adding and removing processes should be initiated by creating an issue in the project's [issue tracker](https://github.com/GSA/site-scanning/issues).  Any one can create the issue, but the system owner should be the one who addresses and closes it.    

These accounts are created for developers that need access to contribute code and debug apps.

1. Create an issue in the project's [issue tracker](https://github.com/GSA/site-scanning/issues) to track the request.  

1. [Create an account](https://cloud.gov/docs/getting-started/accounts/) with cloud.gov and this will include multi factor authentication with [Google authenticator](https://support.google.com/accounts/answer/1066447?hl=en) or [authy](https://www.authy.com/).

4. The system owner will confirm the GSA identity of the applicant and comment on the ticket to show approval. 

5. The system owner will add a person to the Site Scanning organization in cloud.gov. 
 
6. The system owner will document the permissions that were assigned in the issue and close the issue when completed.  



### Public API Users 

Pulic API users may self-provision API keys using the sign up form on the [API documentation for the Site Scanning API](https://open.gsa.gov/api/site-scanning-api/).  These keys then allow them general, public access to the API.  

These keys are then used to identify the developer when making API calls, but do not provide any site authentication.  There is no login or admin experience by which a public API user interacts with or manages their API key(s).  


### Weekly Monitoring Checklist

The development team checks for security events weekly. Any unusual or suspicious activities are immediately brought to the team's attention in the project slack channel (#site-scanning) and the system owner coordinates appropriate investigation and followup. The team will follow the [TTS incident response handbook](https://handbook.tts.gsa.gov/security-incidents/).

Checklist:
1. Create an issue in the project's [issue tracker](https://github.com/GSA/site-scanning/issues) to track this Security Event Review.
2. Review tool for all repositories and open a ticket for all "red" alerts.
3. Review [production logs](https://logs.fr.cloud.gov) for unapproved and unusual activities. 
4. Review actionable security events on production logs for successful and unsuccessful account logon events, account management events, object access, policy change, privilege functions, process tracking, system events, all administrator activity, authentication checks, authorization checks, data deletions, data access, data changes, and permission changes.
5. Deactivate any cloud.gov and github access for people who have left the team.
6. Note any findings in the Security Event Review issue.
7. Close the Security Event Review issue.

### Monitoring of New Relic Alerts

New Relic alerts are emailed to the full team immediately.  The first team member to see the alert checks the site's status and posts in the project slack channel (#site-scanning) the results.  The system owner then coordinates any necessary followup.  

### Analysis of Security Impacts

Every change is assessed for potential impact on security posture as part of the change request submission, and is code reviewed by GitHub Actions. Changes with a potential impact on security include a review of standards and guidelines as part of requirements development. After a deployment, security posture is reviewed and confirmed via the GSA SecOps scanning suite during regular scanning.   Dependabot is used across TTS Github repos to automatically scan for vulnerabilities and dependency versioning. If an update is identified as needed, the team reviews documentation and takes necessary action.
