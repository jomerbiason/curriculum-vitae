# Retro Pixel Portfolio

🔗 **Live Site:** [jomerbiason.github.io/curriculum-vitae](https://jomerbiason.github.io/curriculum-vitae/)

An interactive CV/portfolio site built with vanilla HTML, CSS, and JavaScript — no frameworks, no build step.

Instead of a static resume page, this project uses a retro pixel-art theme (day/night sky, parallax canvas scenery, animated clouds) to present the same information a traditional CV would: experience, education, skills, projects, certifications, and contact info.

---

# Architecture

```
Browser
│
├── HTML
│     ├── Semantic Layout
│     ├── Navigation
│     ├── Sections
│     ├── Accessibility
│     └── SEO / Social Metadata
│
├── CSS
│     ├── Theme Engine (day/night, CSS variables)
│     ├── Pixel UI
│     ├── Responsive Layout
│     ├── Animations
│     ├── Component Styling
│     └── Reduced-Motion Support
│
└── JavaScript
      ├── Theme Controller
      ├── Canvas Renderer (stars, wind/mist, sky scene)
      ├── Navigation Observer
      └── Contact Obfuscation
```

---

# Project Goals

- Demonstrate front-end development without frameworks.
- Present a resume in a memorable, interactive way without sacrificing scannability.
- Keep the entire experience inside a single HTML file with no external JS dependencies.

---

# Technology Stack

| Technology | Purpose |
|------------|---------|
| HTML5 | Semantic document structure |
| CSS3 | Component styling and animations |
| CSS Variables | Runtime theme switching |
| Canvas API | Rendering the animated sky/cloud/star scenery |
| JavaScript ES6 | Application logic |
| LocalStorage | Theme preference persistence |
| IntersectionObserver | Active navigation highlighting and panel fade-in |
| requestAnimationFrame | Smooth canvas rendering loops |
| matchMedia | Reduced-motion detection |
| Open Graph / JSON-LD | Link previews and structured data for search engines |
| Web App Manifest | Home-screen installability |

---

# HTML Structure

```
index.html
│
├── Hero
├── Career Objective
├── Education
├── Experience
├── Skills
├── Projects
├── Certifications
├── References
├── Contact
│
├── Sky Scene Canvas (clouds, sun/moon)
├── Wind/Mist Canvas
├── World Canvas (parallax scenery)
└── Navigation
```

Each resume section is isolated in a semantic `<section>` for accessibility and easier maintenance.

---

# Theme System

The portfolio supports automatic day and night themes.

- CSS Custom Properties drive every color
- A JavaScript controller sets `data-theme` on `<html>`
- The choice is persisted in LocalStorage once the visitor manually toggles it
- Falls back to automatic switching based on local time until a manual choice is made

```
:root → CSS Variables → JS sets data-theme → interface recolors instantly
```

---

# Canvas Rendering

Three independent canvas layers create the atmosphere.

## Stars Canvas
Renders animated twinkling stars during night mode.

## Wind / Mist Canvas
A lightweight particle system (position, velocity, opacity, lifetime) produces drifting fog without video or GIF assets.

## World / Sky Canvas
Pixel-art clouds, a sun/moon with day/night rendering, a hot-air balloon, and an aerial banner plane drift across the scene — purely canvas-drawn, no image assets.

All three respect `prefers-reduced-motion` and skip initialization entirely when it's enabled.

---

# Navigation System

Section highlighting in the nav bar is powered by the Intersection Observer API instead of scroll-position calculations, for lower CPU usage and a smoother active-state transition.

---

# Animation Engine

Built entirely on native browser APIs: `requestAnimationFrame`, CSS keyframes/transitions, and transform/opacity interpolation. No animation libraries.

Every canvas loop checks `prefers-reduced-motion` before starting and skips initialization for visitors who have that preference enabled; decorative CSS keyframe animations (fog drift, badge blink, panel fade-in, road scroll) are disabled via the same media query.

---

# Performance Considerations

- CSS Variables instead of duplicated per-theme stylesheets
- `requestAnimationFrame` for all canvas rendering
- Intersection Observer instead of scroll listeners
- Debounced resize handling (150ms) across all canvas layers
- `prefers-reduced-motion` short-circuits animation loops before they start

---

# Responsive Design

Handled entirely through CSS media queries: navigation sizing, card/grid layout changes, typography scaling, and mobile spacing adjustments.

---

# Accessibility

- Semantic HTML and ARIA labels
- Keyboard-friendly navigation
- Lazy-loaded certificate images with descriptive alt attributes
- `prefers-reduced-motion` support that disables decorative animation
- Keyboard-operable contact reveal controls (`role="button"`, `tabindex`, Enter/Space activation)

---

# Privacy & Contact Protection

Reference contact emails are not present as plain text in the page source. Each reference's email is stored as separated `data-user` / `data-domain` attributes and is only assembled into a clickable `mailto:` link after an explicit click or keyboard activation, reducing exposure to automated email harvesters while keeping the information one tap away for real visitors.

---

# SEO & Social Sharing

- Open Graph tags (`og:title`, `og:description`, `og:image`, `og:url`)
- Twitter Card tags
- JSON-LD `Person` structured data (name, job title, alumni info, social links)
- `robots.txt` and `sitemap.xml` for crawler discovery
- `theme-color` meta tag matching the site's pixel-header palette

---

# Progressive Web App Support

A `manifest.json` is linked from the document head, allowing the portfolio to be added to a mobile home screen with a standalone display mode, themed splash color, and app icon.

---

# Error Handling

A themed `404.html` page is served automatically by GitHub Pages for any unmatched route, styled consistently with the site's pixel/retro aesthetic and linking back to the live portfolio.

---

# Folder Structure

```
/
│
├── index.html
├── 404.html
├── robots.txt
├── sitemap.xml
├── manifest.json
├── certs/
├── README.md
└── JomerAntoniegoBiason_CurriculumVitae.pdf
```

---

# Future Improvements

- Automated Lighthouse/accessibility CI checks
- TypeScript migration
- Full offline PWA support (service worker + asset caching)
