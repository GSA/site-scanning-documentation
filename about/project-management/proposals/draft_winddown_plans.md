
### Swift Version

On any given day, the Site Scanning team could turn off the Site Scanning program.  The system steps would include: 
- Deleting the system’s cloud.gov resources.
- Deleting or turning off the component GitHub actions.  

Financial steps would include: 
- Notifying the cloud.gov team of the need to end the MOU for the system.  
- Notifying the contracting officer of the need to end the Flexion engineering contract.  
- Notifying OCISO of the end of the need to maintain the system’s ATO.  

Appropriate stakeholder steps would include:
- Removing the relevant digital.gov pages, ideally redirecting them to github.com/gsa/site-scanning.  
- Updating the program’s github repositories with a notice about the program’s end. 
- Notifying known current data users of the program’s end.

Current data users to contact would include: 
- OMB - OFCIO
- GSA - Search.gov 
- GSA - Digital Analytics Program
- GSA - USWDS 
- GSA - Touchpoints **
- GSA - IT
- GSA - itdashboard.gov **
- GSA - digitaldashboard.gov **
- GSA - d2d.gsa.gov **
- NIST
- CISA
- NASA
- Digital Experience Council 
- Any 3rd party developer who has queried the API in the past three months

** indicates that the user has Site Scanning data integrated into a production system.

### Customer Centric Version

General Notes
- The Site Scanning system ATO is currently on track to go through July, 2025.  
- The system generally runs very reliably and would continue to do so.  
- Active development is almost entirely focused on iterating on current scans to further improve their accuracy and creating new scans that OMB, GSA, or other agencies have requested.  
- The critical features of the program would remain available, but the near term major impact would come from no longer supporting stakeholders and new agency users in understanding and navigating the data.  
- The API and bulk data sets would remain live and continue refreshing daily.

Communication Steps
- The three main areas of communication that would need to take place would be:
- Notifying the above current stakeholders of the end of customer support and the date at which the system will no longer be available.  
- Updating the current web presence to announce the planned date of deprecation.  
- Updating the system documentation to provide instructions on how an agency or individual user could stand up their own instance and migrate any applications that currently rely on the system over to a new instance.  

Financial Steps
- Coordinate a short term extension of the cloud.gov agreement (by 4/29/25)
- Coordinate the August 2025 wind-down of the cloud.gov agreement 
- Coordinate the wind-down of the engineering support contract (by 6/15/25)

Engineering Steps
- Delete the cloud.gov resources 
- Delete or turn off the component GitHub Actions 


In the near term, the main losses for stakeholders would be having to pay for and host their own instance, but more so the lack of subject matter expertise from the site scanning team, which they currently use quite frequently to understand and use the data.  

In the long term, GSA will mainly lose out by no longer having this data for their internal use and no longer ensuring that all agencies maintain comprehensive, real-time data on their websites.  
