

# Version 2.0 


Sept. 4, 2024 - [Here is a spreadsheet with the 1503 canonical link sites that have an identified issue](https://github.com/GSA/site-scanning-analysis/blob/main/reports/website-requests/sites-with-issues-9-4-24.csv). The highlighted issues are...

**Possible scan issue arising from META redirect**
The presence or use of a META redirect in the redirect chain is possibly causing the scan to timeout or fail.   

**Possible SSL issues**
Broken or missing SSL prevents the site from resolving properly.  

**Resolve to different Final URLs depending on if www. is included or not**
Site resolves to different locations depending on if 'www.' is included or not.  

**Site errors out** 
Site is breaking or not loading.  

**Site not present**
Site is breaking or not loading.  

**www. breaks**
Site breaks or will not load if it is prepended with `www.` 

**www. required**
The target URL breaks or will not load if 'www.' is not included.  Since all websites that are scanned for 21st Century IDEA are done so without 'www.', the scans will not resolve.  


==============================

# Version 1.0

## Department of Agriculture
* naldc.nal.usda.gov never finishes loading

## Department of Defense 
- www.army.nationalguard.mil has a strange media type (text/htmltext/html)
- scnewsltr.dodlive.mil has a strange media type (text/htmltext/html)

## Department of the Interior 
- ribd.recreation.gov. has a `lang` tag of `null` instead of `en`, that is oddly present when the DOM loads but not in the source code directly ([screenshot](https://github.com/GSA/site-scanning/issues/914#issuecomment-2061118800))

## FERC 
* https://ferconline.ferc.gov has a popup before page load

## GSA 
* apps.ocfo.gsa.gov has a popup before page load

## HHS 
- www.phe.gov's homepage is empty 

## NASA

- g5nr.nccs.nasa.gov returns an erroneous MIMETYPE


## Other Websites in General
- Not having a mimetype 

## Other 

Requiring www:
- afadvantage.gov - GSA
- aff.gov - USDA
- afrh.gov - Armed Forces Retirement Home
- ahcpr.gov - HHS
- ahrq.gov - HHS
- america.gov - State
- ameslab.gov - Energy
- anl.gov - Energy
- ars-grin.gov - USDA
- banknet.gov - Treasury
- bop.gov - DOJ
- bts.gov - DOT
- businessdefense.gov - DOD
- defense.gov - DOD
- dnfsb.gov - Defense Nuclear Facilities Safety Board
- fdicconnect.gov - FDIC
- fedcenter.gov - EPA
- federalcourts.gov - US Courts
- federalprobation.gov - US Courts
- federalrules.gov - US Courts
- firecode.gov - Interior
- firenet.gov - Interior
- fmc.gov - federal maritime commission
- forfeiture.gov - DOJ
- fsgb.gov - State
- gcmrc.gov - Interior
- gpodev.gov - GPO
- hive.gov - DOD
- iat.gov - Interior
- intelink.gov - DNI
- intelligencecareers.gov - DOD
- ipcc-wg3.gov - United States Global Change Research Program
- jccs.gov - DOD
- judicialconference.gov - US Courts
- mortgagetranslations.gov - FHFA
- lps.gov - DOD
- nro.gov - DOD
- ntis.gov - Commerce
- nwcg.gov - USDA
- ofcm.gov - Commerce
- ofia.gov - FDIC
- onhir.gov - Office of Navajo and Hopi Indian Relocation
- osac.gov - State
- phe.gov - HHS
- ppdcecc.gov - Congress
- pppl.gov - Energy
- privacyshield.gov - Commerce
- protectyourmove.gov - DOT
- sharetheroadsafely.gov - DOT
- srs.gov - Energy
- supremecourtus.gov - Supreme Court
- symbols.gov - USDA
- usbankruptcy.gov - US Courts
- uscavc.gov - US Courts
- uscp.gov - US Capitol Police
- usprobation.gov - US Courts
- usps.gov - us Postal Service
- ussc.gov - US Sentencing Commission
- wildfire.gov - USDA

Breaks if www is included:  
- www.bankanswers.gov - Treasury
- www.biomassboard.gov - Energy
- www.brain.gov - HHS
- www.business.gov - SBA
- www.buyaccessible.gov - GSA
- www.buyusa.gov - GSA
- www.donaciondeorganos.gov - HHS
- www.energysavers.gov - Energy
- www.eseclab.gov - GAO
- www.exploretsp.gov - Federal Retirement Thrift Investment Board
- www.federaljobs.gov - OPM
- www.fedjobs.gov - OPM
- www.governmentjobs.gov - OPM
- www.greengov.gov - EPA
- www.hhsoig.gov - HHS
- www.iawg.gov - State
- www.icts.gov - Commerce
- www.jwod.gov - United States AbilityOne
- www.nea.gov - National Endowment for the Arts
- www.osc.govc - Office of Special Counsel
- www.ots.gov - Treasury
- www.patriotbonds.gov - Treasury
- www.presidentialserviceawards.gov - CNCS
- www.sen.gov - Congress
- www.smithsonian.gov - Smithsonian
- www.sns.gov - Energy
- www.spd15revision.gov - Commerce
- www.tasefiling.gov - Commerce
- www.thebraininitiative.gov - HHS
- www.tox21.gov - HHS
- www.ui.gov - Labor
- www.unemployment.gov - Labor
- www.unitedstatescongress.gov - Congress
- www.usconsulate.gov - State
- www.usicecenter.gov - Commerce
- www.watermonitor.gov - Interior
