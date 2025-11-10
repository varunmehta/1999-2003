# 1999-2003 Website Archive Restoration Project

## Overview

This document chronicles the restoration of a personal web development archive from 1999-2003, bringing vintage Flash-based websites back to life using modern web technologies. The project involved restoring 60+ websites, integrating Flash emulation, and deploying everything via GitHub Pages.

**Live Site**: [https://varunmehta.github.io/1999-2003/](https://varunmehta.github.io/1999-2003/)

---

## Project Timeline

**Date**: November 2025
**Original Content**: 1999-2003
**Technology Stack**: HTML, Flash/ActionScript, Jekyll, GitHub Pages, Ruffle

---

## Initial Requirements

### The Challenge

Restore a collection of old websites from 1999-2003 that included:
- Flash-based interactive content (Adobe Flash Player deprecated in 2020)
- Multiple website versions and iterations
- Lost or corrupted source files
- Links to defunct hosting services (tripod.com, cjb.net)
- Mixed HTML standards (HTML 3.2, 4.01, early XHTML)

### Goals

1. Create a new git branch for safe experimentation
2. Convert Flash content to work in modern browsers using Ruffle
3. Create a landing page with organized links to all websites
4. Fix all broken links and redirects
5. Make sites accessible as they were in 1999-2003

---

## Technical Approach

### Phase 1: Repository Setup
- Created isolated git branch: `restore-1999-2003-sites`
- Explored directory structure and identified all websites
- Catalogued 60+ SWF (Flash) files across multiple projects

### Phase 2: Flash Emulation with Ruffle
- Integrated [Ruffle](https://ruffle.rs/) - an open-source Flash Player emulator written in Rust
- Added Ruffle script to 44+ HTML files containing Flash content
- Created HTML wrappers for standalone SWF files

### Phase 3: Jekyll Configuration
- Configured Jekyll for GitHub Pages deployment
- Fixed static file serving issues
- Created organized landing page with navigation

### Phase 4: Link Restoration
- Fixed broken redirects to old hosting services
- Created missing index files
- Redirected pages referencing lost Flash files

---

## Technical Issues and Solutions

### Issue 1: Flash Content Deprecated
**Problem**: Adobe Flash Player was discontinued in December 2020. All `.swf` files were unplayable in modern browsers.

**Solution**: Integrated Ruffle Flash emulator via CDN:
```html
<script src="https://unpkg.com/@ruffle-rs/ruffle"></script>
```

### Issue 2: HTML Files Showing Source Code
**Problem**: Jekyll was processing `.htm` files as templates, displaying source code instead of rendered pages.

**Solution**: Simplified Jekyll configuration to serve HTML files as static assets.

### Issue 3: SWF Files Returning 404 Errors
**Problem**: GitHub Pages wasn't serving `.swf` files - all Flash content returned 404 errors.

**Root Cause**: Jekyll `_config.yml` had `*.swf` in the exclude list:
```yaml
exclude:
  - "*.swf"  # This was preventing SWF files from being published!
```

**Solution**: Removed SWF from exclude list and explicitly included all asset types:
```yaml
include:
  - "*.htm"
  - "*.html"
  - "*.swf"
  - "*.gif"
  - "*.jpg"
  - "*.png"
  - "*.css"
  - "*.js"

keep_files:
  - "*.swf"
  - "*.gif"
  - "*.jpg"
  - "*.png"
```

### Issue 4: Missing Flash Files
**Problem**: Some pages referenced `main.swf` that was lost over time.

**Solution**: Redirected pages to alternate entry points with existing Flash files:
```html
<meta http-equiv="refresh" content="0; url=home.htm">
```

---

## Archive Contents

### The Acres Club (2000-2002)
One of Mumbai's first lifestyle clubs. Complete Flash-based website with interactive navigation.

**Technologies**: Flash 5, HTML 4, CSS
**Features**: Animated navigation, image slideshows, contact forms

### Digital Art Portfolio
CGI and 3D modeling work created in Photoshop, Blender, and 3D Studio Max. Portfolio built for MDes applications.

**Technologies**: HTML, DHTML, JavaScript
**Techniques**: Computer-generated imagery, photomanipulation, 3D rendering

### Flash Freelance Projects (13 Projects)
Client work done as a freelancer, including:
- **ACPCE**: Association of Consulting Civil & Public Health Engineers
- **E-Tco Telecom**: Corporate website with Flash animations
- **Match Fixing Game**: Interactive Flash game
- **Optivity**: Corporate website
- **Whatman**: Project showcase
- Plus 8 experimental Flash animations

### VarunInfo (7 Versions)
First personal website showing portfolio evolution from 1999-2003. Each version represents different design trends and technical skills.

**Version Highlights**:
- Ver 1-3: Basic HTML with frames
- Ver 4: Flash integration begins
- Ver 5-7: DHTML, CSS, advanced layouts

### VarunMehta Portfolio (3 Versions)
Complete name portfolio with progressively more sophisticated Flash integration.

### M.M. Enterprises
Father's side business - paper and board dealership website.

**Technologies**: Basic HTML, Flash navigation
**Features**: Product catalog, dealer network, contact information

### Software & Utilities
Engineering projects and presentations including:
- DC Machines software
- Flash-based technical presentations

### CGI-BIN Scripts
Collection of early server-side scripts, jokes database, and poetry (Shairye).

---

## Changes Performed

### Files Modified: 62
- 44+ HTML files updated with Ruffle integration
- 17 new files created
- 340 lines added, 48 lines removed

### New Files Created
1. `index.md` - Main landing page
2. `_config.yml` - Jekyll configuration
3. `flash/bobby.html` - Flash wrapper
4. `flash/Main.html` - Flash wrapper
5. `flash/When.html` - Flash wrapper
6. `flash/Where.html` - Flash wrapper
7. `softwares/Presentation.htm` - Flash wrapper
8. `softwares/index.htm` - Section index
9. `cgi-bin/index.htm` - Section index
10. `varuninfo/ver5/index.htm` - Redirect file
11. `varunmehta/index.htm` - Redirect file

### Git Commits
1. **Restore 1999-2003 websites with Ruffle Flash emulator** - Core restoration work
2. **Configure Jekyll for GitHub Pages** - Jekyll setup and configuration
3. **Fix missing main.swf in Acres website** - Fixed broken Flash references
4. **Fix SWF files not being served by GitHub Pages** - Critical bug fix

---

## Restoration Statistics

- **Total Websites Restored**: 60+
- **Flash Files Recovered**: 60 SWF files
- **HTML Files Modified**: 44+
- **Time Period Covered**: 1999-2003 (4 years)
- **Technologies Preserved**: Flash 4/5/6, HTML 3.2/4.01, DHTML, CSS 1/2, JavaScript

---

## Historical Context

### The Early 2000s Web

This archive represents a specific era in web development:

- **Flash Era**: Flash was the primary technology for interactive web content
- **Dial-up Internet**: Sites optimized for 56k modems
- **Web Standards**: HTML 4.01, CSS 2, ECMAScript 3
- **Browser Wars**: Sites often included "Best viewed in IE/Netscape" notices
- **Hosting Services**: Free hosting on Tripod, GeoCities, Angelfire
- **Search Engine Dominance**: Google was just beginning to dominate (launched 1998)

### Personal Milestones

- **2000-2001**: Top 3 Google results for "varun mehta" and "varun info"
- **First Commercial Client**: The Acres Club website
- **Freelance Work**: Earning money for first motorcycle
- **Portfolio Evolution**: 10 distinct portfolio versions
- **Technical Growth**: From basic HTML to Flash ActionScript

---

## Technologies Used in Restoration

### Modern Stack
- **Git**: Version control and safe experimentation
- **Jekyll**: Static site generator for GitHub Pages
- **GitHub Pages**: Free hosting and deployment
- **Ruffle**: Flash Player emulator (WebAssembly)
- **Markdown**: Documentation and landing page

### Preserved Technologies
- **Flash/ActionScript**: Interactive content (now via Ruffle)
- **HTML 3.2/4.01**: Original markup preserved
- **CSS 1/2**: Original styling maintained
- **JavaScript**: Image preloading, popups, DHTML effects
- **Frames**: Some sites use framesets (preserved as-is)

---

## Lessons Learned

### Web Preservation Challenges
1. **Proprietary Technologies**: Flash's discontinuation highlights the risk of proprietary tech
2. **File Rot**: Some files were corrupted or lost over 20+ years
3. **Dependency Hell**: External resources (counters, analytics) no longer work
4. **Link Decay**: External links to defunct services
5. **Format Obsolescence**: Some technologies have no modern equivalent

### Successful Strategies
1. **Emulation over Conversion**: Ruffle allows Flash to run as-is
2. **Minimal Modifications**: Preserved original design and code
3. **Documentation**: This file ensures future maintainers understand the archive
4. **Version Control**: Git branch strategy allowed safe experimentation
5. **Static Hosting**: GitHub Pages provides reliable, free hosting

---

## Future Considerations

### Maintenance
- **Ruffle Updates**: Monitor Ruffle project for compatibility improvements
- **GitHub Pages Limits**: Current repo is well under the 1GB soft limit
- **Link Monitoring**: Periodically check for broken internal links
- **Browser Testing**: Test in multiple browsers as web standards evolve

### Potential Enhancements
- Add metadata/timestamps to each website
- Create a visual timeline of portfolio evolution
- Extract and display Flash source code (if available)
- Add contemporary screenshots for comparison
- Create mobile-responsive wrapper for vintage sites

### Archival Considerations
- **Backup Strategy**: Maintain local copies outside of Git
- **Format Migration**: Consider converting Flash to HTML5 Canvas if Ruffle development stops
- **Internet Archive**: Submit to Wayback Machine for long-term preservation
- **Digital Preservation**: Follow archival best practices

---

## Acknowledgments

- **Ruffle Project**: For creating an open-source Flash emulator
- **GitHub**: For free hosting via GitHub Pages
- **Jekyll**: For static site generation
- **Original Content Creators**: Clients and collaborators from 1999-2003

---

## Repository Information

**Repository**: [github.com/varunmehta/1999-2003](https://github.com/varunmehta/1999-2003)
**Branch**: `restore-1999-2003-sites`
**Live Site**: [varunmehta.github.io/1999-2003](https://varunmehta.github.io/1999-2003/)
**License**: Personal archive - all rights reserved

---

## Conclusion

This restoration project successfully brought 20+ year old websites back to life, preserving a snapshot of early 2000s web development. Through modern emulation technologies and careful preservation techniques, the archive remains accessible and functional for future generations.

The project demonstrates that with proper tools (Ruffle, Git, GitHub Pages) and careful planning, vintage web content can be preserved and made accessible despite deprecated technologies like Flash.

---

*This restoration was completed in November 2025 using Claude Code.*

*Archive content originally created 1999-2003.*
