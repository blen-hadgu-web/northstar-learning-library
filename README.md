# Northstar Learning Library

Northstar Learning Library is a progressive capstone project by **Blen Hadgu**. It uses **Archetype C: The Curation & Discovery Portal** to create an accessible interface for finding, filtering, comparing, and saving technology-learning resources.

## Live Milestones

- Project landing page: `https://blen-hadgu-web.github.io/northstar-learning-library/`
- Week 02 design tokens: `https://blen-hadgu-web.github.io/northstar-learning-library/week02/`
- Week 03 structural frame: `https://blen-hadgu-web.github.io/northstar-learning-library/week03/`
- Week 04 asymmetric grid: `https://blen-hadgu-web.github.io/northstar-learning-library/week04/`
- Week 05 CSS architecture: `https://blen-hadgu-web.github.io/northstar-learning-library/week05/`

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
│   └── VIDEO-SCRIPT.md
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
└── week05/
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
    ├── TESTING-CHECKLIST.md
```

Week 05 duplicates the Week 04 page and assets into a new directory. The Week 05 HTML is byte-for-byte identical to Week 04; only the copied stylesheet is architecturally refactored.

## Run Locally

No package manager, CSS preprocessor, JavaScript framework, or build command is required.

1. Download or clone the repository.
2. Open the root `index.html`.
3. Use the milestone links to open Week 04 and Week 05 for comparison.

VS Code Live Server may also be used.

# Week 05: Native Nesting & `@layer` Architecture

## Visual-continuity goal

The Week 05 page intentionally preserves the Week 04 content and visual hierarchy:

- Same semantic HTML
- Same local SVG assets
- Same header and filter rail
- Same asymmetric six-card grid
- Same colors, spacing, shadows, and breakpoints

The change is architectural rather than visual. An automated Chromium comparison found zero changed pixels at 1440×900, 1024×900, 768×1024, and 375×812.

## Layer precedence

The first statement in `week05/styles.css` is:

```css
@layer reset, base, layout, components;
```

The responsibilities are:

### `reset`

Structural browser-default cleanup:

- Universal `box-sizing`
- Default margin removal
- List padding reset
- Responsive image defaults
- Form-control font inheritance

### `base`

Global design and element defaults:

- Week 02 custom properties
- Light and dark OKLCH tokens
- Body typography and background
- Heading, paragraph, link, code, and focus defaults

### `layout`

High-level frames inherited from Week 03:

- Full dynamic-viewport portal shell
- Global header grid
- Filter sidebar
- Main catalog workspace
- Footer
- Responsive frame rearrangement

### `components`

Specific interface pieces:

- Navigation links
- Filter controls
- Asymmetric grid
- Resource cards
- Hero modifier
- Badges
- Metadata
- Card links
- Grid note
- Accessibility utility

Because `components` is declared later than `base`, component rules win by layer precedence before selector specificity needs to be increased.

## Native CSS nesting

Week 05 uses native nesting directly inside the `.css` file.

Example:

```css
.resource-card {
  display: grid;

  &.resource-card--hero {
    grid-template-columns: minmax(0, 1.05fr) minmax(0, 0.95fr);

    .resource-card__content {
      align-content: center;
    }
  }

  .resource-card__link {
    text-decoration: none;

    &:hover {
      text-decoration: underline;
    }

    &:focus-visible {
      outline: 0.22rem solid var(--color-focus);
    }
  }
}
```

Other nested component roots include:

- `.portal-header`
- `.filter-form`
- `.catalog-grid`
- `.resource-card`
- `.grid-notes`

## Parent selector usage

The stylesheet uses `&` for:

- `&:hover`
- `&:focus`
- `&:focus-visible`
- `&[aria-current="page"]`
- `&.catalog-item--hero`
- `&.resource-card--hero`

It does not use Sass-only selector concatenation such as `&--hero`.

## No preprocessor

The project requires:

- No Sass
- No PostCSS compilation
- No npm command
- No generated CSS
- No source map

The browser reads `week05/styles.css` directly.

## AI Tool and Prompts

**AI tool:** ChatGPT

### Prompt 1: Refactoring CSS to cascade layers

> Here is my Week 04 stylesheet [paste CSS]. Modernize it by sorting the rules into exactly four cascade layers declared in this order: `reset`, `base`, `layout`, and `components`. Preserve the existing visual output. Put browser-default cleanup in reset, design tokens and element defaults in base, global header/sidebar/main/footer frames in layout, and navigation, forms, grids, cards, badges, and widgets in components. Keep responsive rules inside the layer that owns the affected rules. Explain why each group belongs in its layer.

### Prompt 2: Refactoring to native nesting

> Analyze my Week 04 card, navigation, filter, and grid styles [paste component CSS]. Refactor them with native CSS nesting in a normal `.css` file. Nest child selectors beneath `.portal-header`, `.filter-form`, `.catalog-grid`, `.resource-card`, and `.grid-notes`. Use the parent selector for pseudo-classes and modifiers, including `&:hover`, `&:focus-visible`, `&[aria-current="page"]`, and `&.resource-card--hero`. Do not use Sass-only `&--modifier` syntax, and do not require a build process. Preserve the Week 04 visual output.

## Human Audit

### Visual continuity

Compare Week 04 and Week 05 at identical viewport sizes. The HTML and assets are identical, and the refactored declarations retain the same values for the live interface.

### Inspector layer audit

In DevTools:

1. Inspect `.resource-card__badge` and find the `components` layer.
2. Inspect `.catalog-workspace` and find the `layout` layer.
3. Inspect an `h3` and find the `base` layer.
4. Confirm that the browser displays nested rules rather than ignoring them.

### Native-syntax check

Verify:

- The file is `styles.css`
- Nested rules appear in DevTools
- Hover and focus states work
- Hero modifier rules apply
- No `.scss` file exists

## Testing and Video

- Week 05 architecture audit: [`week05/ARCHITECTURE-AUDIT.txt`](week05/ARCHITECTURE-AUDIT.txt)
- Week 05 checklist: [`week05/TESTING-CHECKLIST.md`](week05/TESTING-CHECKLIST.md)
- Week 05 video script: [`week05/VIDEO-SCRIPT.md`](week05/VIDEO-SCRIPT.md)

The separate “Web Project Testing & Quality Assurance Guide” was not included in the supplied assignment text. The prepared checklist covers archive preservation, visual continuity, layer inspection, nesting syntax, responsive behavior, keyboard access, zoom, and deployment.

## Deployment

GitHub Pages remains configured as:

```text
Branch: main
Folder: /(root)
```

## Author

**Blen Hadgu**

GitHub ID: `blenhadgu`
