# Copilot Instructions for Photography Portfolio Site

## Project Overview
This is a **single-page HTML/CSS portfolio website** for Tetyana Ryasnykh, a photographer and videographer based in Cannes. The project is a **self-contained `index.html` file** with embedded CSS and minimal dependencies (no build process, no frameworks).

## Architecture & Key Files

### Structure
- **`index.html`** – Single monolithic file containing:
  - Semantic HTML sections (hero, about, services, portfolio, contact, footer)
  - Embedded CSS with design system variables
  - No JavaScript; purely structural and styled

### Design System (CSS Variables)
Located in the `:root` selector of `index.html`:
- **Color Palette**: Warm, editorial aesthetic (beige `#DED8D3`, brown accents `#4A301B`)
- **Typography**: Montserrat font family, light weights (300, 400, 500), uppercase text transforms
- **Spacing**: `--container-width: 1200px`, `--section-padding: 100px 24px`
- **Animations**: `--ease: cubic-bezier(0.25, 1, 0.5, 1)` for smooth transitions

### Sections & Content Areas

| Section | ID | Purpose | Key Pattern |
|---------|-----|---------|------------|
| **Navigation** | `.navbar` | Fixed top nav with anchor links | Semi-transparent backdrop blur |
| **Hero** | `#hero` | Full-viewport intro with CTA buttons | Background image overlay, asymmetric grid layout (1.2fr 1fr) |
| **About** | `#about` | Photographer bio & credentials | Two-column grid (text + image), reorders on mobile |
| **Services** | `#services` | Offerings with pricing | 4-column card grid, hover lift effect (`translateY(-5px)`) |
| **Portfolio** | `#portfolio` | Image gallery showcase | 3-column grid, 4:5 aspect ratio, zoom on hover |
| **Contact** | `#contact` | Form + info block | 1.5fr/1fr two-column layout, minimal form styling (border-bottom only) |
| **Footer** | `<footer>` | Copyright & tagline | Centered, light background |

## Development Patterns & Conventions

### Design Token Usage
Always reference CSS variables in `/root` rather than hardcoding colors:
```css
background-color: var(--bg-color);        /* Not #DED8D3 directly */
border: 1px solid var(--border-color);
```

### Responsive Breakpoints
- **1024px**: Reduce hero title to 3rem, services grid to 2 columns
- **768px**: Single column layouts, centered navigation, stacked hero/about

### Hover & Interaction States
- **Links**: Subtle underline animation (`width: 0` → `100%`)
- **Cards**: Combine `transform: translateY(-5px)`, border, and shadow
- **Images**: `transform: scale(1.05)` with easing for smooth zoom

### Form Styling (Contact Section)
Minimal, editorial approach:
- No borders except `border-bottom: 1px solid var(--border-color)`
- Focus state changes border color to `var(--accent-color)`
- `background: transparent` for integrated feel

### Typography Conventions
- Page title: uppercase, light weight (300), tight `letter-spacing: -0.02em`
- Section headers: `font-size: 2.5rem`, `letter-spacing: 2px`, uppercase
- Labels: `font-size: 0.85rem`, uppercase, `letter-spacing: 2px`, muted color

## Modification Guidelines

### Adding New Sections
1. Add semantic HTML section with unique `id` (e.g., `<section id="new-section">`)
2. Add CSS rule for `#new-section` with `padding: var(--section-padding)`
3. Use `.container` wrapper for content width constraints
4. Follow existing grid patterns (`.services-grid` style) if displaying multiple items
5. Update navigation `.nav-links` with anchor link to new section

### Updating Colors
Modify only the CSS variables in `:root`:
```css
:root {
    --accent-color: #4A301B;  /* Change here once, updates everywhere */
}
```

### Adding Images
- Use `background-image: url()` for hero/sections or `<img>` tags for inline content
- Placeholder images sourced from Unsplash (can be replaced)
- Use `object-fit: cover` and `aspect-ratio` for consistent sizing

### Mobile Responsiveness
Update relevant media queries at end of CSS (768px and 1024px breakpoints). Maintain stacked single-column layout and center-aligned text on mobile.

## Common Tasks

### Task: Change Hero Background Image
Edit the `.hero` rule:
```css
.hero {
    background-image: url('new-image-url.jpg');
}
```

### Task: Update Service Pricing
Locate the relevant `.service-card` in HTML and modify the `.service-price` div content.

### Task: Add Portfolio Items
Duplicate a `.portfolio-item` div block and update the image `src` and `alt` text.

### Task: Modify Contact Form Fields
Add/remove `.form-group` divs with `<label>`, `<input>` or `<textarea>` elements following existing styling.

## External Dependencies
- **Google Fonts**: Montserrat (loaded via CDN link in `<head>`)
- **Images**: Unsplash URLs as placeholders (replace in production)

No build tools, no npm packages, no JavaScript framework—plain HTML + CSS.

## No Build Process
This project requires **no compilation, bundling, or build step**. Open `index.html` directly in a browser or deploy to any static host (Netlify, Vercel, GitHub Pages).
