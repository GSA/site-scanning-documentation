# Site Scanning Process Slides

This directory contains PDF slides generated from the `pages/scan_steps.md` documentation.

## Generated Files

- **`scan_steps_slides.pdf`** - Basic slides generated directly from the original markdown
- **`scan_steps_clean_slides.pdf`** - Cleaned up version with better slide breaks and formatting  
- **`scan_steps_enhanced_slides.pdf`** - Enhanced presentation with improved structure, themes, and organization
- **`scan_steps_slides.md`** - Enhanced markdown source file used to generate the enhanced slides

## How to Generate

The slides were generated using Pandoc with the Beamer LaTeX class:

```bash
# Basic conversion
pandoc pages/scan_steps.md -t beamer -o scan_steps_slides.pdf --slide-level=2

# Enhanced version with theme
pandoc scan_steps_slides.md -t beamer -o scan_steps_enhanced_slides.pdf --slide-level=2 -V theme:Madrid

# Clean version with better slide breaks
pandoc pages/scan_steps.md -t beamer -o scan_steps_clean_slides.pdf --slide-level=3 -V theme:Madrid -V fontsize:10pt
```

## Requirements

To regenerate these slides, you need:
- Pandoc
- LaTeX (texlive-latex-base, texlive-latex-recommended, texlive-pictures, texlive-latex-extra)

## Content

The slides cover the technical process of how the Site Scanning program analyzes federal websites, including:

- Initial data population
- Primary scan components (URL, CMS, cookies, DAP, login, mobile, etc.)
- DNS scan details
- 404 testing
- Robots.txt and sitemap.xml analysis
- Scan status tracking and results

The enhanced slides provide a more structured presentation suitable for technical presentations and training sessions.