
As the [Federal Website Standards](https://standards.digital.gov) project progresses, we've submitted a [proposal](https://github.com/GSA-TTS/federal-website-standards/discussions/310
) for certain standards that we both think make sense and will also help ensure that our scans can complete.  This proposal serves as a drafting board for us to further flesh out the proposed standards.  

----------------------------------

If one standard...

For any x.gov that intends to be a public-facing website, set a small number of clear, consistent structural expectations:

- HTTPS required
  - Problem this addresses: fundamental security need, and formal requirement all sites have
- Ensure that the base domain works both with or without www. In other words, both https://www.x.gov and https://x.gov resolve and one redirects to the other.
  - Problems this addresses: www. being required; the absence of www. being required; the two URLs resolving to different files.
- For subdomains, if www. is used it cannot be required. In other words, if https://www.something.agency.gov exists, the www. should not be required (https://something.agency.gov should work for a user).
  - www. being required
- A website should have a live homepage at its root. In other words, if there is live content anywhere on a website (e.g. at https://program.gov/something/somethingelse), then the site should have a homepage (e.g. at https://program.gov).
  - Confusion for a user seeking a website's main page; difficulty caused for scanning efforts.

----------------------------------


If distinct standards...


Standard: HTTPS required for all websites.    
Why: An HTTPS-Only standard will eliminate inconsistent, subjective determinations across agencies regarding which content or browsing activity is sensitive in nature, and create a stronger privacy standard government-wide.     
Research questions: What barriers do you face to achieving 100% compliance?    
Read more:     
- https://https.cio.gov    
- https://obamawhitehouse.archives.gov/sites/default/files/omb/memoranda/2015/m-15-13.pdf    
- https://www.whitehouse.gov/wp-content/uploads/2023/09/M-23-22-Delivering-a-Digital-First-Public-Experience.pdf    
- https://www.congress.gov/bill/115th-congress/house-bill/5759/text    

----------------------------------


Standard: Ensure that the base domain works both with or without www.    
Why: This will ensure a better visitor experience by eliminating failed page loads if a user attempts to load a domain with or without `www.`.      
Research questions:  ...    
Read more:    
- "With these techniques, you can configure your server to respond correctly for both, the www-prefixed and the non-www-prefixed domains. It is good advice to do this since you can't predict which URL users will type in their browser's URL bar."  [mozilla.org](https://developer.mozilla.org/en-US/docs/Web/URI/Guides/Choosing_between_www_and_non-www_URLs)    
- "...your site must work with or without the www." [sitepoint.com](https://www.sitepoint.com/domain-www-or-no-www/)    
- "...it’s important to ensure both the ‘www’ and non-‘www’ versions of your domain are accessible, as users may type either." [sitepoint.com](https://www.sitepoint.com/domain-name-www-or-not/)

----------------------------------



Standard: _(briefly describe what the standard is (one sentence))_    
Why: _(why this standard should be required (who would benefit, and how would they benefit))_    
Research questions:  _(a bulleted list of things we want to validate with agencies concerning this standard)_    
Read more: _(any links to authoritative sources that support the need for this standard)_    

----------------------------------

Standard: _(briefly describe what the standard is (one sentence))_    
Why: _(why this standard should be required (who would benefit, and how would they benefit))_    
Research questions:  _(a bulleted list of things we want to validate with agencies concerning this standard)_    
Read more: _(any links to authoritative sources that support the need for this standard)_    


----------------------------------
