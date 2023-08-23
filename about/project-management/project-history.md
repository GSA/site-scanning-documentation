
### Past scanning efforts

From 2011 to 2015, Ben Balter, a staffer within the Office of the Chief Information Officer at the Executive Office of the President and later a Presidential Innovation Fellow, performed an [analysis of federal.gov domains](https://ben.balter.com/2015/05/11/third-analysis-of-federal-executive-dotgovs/).  

Later in 2015, Jon Tindle (OGP), Eric Mill (TTS), and Gray Brooks (TTS) built https://pulse.cio.gov/ and the [two open-source site scanners](https://github.com/18F/domain-scan) that gather the data for that website: the use of [Hypertext Transfer Protocol Secure (HTTPS)](https://https.cio.gov/) and participation in the government’s [Digital Analytics Program (DAP)](https://analytics.usa.gov/).  Between 2016-2017, three other scanners were prototyped by Eric Mill, but are not currently deployed: participation in the [U.S. Web Design System](https://github.com/18F/domain-scan/commit/4458978d3871909c047319aba1102f32e6b51349), [Accessibility](https://github.com/18F/domain-scan/blob/master/scanners/a11y.py), and the use of [third-party services](https://github.com/18F/domain-scan/blob/master/scanners/third_parties.js). 

In 2016, OGP built https://digitaldashboard.gov/, which incorporates results from the Pulse HTTPS and DAP scans, as well as accessibility, mobile-responsiveness, IPv6, and Domain Name System Security Extensions (DNSSEC). Results are available to Federal employees behind a secure login. 

Between 2015 - 2017, DHS builts scans for [HTTPS](https://github.com/18F/domain-scan/blob/master/scanners/pshtt.py) and [Trusted Email](https://github.com/18F/domain-scan/blob/master/scanners/trustymail.py) to help assess whether agencies were in compliance with [Binding Operational Directives](https://cyber.dhs.gov/directives/). From these scans, DHS generates weekly “cyber hygiene reports” and sends these PDFs to agencies. 

### Early program history


<li> 2016-2017 - Eric Mill prototypes USWDS, Accessibility, and Third-party Services scans.</li>
	<li> July 2018 - Eric Mills submits an idea to 10x to address the inability to easily scan sites for federal website best practices and standards. At the time there is no actively-maintained scanning infrastructure in production, no long-term solution for storing results (cloud.gov sandbox), and site scanning is not architected to be replicable (for interested parties to stand up their own copy of site scans) or extensible (for new, custom scans to be added to the suite). He proposes 10x to build a cloud-based tool that automatically scans federal sites so federal employees could use to see what's behind these sites.</li>
	<li> Fall 2018 - 10x funds Site Scanner. <a href="https://10x.gsa.gov/the-10x-process/">Phase 1 begins</a>. Phase 1 team finds in support of the idea and requests Phase 2 funding.</li>
	<li> Summer 2019 - 10x funds Site Scanner Phase 2. Team develops initial product strategy, and launches prototypes of Site Scanner.</li>
	<li> Fall 2019 - Phase 2 team launches the Site Scanner website which includes 200 and USWDS scanner search results, individual pages for /code.json, /data.json, /data, /developer, /digitalstrategy, /open, /privacy, /robots.txt, and /sitemap.xml 200 scans, and various data export options aimed at technical users. Team finds in support of the idea and requests Phase 3 funding.</li>
	<li> Winter 2019 - 2020 - 10x funds Site Scanner Phase 3. Team refines product strategy, continues outreach, and develops a customizable UI for Site Scanner.</li>
</ul>
