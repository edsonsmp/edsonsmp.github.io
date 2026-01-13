# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Portfolio case study website showcasing the "Roteirizador Inteligente" (Intelligent Routing System) project developed for Involves. This is a static HTML/CSS/JavaScript portfolio site demonstrating a UX/Product Design case study about an AI-powered route optimization system that reduced operational costs by up to 20% for enterprise clients like Heineken, Unicharm, O Boticário, and Fini.

## Technology Stack

- **Pure Vanilla JavaScript** (no frameworks or libraries)
- **HTML5** semantic markup
- **CSS3** with a custom Design System using CSS Variables
- **Mobile-first responsive design**
- **Progressive enhancement** approach

## Architecture & Structure

### CSS Architecture (Design System)

The CSS follows a layered architecture with strict import order:

1. **[reset.css](portfolio/css/reset.css)** - CSS reset/normalization
2. **[variables.css](portfolio/css/variables.css)** - Design tokens (colors, typography, spacing, shadows, transitions)
3. **[base.css](portfolio/css/base.css)** - Base HTML element styles
4. **[layout.css](portfolio/css/layout.css)** - Layout utilities (container, grid, sections)
5. **[components.css](portfolio/css/components.css)** - Component-specific styles (header, cards, buttons)

**Important**: Always maintain this CSS import order. The design system uses CSS Custom Properties (variables) extensively - never hardcode values that exist as tokens in [variables.css](portfolio/css/variables.css).

### Design Token System

All design decisions are tokenized in [variables.css](portfolio/css/variables.css):
- **Color system**: Neutral, accent, semantic colors
- **Typography**: Fluid sizing using `clamp()` for responsive text
- **Spacing**: 8px grid system (`--space-xs` through `--space-4xl`)
- **Shadows**: Layered shadow system inspired by modern design
- **Transitions**: Consistent easing and timing
- **Z-index scale**: Predictable layering (`--z-base` to `--z-tooltip`)

### JavaScript Architecture

[main.js](portfolio/js/main.js) uses an IIFE (Immediately Invoked Function Expression) pattern with modular initialization functions:

- **Header scroll behavior**: Adds `.scrolled` class on scroll with throttled performance
- **Smooth scroll**: For anchor links, respects `prefers-reduced-motion`
- **Scroll animations**: Intersection Observer for fade-in effects
- **Reading progress bar**: Visual scroll indicator
- **External links**: Automatic security attributes
- **Keyboard navigation**: Enhanced focus states for accessibility

All JavaScript features use **progressive enhancement** - the site works without JS, enhanced with it.

### HTML Structure

Two main pages:
- **[index.html](portfolio/index.html)** - Portfolio landing page with work showcase
- **[case-roteirizador-resumido.html](portfolio/case-roteirizador-resumido.html)** - Full case study page

Both follow semantic HTML5 structure with accessibility features:
- Skip-to-content links
- Semantic landmarks (`<header>`, `<main>`, `<section>`)
- Proper heading hierarchy
- ARIA attributes where appropriate

## Development Guidelines

### Working with CSS

1. **Never hardcode values** - Use design tokens from [variables.css](portfolio/css/variables.css)
2. **Follow the cascade** - Respect the CSS layer order (reset → variables → base → layout → components)
3. **Mobile-first** - Write base styles for mobile, add `@media` queries for larger screens
4. **Use semantic class names** - Follow BEM-like conventions (`.card`, `.card-title`, `.card-content`)

### Working with JavaScript

1. **Respect `prefers-reduced-motion`** - Always check before adding animations
2. **Progressive enhancement** - Features should enhance, not be required
3. **Performance-conscious** - Use `requestAnimationFrame` for scroll handlers, `passive: true` for event listeners
4. **Intersection Observer** - Prefer over scroll event listeners for visibility detection

### Accessibility Requirements

- Maintain semantic HTML structure
- Preserve skip-to-content links
- Keep keyboard navigation functional
- Respect reduced motion preferences
- Ensure color contrast meets WCAG AA standards

### File Paths

When updating HTML files, note that:
- [index.html](portfolio/index.html) uses relative paths: `css/variables.css`, `js/main.js`
- [case-roteirizador-resumido.html](portfolio/case-roteirizador-resumido.html) currently has absolute paths (should be relative)
- Images are in `assets/images/`

## Case Study Content Context

The portfolio showcases a real product design case about an AI-powered route optimization system:

- **Business context**: Trade marketing operations for CPG (Consumer Packaged Goods) companies
- **Problem**: Manual route planning, inconsistent data, high operational costs
- **Solution**: Partial automation with AI validation (MVP approach)
- **Results**: 20% cost reduction, 46-second route generation, improved reliability
- **Trade-off**: Accepted complex onboarding to validate AI quality first

Key learning: The case demonstrates **decision-making under uncertainty** and prioritizing **technical validation over user experience polish** in early stages.

## Content Location

- Case study content files (markdown): Root directory
  - `case-resumido.md` - Condensed case overview
  - `context.txt` - Extended case analysis and workflow documentation
- Portfolio HTML: `portfolio/` directory
- Assets: `portfolio/assets/images/`

## Common Tasks

### Viewing the site locally
Open HTML files directly in a browser (no build process required) or use a simple HTTP server:
```bash
cd portfolio
python3 -m http.server 8000
# Open http://localhost:8000
```

### Making design changes
1. Identify the appropriate CSS file based on the layered architecture
2. Check if a design token exists in [variables.css](portfolio/css/variables.css)
3. Use existing tokens rather than creating new values
4. Test responsive behavior from mobile → desktop

### Adding new components
1. Add component markup to HTML with semantic, descriptive class names
2. Add component styles to [components.css](portfolio/css/components.css)
3. Use existing design tokens for consistency
4. Ensure mobile-first responsive behavior
