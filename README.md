# Interactive RPG Portfolio

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
│     └── Accessibility
│
├── CSS
│     ├── Theme Engine
│     ├── Pixel UI
│     ├── Responsive Layout
│     ├── Animations
│     └── Component Styling
│
└── JavaScript
      ├── Theme Controller
      ├── Canvas Renderer
      ├── Particle Engine
      ├── Navigation Observer
      ├── RPG Minigame
      ├── State Management
      └── UI Effects
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

Three independent canvas layers are used.

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

---

# Responsive Design

Responsive behavior is handled entirely through CSS media queries.

Adaptations include

- Navigation resizing
- Card layout changes
- Typography scaling
- Grid restructuring
- Mobile spacing adjustments

---

# Accessibility

The project includes

- Semantic HTML
- ARIA labels
- Keyboard-friendly navigation
- Responsive scaling
- Lazy loaded images
- Descriptive alt attributes

---

# Folder Structure

```
/
│
├── index.html
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
- PWA support
- TypeScript migration
