# Week 05 Testing & Quality Assurance Checklist

Use this checklist during the video demonstration.

## Archive preservation

- [ ] Week 02 still loads at `/week02/`.
- [ ] Week 03 still loads at `/week03/`.
- [ ] Week 04 still loads at `/week04/`.
- [ ] Week 02–04 source files were not edited.
- [ ] Week 05 is stored separately at `/week05/`.
- [ ] Week 05 uses the same HTML and assets as Week 04.

## Visual continuity

Compare Week 04 and Week 05 at the same viewport:

- [ ] Header position and spacing match.
- [ ] Filter rail width and controls match.
- [ ] Catalog heading and toolbar match.
- [ ] Featured card size and placement match.
- [ ] Five supporting cards match.
- [ ] Grid gaps and card padding match.
- [ ] Colors, borders, radii, and shadows match.
- [ ] Tablet layout matches.
- [ ] Mobile layout matches.
- [ ] No new clipping, overlap, or horizontal overflow appears.

## Cascade-layer declaration

- [ ] The first CSS statement is:
      `@layer reset, base, layout, components;`
- [ ] The stylesheet contains an `@layer reset` block.
- [ ] The stylesheet contains an `@layer base` block.
- [ ] The stylesheet contains an `@layer layout` block.
- [ ] The stylesheet contains an `@layer components` block.
- [ ] No fifth named layer was added.
- [ ] Components is the final layer in the declared order.

## Layer responsibility

- [ ] `reset` contains box sizing and default margin resets.
- [ ] `base` contains variables and default HTML element styles.
- [ ] `layout` contains the portal shell, header, sidebar, main, and footer frame.
- [ ] `components` contains navigation controls, filters, cards, badges, links, and widgets.
- [ ] Responsive rules remain inside the appropriate layer.

## DevTools layer audit

- [ ] Open Week 05 in a current browser.
- [ ] Inspect `.resource-card__badge`.
- [ ] The Styles panel identifies its rule as part of `components`.
- [ ] Inspect `.catalog-workspace`.
- [ ] Its high-level frame rule appears in `layout`.
- [ ] Inspect an `h3`.
- [ ] Its default element rule appears in `base`.
- [ ] Verify that later layers override earlier layers without `!important` for normal component styling.

## Native CSS nesting

- [ ] `.resource-card` contains nested child rules.
- [ ] `.filter-form` contains nested child rules.
- [ ] `.portal-header` contains nested child rules.
- [ ] `.catalog-grid` contains nested child rules.
- [ ] `.grid-notes` contains nested child rules.
- [ ] Nested `&:hover` is present.
- [ ] Nested `&:focus-visible` is present.
- [ ] Nested `&[aria-current="page"]` is present.
- [ ] Modifier selectors use valid native syntax such as
      `&.resource-card--hero`.
- [ ] No Sass-only `&--modifier` concatenation appears.
- [ ] No `.scss` file or build step is required.

## Browser syntax verification

- [ ] The browser loads the CSS without parse errors.
- [ ] Nested resource-card rules appear in DevTools.
- [ ] Hovering a resource link still underlines it.
- [ ] Keyboard focus remains visible.
- [ ] The hero modifier still applies.
- [ ] Dark mode still uses the same token values.

## Responsive and accessibility checks

Test approximately:

- [ ] 320px
- [ ] 375px
- [ ] 768px
- [ ] 1024px
- [ ] 1440px
- [ ] 2560px

At each size:

- [ ] No horizontal page scrollbar appears.
- [ ] Cards do not overlap.
- [ ] Navigation remains usable.
- [ ] Text remains inside components.
- [ ] The page works at 200% zoom.
- [ ] Keyboard focus order remains logical.
- [ ] Reduced-motion mode remains usable.

## Deployment

- [ ] The repository is public.
- [ ] GitHub Pages deploys from `main` and `/(root)`.
- [ ] The Week 05 URL loads in an Incognito/Private window.
- [ ] Week 02–04 URLs still load after deployment.
- [ ] README documents the prompts, layer architecture, nesting syntax, audit, and local setup.
