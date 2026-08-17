# Week 06 Testing & Quality Assurance Checklist

Use this checklist during your video demonstration and code review.

## 1. Archive Preservation & Progressive Enhancement

- [ ] Week 02 loads properly at `/week02/`.
- [ ] Week 03 loads properly at `/week03/`.
- [ ] Week 04 loads properly at `/week04/`.
- [ ] Week 05 loads properly at `/week05/`.
- [ ] Historical milestone files (Weeks 02–05) remain completely untouched.
- [ ] Week 06 is stored in its own dedicated directory `/week06/`.
- [ ] Week 06 local assets are located in `week06/assets/`.

## 2. Container Context Establishment

- [ ] Parent card slots declare `container-type: inline-size;`.
- [ ] Main grid items (`.catalog-item`) are established container contexts.
- [ ] Sidebar slot (`.sidebar-card-slot`) is an established container context.
- [ ] Direct parent elements have `min-inline-size: 0;` to prevent layout blowout.

## 3. Component-Level Container Queries (`@container`)

- [ ] Base `.resource-card` default layout is a compact, vertically stacked structure (image top, content bottom).
- [ ] Container query `@container (min-width: 480px)` transforms `.resource-card` into a horizontal layout (image left, content right).
- [ ] Hero variant `.resource-card--hero` adjusts seamlessly across wide container breakpoints (`@container (min-width: 720px)`).
- [ ] All `@container` declarations reside inside the `@layer components` layer block.

## 4. Media Query Elimination on Card Internals

- [ ] Zero `@media` queries are used to adjust internal card alignments, flex directions, or card-internal grid templates.
- [ ] Macro `@media` queries only adjust top-level page shells (`.portal-shell`, `.portal-header`, `.catalog-grid` columns).
- [ ] When macro columns change, the cards respond purely to their newly computed container inline-size.

## 5. Relative Container Units (`cqi` / `cqw`)

- [ ] Relative container units (`cqi`) are applied to internal padding: `padding: clamp(var(--space-sm), 4cqi, var(--space-md));`.
- [ ] Relative container units (`cqi`) are applied to fluid card headings: `font-size: clamp(1.05rem, 0.95rem + 1.8cqi, 1.35rem);`.
- [ ] Relative container units (`cqi`) are applied to badge sizes, meta gaps, and action link offsets.

## 6. The Placement Test (Multi-Context Verification)

- [ ] **Sidebar Placement**: Inspect the card inside `<aside class="filter-rail">` (`.sidebar-card-slot`).
  - Container width is narrow (< 480px).
  - The card renders vertically stacked with compact spacing.
- [ ] **Main Catalog Hero Placement**: Inspect the card inside `.catalog-item--hero`.
  - Container width is wide (> 500px).
  - The exact same component renders horizontally with expansive typography and side-by-side media.
- [ ] **Comparison**: Both instances use identical `.resource-card` markup and styles without custom wrapper hacks.

## 7. DevTools Container Query Inspection

- [ ] Open DevTools in Chrome, Edge, Firefox, or Safari.
- [ ] Inspect `.catalog-item` and verify the `container` badge appears in the Elements tree.
- [ ] Inspect `.resource-card` and verify `@container` rules appear in the Styles panel.
- [ ] Resize the browser or container; observe the container query activating and deactivating dynamically.

## 8. Accessibility & Visual Polish

- [ ] High-contrast focus rings (`:focus-visible`) remain functional on all links and form inputs.
- [ ] Images retain descriptive `alt` text and responsive `aspect-ratio` / `object-fit: cover`.
- [ ] Page passes manual 200% zoom testing without content overlap.
- [ ] Dark mode and light mode color schemes render with WCAG AA compliance.
- [ ] Semantic HTML hierarchy (`header`, `nav`, `aside`, `main`, `section`, `article`, `footer`) is maintained.

## 9. Deployment & Submission Verification

- [ ] GitHub repository visibility is set to **Public**.
- [ ] GitHub Pages deploys from the `main` branch and `/(root)` directory.
- [ ] Live URL loads cleanly in an Incognito / Private browsing window.
- [ ] `README.md` documents Week 06 container queries, prompt transcripts, and test instructions.
