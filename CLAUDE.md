# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**HubPatagonia** is a landing page for a tech community in Patagonia, Chile (Aysén region). It's a static HTML site promoting community membership with three subscription tiers, event announcements, and testimonials.

## Tech Stack

- **HTML/CSS/JS**: No build process, no framework
- **Styling**: Tailwind CSS (via CDN) + custom CSS (style.css)
- **Animations**: Vanilla JavaScript scroll-reveal animations
- **Hosting**: GitHub Pages (hubpatagonia.tech)
- **AI Integration**: OpenCode AI plugin for code generation (.opencode folder)

## Development

### View the site locally

Open `index.html` directly in your browser (no server required) or:

```bash
python3 -m http.server 8000
# Open http://localhost:8000
```

### Project structure

```
index.html              # Main landing page (all content in one file)
style.css              # Additional CSS (mostly overridden by Tailwind)
assets/                # SVG logos and favicon
.opencode/             # OpenCode AI plugin (auto-generated files)
CNAME                  # GitHub Pages domain (hubpatagonia.tech)
```

## Architecture

The page is a **single-file static site** with six main sections:

1. **Navigation** - Fixed header with logo and nav links (responsive menu)
2. **Hero** - Large headline with gradient text, CTA buttons, floating animations
3. **Features** - 6 feature cards (Community, Innovation, Events, Training, Opportunities, Recognition)
4. **Pricing** - 3 subscription tiers (Free, Pro $5k/mo, Business $25k/mo)
5. **Testimonials** - 3 member quotes with 5-star ratings
6. **CTA Section** - "Únete" call-to-action with Discord/LinkedIn links
7. **Footer** - Logo, social links, copyright

All styling is inline Tailwind utility classes except for:
- Custom animations (gradient, float) defined in `<style>`
- Glass morphism effects (.glass-card)
- Scroll-triggered reveal animations (.reveal class)
- Responsive utilities

## Key Details

### Tailwind Configuration

Inline config in `<script>` tag in `<head>`:
- Custom color palette (primary blue, secondary orange, backgrounds)
- Font families (Space Grotesk for headings, DM Sans for body)
- Custom animations (float, gradient)

### Animations

- **Scroll-reveal**: `.reveal` elements animate in as user scrolls (opacity + translateY)
- **Floating elements**: `.animate-float` and `.animate-float-delayed` (y-axis movement)
- **Gradient text**: Animated background-position gradient on heading
- **Hover effects**: `.hover-lift` cards elevate on hover with shadow

JavaScript in footer handles scroll detection for `.reveal` class.

### Responsive Design

- Mobile-first approach using Tailwind breakpoints (sm, md, lg)
- Navigation menu hidden on mobile, shown on md breakpoint
- Cards grid switches from 2-3 columns on desktop to 1 column on mobile
- Padding and font sizes scale with clamp() for fluid typography

## Editing Tips

- **Colors**: Defined in Tailwind config `theme.colors` — update there for consistency
- **Section spacing**: `.section-padding` or manual `py-24 md:py-32` classes
- **Adding content**: All content is in index.html; no templates or components
- **Font changes**: Space Grotesk (headings, h1-h6), DM Sans (body text)
- **Glass effect**: Use `.glass-card` class for frosted glass appearance
- **Animations**: New animations go in `<style>` block; new classes inherit Tailwind keyframes

## Deployment

Site is deployed via GitHub Pages. Push to `main` branch to deploy.

```bash
git checkout main
git merge UiUxProMax
git push origin main
```

The site is live at **hubpatagonia.tech** (configured via CNAME file).

## Language

Content is in **Spanish** (es). Headings, CTAs, and all text are Spanish-language.
