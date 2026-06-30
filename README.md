# Interactive RPG Portfolio

🔗 **Live Site:** [jomerbiason.github.io/curriculum-vitae](https://jomerbiason.github.io/curriculum-vitae/)

An interactive portfolio website built using vanilla HTML, CSS, and JavaScript.

Unlike a traditional portfolio, this project combines front-end engineering techniques with game-inspired UI/UX, procedural canvas rendering, and lightweight animation systems without relying on external frameworks.

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
│     ├── Theme Engine
│     ├── Pixel UI
│     ├── Responsive Layout
│     ├── Animations
│     ├── Component Styling
│     └── Reduced-Motion Support
│
└── JavaScript
      ├── Theme Controller
      ├── Canvas Renderer
      ├── Particle Engine
      ├── Navigation Observer
      ├── RPG Minigame
      ├── State Management
      ├── UI Effects
      └── Contact Obfuscation
```

---

# Project Goals

The project was designed around four objectives.

- Demonstrate modern frontend development without frameworks.
- Showcase interactive UI design.
- Build an animated portfolio with minimal dependencies.
- Keep the entire project inside a single HTML file.

---

# Technology Stack

| Technology | Purpose |
|------------|---------|
| HTML5 | Semantic document structure |
| CSS3 | Component styling and animations |
| CSS Variables | Runtime theme switching |
| Canvas API | Rendering sprites, particles and game objects |
| JavaScript ES6 | Application logic |
| LocalStorage | Theme persistence and high score storage |
| IntersectionObserver | Active navigation and lazy animations |
| requestAnimationFrame | Smooth rendering loop |
| matchMedia | Reduced-motion detection |
| Open Graph / JSON-LD | Link previews and structured data for search engines |
| Web App Manifest | Home-screen installability |

---

# HTML Structure

The application is divided into reusable sections.

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
├── Game Canvas
├── Wind Canvas
├── Stars Canvas
└── Navigation
```

Each section is isolated using semantic `<section>` elements for accessibility and easier maintenance.

---

# Theme System

The portfolio supports automatic day and night themes.

Implementation:

- CSS Custom Properties
- JavaScript theme controller
- LocalStorage persistence
- Automatic switching based on local time

```
:root
↓

CSS Variables

↓

JavaScript updates data-theme

↓

Entire interface recolors instantly
```

No duplicate stylesheets are required because every color is referenced through CSS variables.

---

# Canvas Rendering

Multiple independent canvas layers are used.

## Stars Canvas

Responsible for rendering animated stars during night mode.

Uses

- requestAnimationFrame
- Random star generation
- Alpha oscillation
- Canvas drawing

---

## Wind Canvas

Creates moving fog and wind.

Features

- Radial gradients
- Particle pooling
- Continuous spawning
- Velocity simulation
- Opacity decay

This produces a lightweight atmospheric effect without using videos or GIFs.

---

## World Canvas

Renders the scrolling background scene — trees, lamp posts, oncoming traffic, the foreground car, and time-of-day creatures (birds and butterflies by day, bats and mist wisps by night).

Features

- Parallax scrolling by depth
- Procedural pixel-art trees with day/night variants
- Stationary "moving" car illusion via scrolling road, streak lines, and spinning wheel spokes
- Spawned oncoming traffic (cars, motorcycles, buses)

---

## Game Canvas

Contains the RPG minigame.

Responsible for

- Character rendering
- Enemy rendering
- Collision detection
- Animation states
- Combat
- Score system

Sprites are rendered programmatically from pixel arrays rather than image assets.

---

# Sprite Engine

Instead of PNG sprite sheets, every sprite is defined as a 16×16 matrix.

Example

```
[
0,0,2,2,2,
0,2,1,1,2,
...
]
```

Each number maps to a color palette.

Advantages

- No image downloads
- Easy recoloring
- Small project size
- Fully customizable

---

# Navigation System

Navigation highlighting is powered by the Intersection Observer API.

Benefits

- Better performance than scroll events
- Minimal CPU usage
- Automatic active state
- Smooth user experience

---

# Animation Engine

Animations use native browser APIs.

Primary techniques include

- requestAnimationFrame
- CSS Keyframes
- CSS Transitions
- Transform animations
- Opacity interpolation

No animation libraries are used.

All canvas-driven animation loops check `prefers-reduced-motion` on load and skip initialization entirely for visitors who have that preference enabled, in addition to disabling CSS keyframe animations (fog drift, badge blink, panel fade-in, road scroll) via a dedicated media query.

---

# Particle System

The wind effect uses a lightweight particle engine.

Each particle stores

```
Position
Velocity
Opacity
Lifetime
Size
Gradient
```

Every animation frame

```
Move

↓

Fade

↓

Destroy

↓

Respawn
```

This avoids memory leaks while maintaining a constant particle count.

---

# State Management

Application state is maintained using plain JavaScript objects.

Examples

```
Theme

↓

Game Running

↓

Enemy States

↓

Player Health

↓

High Score
```

Persistent values are synchronized with LocalStorage.

---

# Performance Considerations

Several optimizations are included.

- CSS Variables instead of duplicate themes
- requestAnimationFrame rendering
- Intersection Observer
- Canvas rendering
- Minimal DOM updates
- Hardware accelerated transforms
- Local sprite rendering
- No external JavaScript libraries
- Debounced resize handling (150ms) across all canvas layers to avoid redundant re-initialization during window dragging
- `prefers-reduced-motion` short-circuits canvas animation loops before they start, reducing CPU/battery usage for users who opt out of motion

---

# Responsive Design

Responsive behavior is handled entirely through CSS media queries.

Adaptations include

- Navigation resizing
- Card layout changes
- Typography scaling
- Grid restructuring
- Mobile spacing adjustments
- Reduced-motion adaptations for users with vestibular or motion sensitivity

---

# Accessibility

The project includes

- Semantic HTML
- ARIA labels
- Keyboard-friendly navigation
- Responsive scaling
- Lazy loaded images
- Descriptive alt attributes
- `prefers-reduced-motion` support that disables decorative canvas/CSS animation
- Keyboard-operable contact reveal controls (`role="button"`, `tabindex`, Enter/Space activation)

---

# Privacy & Contact Protection

Reference contact emails are not present as plain text in the page source. Each reference's email is stored as separated `data-user` / `data-domain` attributes and is only assembled into a clickable `mailto:` link after an explicit click or keyboard activation, reducing exposure to automated email harvesters while keeping the information one tap away for real visitors.

---

# SEO & Social Sharing

The site includes metadata so links shared on social platforms render as proper preview cards rather than bare URLs, and so search engines can parse the page as a professional profile.

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
├── favicon
└── resume.pdf
```

---

# Future Improvements

- Modular JavaScript architecture
- Web Components
- Asset pipeline
- Sprite editor
- Procedural enemy AI
- Save game system
- Full offline PWA support (service worker + asset caching)
- TypeScript migration
- Automated Lighthouse/accessibility CI checks
