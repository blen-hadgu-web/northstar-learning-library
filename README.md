# Northstar Learning Library

Northstar Learning Library is a progressive capstone project by **Blen Hadgu**. It uses **Archetype C: The Curation & Discovery Portal** to create an accessible interface for finding, filtering, comparing, and saving technology-learning resources.

## Live Milestones

- Project landing page: `https://blen-hadgu-web.github.io/northstar-learning-library/`
- Week 02 design tokens: `https://blen-hadgu-web.github.io/northstar-learning-library/week02/`
- Week 03 structural frame: `https://blen-hadgu-web.github.io/northstar-learning-library/week03/`
- Week 04 asymmetric grid: `https://blen-hadgu-web.github.io/northstar-learning-library/week04/`
- Week 05 CSS architecture: `https://blen-hadgu-web.github.io/northstar-learning-library/week05/`
- Week 06 container queries: `https://blen-hadgu-web.github.io/northstar-learning-library/week06/`
- Week 07 micro-interactions: `https://blen-hadgu-web.github.io/northstar-learning-library/week07/`

## Public Repository

`https://github.com/blen-hadgu-web/northstar-learning-library`

## Project Structure

```text
northstar-learning-library/
├── index.html
├── README.md
├── week02/
│   ├── index.html
│   └── styles.css
├── week03/
│   ├── index.html
│   ├── styles.css
│   ├── TESTING-CHECKLIST.md
├── week04/
│   ├── assets/
│   │   ├── accessible-web.svg
│   │   ├── algorithms.svg
│   │   ├── css-layout.svg
│   │   ├── git-workflow.svg
│   │   ├── javascript.svg
│   │   └── ux-research.svg
│   ├── index.html
│   ├── styles.css
│   ├── TESTING-CHECKLIST.md
├── week05/
│   ├── assets/
│   │   ├── accessible-web.svg
│   │   ├── algorithms.svg
│   │   ├── css-layout.svg
│   │   ├── git-workflow.svg
│   │   ├── javascript.svg
│   │   └── ux-research.svg
│   ├── index.html
│   ├── styles.css
│   ├── ARCHITECTURE-AUDIT.txt
│   ├── TESTING-CHECKLIST.md
├── week06/
│   ├── assets/
│   │   ├── accessible-web.svg
│   │   ├── algorithms.svg
│   │   ├── css-layout.svg
│   │   ├── git-workflow.svg
│   │   ├── javascript.svg
│   │   └── ux-research.svg
│   ├── index.html
│   ├── styles.css
│   ├── ARCHITECTURE-AUDIT.txt
│   ├── CONTAINER-AUDIT.txt
│   ├── TESTING-CHECKLIST.md
└── week07/
    ├── assets/
    │   ├── accessible-web.svg
    │   ├── algorithms.svg
    │   ├── css-layout.svg
    │   ├── git-workflow.svg
    │   ├── javascript.svg
    │   └── ux-research.svg
    ├── index.html
    ├── styles.css
    ├── ARCHITECTURE-AUDIT.txt
    ├── INTERACTION-AUDIT.txt
    └── TESTING-CHECKLIST.md
```

Week 07 duplicates the Week 06 foundation into a new directory. All historical milestone directories (Weeks 02 through 06) remain unmodified.

## Run Locally

No package manager, CSS preprocessor, JavaScript framework, or build command is required.

1. Download or clone the repository.
2. Open the root `index.html`.
3. Use the milestone links to open Week 06 or Week 07 for comparison.

VS Code Live Server may also be used.

# Week 02: Global Token Blueprint

Week 02 established:

- Light and dark OKLCH color variables
- WCAG-aware foreground and background pairs
- Fluid typography with `clamp()`
- Relative spacing constants
- Reusable surfaces, borders, focus, radius, and shadow tokens
- Cascade layers

Shared variables reused across all milestones include:

```css
--color-primary
--color-secondary
--color-background
--color-surface
--color-surface-raised
--color-text
--color-text-muted
--color-border
--color-focus

--space-xs
--space-sm
--space-md
--space-lg
--space-xl
```

# Week 03: Structural Frames & Semantic Navigation

Week 03 established:

- Persistent header
- Semantic navigation
- Left filter `aside`
- Flexible catalog `main`
- Footer
- Full dynamic-viewport frame
- Responsive stacking
- `minmax()` protection for the sidebar and main track

# Week 04: The Asymmetric Responsive Grid Hub

Week 04 established:

- Six curated resource cards using SVG illustrations
- Featured hero card spanning 2 columns and 2 rows on desktop
- Dense auto-placement with `grid-auto-flow: dense`
- Fractional track scaling with `minmax(0, 1fr)`

# Week 05: Native Nesting & `@layer` Architecture

Week 05 established:

- Strict four-layer cascade architecture (`reset`, `base`, `layout`, `components`)
- Native CSS nesting using `&` parent selectors
- Zero CSS build step or preprocessors required
- Visual continuity preservation verified with Chromium pixel audits

# Week 06: Container Queries & Component-Level Fluidity

Week 06 established:

- Container contexts established on parent card slots via `container-type: inline-size`
- Component queries (`@container (min-width: 480px)`) driving horizontal card layout
- Complete elimination of viewport `@media` queries on card internals
- Relative container units (`cqi`) for fluid card typography, padding, and micro-spacing
- The Placement Test verifying context-aware card styling in narrow sidebar vs wide catalog track

# Week 07: Micro-Interactions & Scroll-Driven Enhancements

Week 07 integrates polished, hardware-accelerated micro-interactions and native CSS scroll-driven animations without any external JavaScript animation libraries.

## 1. High-Performance Micro-Interactions

All interactive elements feature hardware-accelerated transitions that animate only compositor-friendly properties (`transform`, `opacity`, `background-color`, `box-shadow`) to avoid layout recalculations and repaint penalties:

- **Resource Card Lift & Elevation:**
  Hovering or focusing inside `.resource-card` elevates the card (`translateY(-0.35rem) scale(1.012)`) with smooth shadow expansion (`--shadow-hover`).
- **Media Scale Interaction:**
  The card illustration gently zooms (`transform: scale(1.05)`) within its clipping boundary.
- **Action Link Glide:**
  Hovering over card links slides the arrow icon (`transform: translateX(0.4rem)`).
- **Tactile Button Feedback:**
  Buttons deliver instant active tactile feedback on click/press (`transform: translateY(0.0625rem) scale(0.97)`).
- **Navigation Item Lift:**
  Header and footer navigation links produce smooth background color shifts and micro-lifts (`translateY(-0.0625rem)`).
- **Interactive Form Inputs:**
  Filter checkboxes scale on hover (`scale(1.1)`) and filter labels smoothly highlight and slide.

```css
.resource-card {
  transition: transform 0.25s cubic-bezier(0.2, 0, 0, 1),
              box-shadow 0.25s ease,
              border-color 0.25s ease;
  will-change: transform, box-shadow;

  &:hover,
  &:focus-within {
    transform: translateY(-0.35rem) scale(1.012);
    border-color: color-mix(in oklch, var(--color-primary) 45%, var(--color-border));
    box-shadow: var(--shadow-hover);

    .resource-card__media img {
      transform: scale(1.05);
    }

    .resource-card__link span {
      transform: translateX(0.4rem);
    }
  }
}
```

## 2. Active and Focus States

Every interactive element incorporates an accessible, high-contrast `:focus-visible` ring utilizing `--color-focus`. Micro-interactions trigger equally on keyboard focus (`:focus-within` on cards) as on mouse hover, ensuring full parity for keyboard navigators.

## 3. Modern CSS Scroll-Driven Animations

Week 07 implements two native CSS scroll-driven animation systems using the web platform's `scroll()` and `view()` animation timelines:

### Option A: Global Reading Progress Indicator

A slim top progress indicator (`.scroll-progress-bar`) fills horizontally as the user scrolls through the page:

```css
.scroll-progress-bar {
  position: fixed;
  inset-block-start: 0;
  inset-inline-start: 0;
  inline-size: 100%;
  block-size: 0.25rem;
  background: linear-gradient(
    90deg,
    var(--color-primary),
    var(--color-secondary),
    var(--color-focus)
  );
  transform-origin: 0 50%;
  z-index: 1000;
  pointer-events: none;
}

@supports (animation-timeline: scroll()) {
  .scroll-progress-bar {
    animation: scale-progress auto linear both;
    animation-timeline: scroll(root);
  }
}

@keyframes scale-progress {
  from { transform: scaleX(0); }
  to { transform: scaleX(1); }
}
```

### Option B: Scroll-Reveal Elements

Catalog cards (`.catalog-item`), the sidebar spotlight card, and section headings smoothly fade in and slide upward as they cross into the viewport:

```css
@keyframes reveal-card {
  from {
    opacity: 0;
    transform: translateY(1.75rem) scale(0.96);
  }
  to {
    opacity: 1;
    transform: translateY(0) scale(1);
  }
}

@supports (animation-timeline: view()) {
  .catalog-item {
    animation: reveal-card auto linear both;
    animation-timeline: view();
    animation-range: entry 10% cover 35%;
  }

  .sidebar-spotlight {
    animation: reveal-card auto linear both;
    animation-timeline: view();
    animation-range: entry 5% cover 30%;
  }
}
```

## 4. Accessibility & Reduced-Motion (`prefers-reduced-motion`)

To protect users with vestibular disorders or motion sensitivities, all animations and transitions are comprehensively disabled when reduced-motion is requested at the OS level:

```css
@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    animation-delay: -1ms !important;
    animation-duration: 1ms !important;
    animation-iteration-count: 1 !important;
    background-attachment: initial !important;
    scroll-behavior: auto !important;
    transition-duration: 0s !important;
    transition-delay: 0s !important;
    transform: none !important;
  }

  .scroll-progress-bar {
    display: none !important;
  }
}
```

## AI Tool and Prompts

**AI tool:** ChatGPT

### Prompt 1: Designing High-Performance Hover States

> I have a card component called `.resource-card`. I want to design a subtle micro-interaction when a user hovers or tabs onto it. The card should scale up very slightly (1.012x), lift upward, and drop a clean shadow. Show me how to write this transition using only CSS transforms and opacity so that it is hardware-accelerated. Also, include an accessible `:focus-visible` ring.

### Prompt 2: Building CSS Scroll-Driven View Animations

> I want to create a scroll-reveal animation for my layout cards using native modern CSS scroll-driven animations. As each card enters the viewport, it should fade from opacity 0 to 1 and slide up by 25px. Can you write the CSS using `animation-timeline: view()` and explain how the view-timeline bounds are determined?

## Human Audit

### DevTools Rendering & Paint Flashing

1. Open Chrome DevTools > More tools > **Rendering**.
2. Check **Paint flashing**.
3. Hover and focus on `.resource-card`, buttons, and links.
4. Confirmed: Only local composited layers repaint; zero full-page layout thrashing or layout shifts occur.

### Reduced-Motion Verification

- Turned on OS-level "Reduce Motion".
- Refreshed the page: all animations and transitions instantly disabled, progress bar hidden, and layout remained 100% accessible and static.

## Testing

- Week 07 interaction audit: [`week07/INTERACTION-AUDIT.txt`](week07/INTERACTION-AUDIT.txt)
- Week 07 architecture audit: [`week07/ARCHITECTURE-AUDIT.txt`](week07/ARCHITECTURE-AUDIT.txt)
- Week 07 checklist: [`week07/TESTING-CHECKLIST.md`](week07/TESTING-CHECKLIST.md)

## Deployment

GitHub Pages is configured to deploy from:

```text
Branch: main
Folder: /(root)
```

Opening all milestone URLs in an Incognito/Private window verifies the public archive:
- Landing page: `/`
- Week 02: `/week02/`
- Week 03: `/week03/`
- Week 04: `/week04/`
- Week 05: `/week05/`
- Week 06: `/week06/`
- Week 07: `/week07/`

## Author

**Blen Hadgu**

GitHub ID: `blenhadgu`
