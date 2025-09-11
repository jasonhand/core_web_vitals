# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is an interactive, educational web application that demonstrates Google's Core Web Vitals performance metrics through hands-on visualizations. It's built as a single HTML file with embedded CSS and JavaScript, requiring no external dependencies or build process.

## Project Structure

```
core_web_vitals/
├── index.html          # Single-file application with all code
├── README.md           # Comprehensive project documentation
└── LICENSE             # MIT license
```

## Architecture

This is a **single-page application (SPA)** built with vanilla HTML, CSS, and JavaScript:

- **No external dependencies** - Everything is self-contained
- **Tab-based navigation** - JavaScript-driven content switching between Core Web Vitals metrics
- **Interactive visualizations** - Animated demonstrations of FCP, LCP, INP, and CLS
- **Real-time simulations** - Interactive buttons and timers to demonstrate performance concepts
- **Responsive design** - CSS Grid and Flexbox for mobile/desktop support

### Key Components

1. **Tab System**: JavaScript-controlled navigation between different Core Web Vitals sections
2. **Animation Engine**: Custom JavaScript functions for FCP and LCP loading demonstrations
3. **Interactive Demos**: Real-time INP measurement and CLS layout shift demonstrations
4. **Educational Content**: Detailed explanations, scoring thresholds, and optimization tips
5. **Code Examples**: JavaScript snippets showing how to measure Core Web Vitals in production

## Development Commands

Since this is a static HTML application, no build commands are required:

```bash
# Serve locally (optional)
python -m http.server 8000    # Python 3
python -m SimpleHTTPServer    # Python 2
# Or use any static file server

# Open directly in browser
open index.html
```

## Key Features to Understand

- **Self-contained**: All styles, scripts, and content are embedded in `index.html`
- **Educational focus**: Designed to teach Core Web Vitals through interactive demonstrations
- **Performance optimized**: The demo itself follows Core Web Vitals best practices
- **Accessibility**: Semantic HTML structure with keyboard navigation support
- **Browser mockups**: CSS-only browser interface simulations for realistic demonstrations

## Making Changes

When modifying this project:

1. **All changes go in `index.html`** - This is a single-file application
2. **Test interactive features**: Ensure animations, timers, and button interactions work correctly
3. **Verify responsiveness**: Test on different screen sizes (mobile/desktop)
4. **Check educational accuracy**: Core Web Vitals thresholds and explanations should be current
5. **Maintain performance**: Keep the demo fast and lightweight as an example of good practices

## Core Web Vitals Covered

- **First Contentful Paint (FCP)**: ≤1.8s good, with animated loading demonstration
- **Largest Contentful Paint (LCP)**: ≤2.5s good, with hero image loading simulation  
- **Interaction to Next Paint (INP)**: ≤200ms good, with interactive response time testing
- **Cumulative Layout Shift (CLS)**: ≤0.1 good, with layout shift demonstration

## Educational Content Structure

Each metric section includes:
- Definition and explanation
- Performance thresholds (Good/Needs Improvement/Poor)
- Interactive visualization
- Optimization tips
- Code examples for measurement

The project serves as both a learning tool and a reference implementation for web performance education.