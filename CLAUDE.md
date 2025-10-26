# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Xtreme Surge Sales Funnel** - A static HTML/CSS/JavaScript landing page and checkout system for a male enhancement product. No build tools, no frameworks, no backend - pure static files served directly.

## Architecture

### Page Flow
```
index.html (Landing) → xtreme.html (Checkout/Order)
```

### Asset Organization
- **`/assets/`** - Checkout page assets (CSS, JS, images, fonts)
  - `css/checkout.css` (1,130 lines) - Checkout form styling
  - `css/responsive.css` (1,672 lines) - Mobile breakpoints
  - `js/scripts.js` - CVV toggle, countdown timers, shipping date calculation
  - `js/social-proof.js` - Fake customer notification generator
  - `js/jquery.cardtype.js` - Credit card validation (Luhn algorithm)
  - `js/jquery.mask.min.js` - Input masking (phone, CC numbers)
  - `js/threeds.2.min.latest.js` - 3D Secure payment authentication

- **`/new_assets/`** - Landing page assets
  - `css/index.css` (13,318 lines) - Main landing page styles
  - `css/custom.css` (11,096 lines) - Form validation, custom components
  - `css/responsive.css` (44,089 lines) - Extensive mobile responsive design
  - Slick slider for testimonials carousel

- **`/new_assets3/`** - Minimal placeholder assets (logo only)

### Key Files

**index.html (717 lines)**
- Multi-section landing page with product showcase
- Right-side registration form (name, address, phone, email)
- Benefits sections, testimonials, trust badges
- "As Seen On" media mentions
- Security seals and money-back guarantees

**xtreme.html (2,864 lines)**
- Complete checkout/order form
- Credit card validation and payment processing
- Address collection
- Product/quantity selection
- Order summary and shipping info

## Development

### Running Locally
```bash
# Option 1: Python simple server
python3 -m http.server 8000

# Option 2: PHP built-in server
php -S localhost:8000

# Option 3: Node.js http-server (if installed globally)
npx http-server -p 8000
```

Then open: `http://localhost:8000/index.html`

### Testing Changes
- No build process - edit HTML/CSS/JS directly
- Refresh browser to see changes
- Test responsive design using browser DevTools
- Verify forms on both pages (index.html and xtreme.html)

### Git Workflow
- Main branch: `main`
- Development branch: `dev`
- Create PRs from dev → main
- Remote: `git@github.com:codebytesss/getxtremesurge.git`

## Code Patterns

### Form Handling
- POST method to server endpoint (currently `action="#"`)
- Client-side validation with CSS classes: `.has-error`, `.has-success`
- HTML5 pattern validation attributes
- Hidden country field defaults to "US"

### Responsive Design
- Desktop fixed width: 1004px contentWrap
- Mobile-first with extensive breakpoints
- Device detection classes (e.g., `device-desktop-page-index`)
- Hidden/repositioned elements for mobile views

### JavaScript Utilities
- **Countdown Timers**: Two variants (10 min, 2 min) in `/assets/js/scripts.js`
- **Social Proof**: Auto-rotating fake customer notifications every 7 seconds
- **Card Validation**: Supports Visa, Mastercard, Amex, Discover, JCB, Maestro, Diners
- **Smooth Scrolling**: Anchor link navigation

### CSS Architecture
- Absolute/relative positioning for complex layouts
- Background images for section backgrounds
- Color scheme: Purple (#5a266e, #6a2e84), Orange (#f47a30), Blue (#2c529d)
- Font: Open Sans (Google Fonts)
- Normalize.css for CSS reset

### Trust Building Elements
- Fake customer notifications (generated JS with random US states/names)
- Security seals (Symantec, SSL)
- Testimonial sliders with reviews
- Media logos and "As Seen On" sections
- Money-back guarantee badges

## Important Notes

### No Build System
- No package.json, no npm scripts, no webpack/vite
- No TypeScript, no transpilation
- Edit files directly and refresh browser

### Form Submission
- Forms currently point to `action="#"`
- In production, update form actions to actual backend endpoints
- Credit card processing requires backend integration

### Path References
- All asset paths are relative (`./assets/`, `./new_assets/`)
- Some hardcoded paths exist (e.g., `/us-z1/assets3/` in xtreme.html)
- Verify paths when deploying to different directory structures

### jQuery Dependencies
- Multiple jQuery plugins used (mask, cardtype, slick slider)
- jQuery loaded via CDN in HTML files
- Check jQuery version compatibility when updating

## File Locations Reference

**Landing Page (index.html):**
- Styles: `/new_assets/css/`
- Images: `/new_assets/images/`, `/new_assets/brand/`
- Scripts: Inline and `/new_assets/js/` (for slick slider)

**Checkout Page (xtreme.html):**
- Styles: `/assets/css/`
- Images: `/assets/images/`, `/assets/brand/`
- Scripts: `/assets/js/`
- Fonts: `/assets/fonts/`

**Shared Elements:**
- Logo: `/new_assets3/images/logo.png` (favicon)
- Both pages use Open Sans from Google Fonts
- important: just reponse me shortly every time maybe one line or one word not longer that two lines