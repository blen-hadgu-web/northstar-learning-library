# Northstar Learning Library

Northstar Learning Library is a progressive capstone project by **Blen Hadgu**. It uses **Archetype C: The Curation & Discovery Portal** to build an accessible interface for finding, filtering, comparing, and saving technology-learning resources.

## Live Milestones

- Project landing page: `https://blen-hadgu-web.github.io/northstar-learning-library/`
- Week 02 design tokens: `https://blen-hadgu-web.github.io/northstar-learning-library/week02/`
- Week 03 structural frame: `https://blen-hadgu-web.github.io/northstar-learning-library/week03/`
- Week 04 asymmetric grid hub: `https://blen-hadgu-web.github.io/northstar-learning-library/week04/`

## Public Repository

`https://github.com/blen-hadgu-web/northstar-learning-library`

## Selected Archetype

**Archetype C: The Curation & Discovery Portal**

The application includes:

- A persistent global header and semantic navigation
- A responsive filter sidebar
- An asymmetric resource-card catalog
- A featured learning path
- Supporting guides, courses, and toolkits
- Future comparison and saved-resource tools

## Project Structure

```text
northstar-learning-library/
├── index.html
├── README.md
├── SUBMISSION.txt
├── SUBMISSION-WEEK03.txt
├── SUBMISSION-WEEK04.txt
├── week02/
│   ├── index.html
│   └── styles.css
├── week03/
│   ├── index.html
│   ├── styles.css
│   ├── TESTING-CHECKLIST.md
│   └── VIDEO-SCRIPT.md
└── week04/
    ├── assets/
    │   ├── accessible-web.svg
    │   ├── algorithms.svg
    │   ├── css-layout.svg
    │   ├── git-workflow.svg
    │   ├── javascript.svg
    │   └── ux-research.svg
    ├── index.html
    ├── styles.css
    ├── TESTING-CHECKLIST.md
    └── VIDEO-SCRIPT.md
```

Every milestone remains at its original URL. Week 04 duplicates the Week 03 foundation into a new folder before adding the resource grid.

## Run Locally

No framework, JavaScript, package manager, or build process is required.

1. Download or clone the repository.
2. Open the root `index.html`.
3. Use the milestone navigation to open Week 02, Week 03, or Week 04.

VS Code Live Server may also be used.

# Week 02: Global Token Blueprint

Week 02 established:

- Light and dark OKLCH color variables
- WCAG-aware foreground and background pairs
- Fluid typography with `clamp()`
- Relative spacing constants
- Reusable surfaces, borders, focus, radius, and shadow tokens
- Cascade layers

Shared variables reused by Week 04 include:

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

Week 04 populates the main catalog with six resource cards.

## Content hierarchy

The first card is the featured learning path:

**Accessible Web Foundations**

It spans two columns and two rows on wide screens. Five supporting cards remain one track each:

1. Git & GitHub Workflow
2. CSS Layout Systems
3. Inclusive UX Research
4. JavaScript Essentials
5. Data Structures & Algorithms

## Grid formula

```css
.catalog-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  grid-auto-flow: dense;
  grid-auto-rows: minmax(12rem, auto);
  gap: var(--space-md);
}

.catalog-item--hero {
  grid-column: span 2;
  grid-row: span 2;
}
```

### Why `minmax(0, 1fr)` matters

A fractional track has an automatic minimum based on its contents unless that minimum is explicitly reduced. `minmax(0, 1fr)` permits the track to shrink below long min-content widths, reducing overflow risk.

### Why dense placement is used

```css
grid-auto-flow: dense;
```

When the number of columns changes, a spanning item may create an earlier available grid position. Dense placement allows a later supporting card to fill that position instead of leaving a large internal hole.

Dense placement affects visual placement only. The semantic and keyboard reading order remains the HTML source order.

## Responsive behavior

Wide screens:

```css
grid-template-columns: repeat(3, minmax(0, 1fr));
```

Tablet screens:

```css
grid-template-columns: repeat(2, minmax(0, 1fr));
```

The hero spans both tablet columns but no longer spans two rows.

Mobile screens:

```css
grid-template-columns: minmax(0, 1fr);
```

The hero returns to a normal single-column card.

## Unified tokens

The grid and cards reuse the Week 02 system:

```css
gap: var(--space-md);
padding: var(--space-md);
background: var(--color-surface);
border-color: var(--color-border);
color: var(--color-text-muted);
```

No hardcoded pixel gaps or padding values were introduced.

## AI Tool and Prompts

**AI tool:** ChatGPT

### Prompt 1: Designing an asymmetric grid

> I have a main content area containing six resource cards for an Archetype C curation portal. I want to build a CSS Grid that is asymmetric. On desktop, create a three-column layout where the first card is a hero card that spans two columns and two rows, while the other five cards each occupy one track. Write the CSS using fractional units and `minmax(0, 1fr)`. Use my existing Week 02 spacing and OKLCH theme variables for grid gaps, card padding, surfaces, borders, text, and accents. Scale to two columns on tablet and one column on mobile without text overlap or horizontal overflow.

### Prompt 2: Preventing grid gaps

> My asymmetric resource grid leaves an empty position when the viewport changes from three columns to two. Analyze the supplied HTML and CSS. Preserve the featured-card hierarchy, add `grid-auto-flow: dense`, ensure child cards use `min-inline-size: 0`, and revise the hero span at tablet and mobile sizes so large internal gaps disappear without changing the semantic source order.

## Human Audit

### Grid Inspector

Inspect `.catalog-grid` in DevTools and enable the Grid overlay. Verify that the three `fr` tracks stretch proportionally and that the hero occupies two tracks in both grid directions.

### No-overlap test

Test the page at:

- 320px
- 375px
- 768px
- 1024px
- 1440px
- 2560px

Confirm that headings, metadata, images, and links remain inside their card boundaries.

### Spacing consistency

The grid gap and card content padding are both powered by existing spacing variables. Week 04 adds no pixel-based gap or padding declaration.

## Testing and Video

- Week 04 checklist: [`week04/TESTING-CHECKLIST.md`](week04/TESTING-CHECKLIST.md)
- Week 04 video script: [`week04/VIDEO-SCRIPT.md`](week04/VIDEO-SCRIPT.md)

The separate “Web Project Testing & Quality Assurance Guide” was not included in the supplied assignment text. The prepared checklist covers every visible requirement plus common semantic, keyboard, responsive, zoom, and deployment tests.

## Deployment

GitHub Pages should remain configured as:

```text
Branch: main
Folder: /(root)
```

Opening all milestone URLs in an Incognito/Private window verifies the public archive.

## Author

**Blen Hadgu**

GitHub ID: `blenhadgu`
