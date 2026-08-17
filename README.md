# Northstar Learning Library

Northstar Learning Library is a progressive capstone project by **Blen Hadgu**. It uses **Archetype C: The Curation & Discovery Portal** to create an accessible interface for finding, filtering, comparing, and saving technology-learning resources.

## Live Milestones

- Project landing page: `https://blen-hadgu-web.github.io/northstar-learning-library/`
- Week 02 design tokens: `https://blen-hadgu-web.github.io/northstar-learning-library/week02/`
- Week 03 structural frame: `https://blen-hadgu-web.github.io/northstar-learning-library/week03/`
- Week 04 asymmetric grid: `https://blen-hadgu-web.github.io/northstar-learning-library/week04/`
- Week 05 CSS architecture: `https://blen-hadgu-web.github.io/northstar-learning-library/week05/`
- Week 06 container queries: `https://blen-hadgu-web.github.io/northstar-learning-library/week06/`

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
└── week06/
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
    ├── CONTAINER-AUDIT.txt
    ├── TESTING-CHECKLIST.md
```

Week 06 duplicates the Week 05 foundation into a new directory. All previous milestone directories (Weeks 02 through 05) remain unmodified.

## Run Locally

No package manager, CSS preprocessor, JavaScript framework, or build command is required.

1. Download or clone the repository.
2. Open the root `index.html`.
3. Use the milestone links to open Week 05 or Week 06 for comparison.

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

Week 06 transitions the project from viewport-based responsiveness (`@media`) to component-level fluidity using CSS Container Queries (`@container`). Components now style themselves based on the inline width of their direct parent container.

## 1. Establishing Container Contexts

In `week06/styles.css` (inside `@layer components`), container contexts are defined on parent wrappers:

```css
.catalog-item,
.sidebar-card-slot {
  container-type: inline-size;
  min-inline-size: 0;
  inline-size: 100%;
}
```

By assigning `container-type: inline-size`, child elements inside `.catalog-item` and `.sidebar-card-slot` evaluate their container queries relative to that wrapper rather than the entire browser viewport.

## 2. Component-Level Container Queries (`@container`)

Card components default to a compact, vertically stacked format suitable for narrow spaces (< 480px). When their parent container reaches 480px or wider, a container query transforms the layout into a horizontal side-by-side arrangement:

```css
/* Base / Narrow Default Layout (< 480px) */
.resource-card {
  display: grid;
  grid-template-columns: minmax(0, 1fr);
  grid-template-rows: auto minmax(0, 1fr);
  block-size: 100%;
  min-inline-size: 0;
  ...
}

/* Wide Container Transformation (>= 480px) */
@container (min-width: 480px) {
  .resource-card {
    grid-template-columns: minmax(0, 1fr) minmax(0, 1.15fr);
    grid-template-rows: minmax(0, 1fr);

    .resource-card__media {
      min-block-size: 100%;
      aspect-ratio: auto;
    }

    .resource-card__content {
      align-content: center;
      padding: clamp(var(--space-md), 3cqi, var(--space-lg));
      gap: clamp(var(--space-sm), 2cqi, var(--space-md));
    }

    .resource-card__header h3 {
      font-size: clamp(1.2rem, 1rem + 1.5cqi, 1.55rem);
    }
  }

  .resource-card.resource-card--hero {
    grid-template-columns: minmax(0, 1.05fr) minmax(0, 0.95fr);

    .resource-card__content {
      padding: clamp(var(--space-md), 4cqi, var(--space-xl));
    }

    .resource-card__header h3 {
      font-size: clamp(1.35rem, 1.1rem + 2cqi, 1.85rem);
    }
  }
}
```

## 3. Elimination of Media Query Dependencies for Cards

In Week 05, internal card layouts relied on viewport media queries (`@media (max-width: 70rem)` and `@media (max-width: 44rem)`). In Week 06, **all viewport media queries controlling internal card structure were removed**.

Page-level media queries now only control macro shell geometry (`.portal-shell`, `.portal-header`, and `.catalog-grid` track count). When the macro grid rearranges from 3 tracks to 2 or 1, the card container sizes change and each card automatically responds through `@container`.

## 4. Relative Container Units (`cqi`)

Week 06 incorporates `cqi` (container query inline size) units for fluid internal spacing, font scaling, and micro-interactions:

- **Fluid heading clamp:** `font-size: clamp(1.05rem, 0.95rem + 1.8cqi, 1.35rem);`
- **Fluid card content padding:** `padding: clamp(var(--space-sm), 4cqi, var(--space-md));`
- **Fluid meta gap:** `gap: var(--space-xs) clamp(var(--space-sm), 2cqi, var(--space-md));`
- **Fluid badge sizing:** `font-size: clamp(0.72rem, 0.68rem + 0.4cqi, 0.82rem);`

## 5. The Placement Test

To verify true context-awareness, `week06/index.html` implements the Placement Test:

1. **Sidebar Context (`<aside class="filter-rail">`):** A `.resource-card` is placed in `.sidebar-card-slot` (~250px wide). Because its container is below 480px, it automatically renders as a compact, vertically stacked reference card.
2. **Main Catalog Context (`<main class="catalog-workspace">`):** The exact same `.resource-card` component is placed in the featured 2-column grid slot (> 500px wide). Because its container exceeds 480px, it automatically renders as an expansive horizontal card.

Both cards share identical HTML markup and classes without custom layout overrides.

## AI Tool and Prompts

**AI tool:** ChatGPT

### Prompt 1: Writing Container Queries

> I have a reusable card element called `.resource-card` containing an image and some text. I want to convert this card's styling to use CSS Container Queries instead of Media Queries. If its parent element is wider than 450px, the card should display horizontally. If its parent is narrower, it should stack vertically. Can you write the HTML structure and the nested CSS using `@container`?

### Prompt 2: Refactoring Layouts for Container Queries

> In my project, I have cards in my main asymmetric grid and cards in my sidebar aside. They currently look messy because the sidebar cards are being squished. Can you help me set `container-type: inline-size` on the parent elements of these card slots and show me how to refactor the cards to self-adjust perfectly?

## Human Audit

### DevTools Container Query Inspector

1. Open DevTools in Chrome, Edge, Firefox, or Safari.
2. Inspect `.catalog-item` and `.sidebar-card-slot` to verify active `container` badges.
3. Inspect `.resource-card` and verify `@container (min-width: 480px)` rules in the Styles panel.
4. Resize the browser window; confirm that cards smoothly switch layout states based on parent track dimensions.

### Multi-Context Comparison

- Inspect the sidebar card: confirmed vertically stacked layout.
- Inspect the main catalog hero card: confirmed horizontal side-by-side layout.
- No horizontal overflow or clipping occurs across 320px, 375px, 768px, 1024px, 1440px, and 2560px viewports.

## Testing and Video

- Week 06 container audit: [`week06/CONTAINER-AUDIT.txt`](week06/CONTAINER-AUDIT.txt)
- Week 06 architecture audit: [`week06/ARCHITECTURE-AUDIT.txt`](week06/ARCHITECTURE-AUDIT.txt)
- Week 06 checklist: [`week06/TESTING-CHECKLIST.md`](week06/TESTING-CHECKLIST.md)
- Week 06 video script: [`week06/VIDEO-SCRIPT.md`](week06/VIDEO-SCRIPT.md)

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

## Author

**Blen Hadgu**

GitHub ID: `blenhadgu`
