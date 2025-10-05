# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Interstellar Interface** - A NASA Hackathon project for exploring massive space image datasets with advanced zoom and analysis capabilities.

This is a single-page web application built with pure HTML5, CSS3, and vanilla JavaScript. It uses OpenSeadragon for high-resolution image viewing and is designed to make NASA's gigapixel imagery accessible to researchers, students, educators, and space enthusiasts.

## Architecture

### Single-File Application Structure
- **index.html** - The entire application is contained in one HTML file with embedded CSS and JavaScript
  - Lines 1-302: HTML structure and embedded CSS styling
  - Lines 303-587: HTML content for 4 main pages (Home, Viewer, Comparison, About)
  - Lines 596-765: JavaScript application logic

### Page Navigation System
- Uses JavaScript to toggle between 4 pages without page reloads
- `showPage(pageName)` function (lines 605-622) handles page switching
- Pages: `home`, `viewer`, `comparison`, `about`
- Each page is a `<div>` with class `page`, shown/hidden via CSS class `active`

### Image Viewer Components
1. **Main Viewer** (lines 625-649)
   - `initMainViewer()` initializes OpenSeadragon viewer
   - Uses OpenSeadragon CDN v4.1.0
   - Configured for NASA images with CORS support
   - Supports zoom, pan, and fullscreen modes

2. **Comparison Viewers** (lines 652-680)
   - `initComparisonViewers()` creates side-by-side viewers (viewerA and viewerB)
   - Allows synchronized navigation between two images
   - Used for temporal analysis and multi-spectral comparisons

### Key Features
- **Annotation System** (lines 717-730): Placeholder for marking features on images
- **Image Loading** (lines 700-714): Dynamic loading of different NASA datasets
- **Comparison Controls** (lines 733-759): Sync/unsync viewers, swap images
- **Viewer Controls** (lines 683-697): Zoom in/out, reset, fullscreen

## Development Commands

Since this is a static HTML project, there are no build commands. To develop:

```bash
# Open the file directly in a browser
open index.html

# Or serve with a simple HTTP server (recommended for CORS)
python3 -m http.server 8000
# Then visit http://localhost:8000
```

## Working with Images

### Current Image Sources
The application currently uses publicly accessible NASA image URLs:
- Mars: Mars Reconnaissance Orbiter (MRO)
- Moon: Lunar Reconnaissance Orbiter (LRO)
- Earth: Apollo 17 Blue Marble
- Deep Space: Hubble Space Telescope imagery

### Adding New Images
To add a new image to the gallery (lines 409-439):
1. Add a new `image-card` div with appropriate NASA image URL
2. Update the `loadImage()` function (lines 700-714) to include the new image type
3. Ensure images are high-resolution and publicly accessible

## Styling System

The application uses:
- Gradient backgrounds: `linear-gradient(135deg, #0a0e27 0%, #1a1f3a 100%)`
- Glass-morphism effects: `backdrop-filter: blur(10px)` with transparent backgrounds
- Responsive grid layouts for image cards and feature cards
- CSS animations for page transitions (fadeIn animation, lines 87-90)

## Known Limitations

1. **Demo Mode**: Currently uses static NASA image URLs instead of connecting to NASA's tile servers
2. **Annotations**: Annotation UI exists but requires full Annotorious library integration for production
3. **Search**: Search box is placeholder; needs implementation with coordinate/feature database
4. **CORS**: Some NASA images may have CORS restrictions; uses `crossOriginPolicy: 'Anonymous'`

## Future Integration Points

According to the codebase (lines 556-564), planned enhancements include:
- AI-powered feature detection (TensorFlow.js integration mentioned in lines 534-537)
- Collaborative annotations with multiple users
- Integration with NASA EarthData, PDS, and other data sources
- 3D terrain visualization from elevation data
- Time-lapse animations
- Mobile app versions
- Research API

## Team Information

Project by Team Interstellar Interface:
- Iqra Jannat
- Kulsoom Alim
- Mohamed Dahir
- Temis Manakkal

NASA Hackathon Project 2025
