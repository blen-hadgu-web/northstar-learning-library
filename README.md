# Northstar Learning Library

Northstar Learning Library is a multi-week capstone project by **Blen Hadgu**. It uses **Archetype C: The Curation & Discovery Portal** to create a future web application for finding, filtering, comparing, and saving accessible technology-learning resources.

## Live Milestones

- Project landing page: `https://blen-hadgu-web.github.io/northstar-learning-library/`
- Week 02 design tokens: `https://blen-hadgu-web.github.io/northstar-learning-library/week02/`
- Week 03 structural frame: `https://blen-hadgu-web.github.io/northstar-learning-library/week03/`

## Public Repository

`https://github.com/blen-hadgu-web/northstar-learning-library`

## Selected Archetype

**Archetype C: The Curation & Discovery Portal**

The planned application includes:

- A persistent search and navigation header
- A filter sidebar
- A responsive catalog area
- Resource-card grids
- Comparison and saved-resource tools

## Project Structure

```text
northstar-learning-library/
├── index.html
├── README.md
├── SUBMISSION.txt
├── SUBMISSION-WEEK03.txt
├── week02/
│   ├── index.html
│   └── styles.css
└── week03/
    ├── index.html
    ├── styles.css
    ├── TESTING-CHECKLIST.md
    └── VIDEO-SCRIPT.md
```

Each milestone remains in its own directory. Week 03 was added without changing either Week 02 file.

## Run Locally

No package manager, framework, JavaScript, or build process is required.

1. Download or clone the repository.
2. Open the root `index.html` in a browser.
3. Use the milestone links to open Week 02 or Week 03.

VS Code Live Server may also be used.

# Week 02: Global Token Blueprint

Week 02 established:

- Light and dark OKLCH color variables
- WCAG AA background/text pairs
- Fluid typography using `clamp()`
- Relative spacing variables
- Cascade layers
- Manual zoom and responsiveness checks

Important shared variables include:

```css
--color-primary
--color-secondary
--color-background
--color-surface
--color-text
--color-border
--color-focus

--space-xs
--space-sm
--space-md
--space-lg
--space-xl
```

# Week 03: Structural Frames & Semantic Navigation

Week 03 adds the physical application skeleton while preserving Week 02.

## Semantic structure

The Week 03 page uses:

- `<header>` for the global brand and control banner
- `<nav>` for primary, utility, catalog, and secondary navigation
- `<aside>` for the filter rail
- `<main>` for the catalog workspace
- `<footer>` for milestone status and secondary links
- `<section>`, `<ol>`, and `<article>` for the reserved catalog structure

The Week 03 HTML contains no `<div>` elements.

## Structural grid

Desktop layout:

```css
.portal-shell {
  display: grid;
  grid-template:
    "header header" auto
    "filters catalog" minmax(0, 1fr)
    "footer footer" auto
    / minmax(14rem, 18rem) minmax(0, 1fr);
  block-size: 100dvh;
}
```

The filter rail receives a usable width range. The catalog uses `minmax(0, 1fr)` so it may shrink below its min-content size instead of producing horizontal overflow.

At viewports below 52rem, the frame becomes a single column:

```css
.portal-shell {
  grid-template:
    "header" auto
    "filters" auto
    "catalog" minmax(0, 1fr)
    "footer" auto
    / minmax(0, 1fr);
}
```

## Why the sidebar previously could collapse or overflow

In Grid, an `auto` minimum or a track based only on flexible fractions may interact with an item's min-content size. A long child may prevent the main track from shrinking, while a loosely defined sidebar may become too narrow or push the grid wider than the viewport.

The audited correction is:

```css
grid-template-columns: minmax(14rem, 18rem) minmax(0, 1fr);
```

- `minmax(14rem, 18rem)` protects the filter rail from collapsing on desktop.
- `minmax(0, 1fr)` explicitly allows the catalog track to shrink.
- A narrow-screen layout stacks the rail and catalog before the two-column minimum becomes unsafe.
- Child elements use `min-inline-size: 0` where necessary.

## Token integration

Week 03 copied the Week 02 stylesheet into `/week03/styles.css` and added a separate `week03-frame` layer. Structural components use the existing variables:

```css
padding: var(--space-md);
gap: var(--space-md);
background: var(--color-surface);
color: var(--color-text);
border-color: var(--color-border);
outline-color: var(--color-focus);
```

## AI Tool and Prompts

**AI tool:** ChatGPT

### Prompt 1: Drafting semantic layout scaffolding

> I am building an Archetype C Curation & Discovery Portal for my Northstar Learning Library capstone project. Write the semantic HTML5 layout wrapper utilizing `<header>`, `<nav>`, `<main>`, `<aside>`, and `<footer>`. Then write the CSS Grid rules needed to position these zones so the layout occupies exactly 100% of the dynamic viewport height. Use low-specificity CSS class selectors and bind padding, gaps, borders, focus indicators, surfaces, and background colors to my existing Week 02 CSS variables. Keep the page focused on structural zones; do not add final catalog content or lorem ipsum.

### Prompt 2: Grid frame debugging

> My aside element is collapsing to zero width when the screen gets narrow, and it is causing a horizontal scrollbar. Can you explain why this is happening within the CSS Grid formatting context and how I can set a responsive minimum width constraint on my sidebar using `minmax()`?
>
> The draft uses a left filter `<aside>` and a flexible catalog `<main>`. Correct the grid with a bounded sidebar track, a shrinkable main track using `minmax(0, 1fr)`, `min-inline-size: 0` where required, and a narrow-screen stacking strategy.

## Human Audit

### No div-soup

- The outer structure is entirely semantic.
- There are no `<div>` elements in `week03/index.html`.
- Reserved catalog positions use list items and articles with visually hidden headings.

### Keyboard focus

- The skip link is first.
- Navigation links follow in a logical source order.
- Filter controls follow navigation.
- High-contrast focus rings reuse `--color-focus`.

### Viewport resiliency

The frame is intended to be tested at:

- 320px
- 375px
- 768px
- 1024px
- 1440px
- 2560px

The sidebar and catalog stack before their desktop minimums can cause overflow. Catalog slots use an auto-fitting grid with bounded minimums.

## Testing and Video

- Week 03 checklist: [`week03/TESTING-CHECKLIST.md`](week03/TESTING-CHECKLIST.md)
- Week 03 video script: [`week03/VIDEO-SCRIPT.md`](week03/VIDEO-SCRIPT.md)

The separate “Web Project Testing & Quality Assurance Guide” was not included in the supplied assignment text. The included checklist covers all visible requirements and common semantic, keyboard, responsive, and production tests.

## Deployment

GitHub Pages should deploy from:

```text
Branch: main
Folder: /(root)
```

Opening the live Week 03 link in an Incognito/Private window verifies that the public deployment is accessible.

## Author

**Blen Hadgu**

GitHub ID: `blenhadgu`
