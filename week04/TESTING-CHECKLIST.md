# Week 04 Testing & Quality Assurance Checklist

Use this checklist during the required video demonstration.

## Progress preservation

- [ ] `/week02/` still loads at its original URL.
- [ ] `/week03/` still loads at its original URL.
- [ ] Week 02 files were not edited.
- [ ] Week 03 files were not edited.
- [ ] `/week04/` contains the new grid milestone.
- [ ] The root milestone page links to Weeks 02, 03, and 04.

## Content-card requirements

- [ ] The main catalog contains at least five cards.
- [ ] The completed catalog contains six cards.
- [ ] Every card has a semantic `article`.
- [ ] Every card has a heading.
- [ ] Every illustration has meaningful alternative text.
- [ ] The first card is clearly identified as the featured resource.

## Asymmetric grid structure

- [ ] `.catalog-grid` uses `display: grid`.
- [ ] Desktop uses three columns.
- [ ] Columns use `repeat(3, minmax(0, 1fr))`.
- [ ] The hero card uses `grid-column: span 2`.
- [ ] The hero card uses `grid-row: span 2`.
- [ ] Supporting cards remain one grid track each.
- [ ] `grid-auto-flow: dense` is enabled.
- [ ] Grid rows use a flexible `minmax()` formula.

## Grid Inspector test

In browser DevTools:

- [ ] Inspect `.catalog-grid`.
- [ ] Enable the Grid overlay or Grid badge.
- [ ] Three proportional tracks appear on a wide desktop.
- [ ] Track boundaries resize with the viewport.
- [ ] The hero occupies two tracks in both directions.
- [ ] At tablet width, the layout changes to two tracks.
- [ ] At mobile width, the layout changes to one track.

## No-gap and auto-placement test

- [ ] Shrink from desktop to tablet gradually.
- [ ] Supporting cards fill available positions.
- [ ] No large internal hole appears beside the hero.
- [ ] Dense placement does not change the semantic reading order.
- [ ] The final incomplete row, if visible, does not create an internal grid hole.

## No-overlap test

Test approximately:

- [ ] 320px
- [ ] 375px
- [ ] 768px
- [ ] 1024px
- [ ] 1440px
- [ ] 2560px

At each width:

- [ ] Card text remains inside its card.
- [ ] Images remain inside their media regions.
- [ ] Headings wrap without clipping.
- [ ] Metadata does not overlap.
- [ ] Links remain reachable.
- [ ] No page-level horizontal scrollbar appears.
- [ ] The filter rail and catalog remain within the structural frame.

## Token and spacing consistency

- [ ] Grid gap uses `var(--space-md)`.
- [ ] Card content padding uses `var(--space-md)`.
- [ ] Larger hero padding uses existing spacing tokens.
- [ ] Card surfaces use `var(--color-surface)`.
- [ ] Borders use `var(--color-border)`.
- [ ] Text uses `var(--color-text)` and `var(--color-text-muted)`.
- [ ] Accents use `var(--color-primary)` or `var(--color-secondary)`.
- [ ] No hardcoded pixel gap or card-padding values were added.

## Keyboard and zoom

- [ ] Skip link appears first.
- [ ] Header navigation has visible focus.
- [ ] Filter controls have visible focus.
- [ ] Every card link has visible focus.
- [ ] Footer navigation has visible focus.
- [ ] The page remains usable at 200% browser zoom.
- [ ] At 200% zoom, cards reflow without clipping or overlap.

## Production deployment

- [ ] The repository is public.
- [ ] GitHub Pages deploys from `main` and `/(root)`.
- [ ] The Week 04 URL loads in an Incognito/Private window.
- [ ] All six local SVG illustrations load over HTTPS.
- [ ] Week 02 and Week 03 remain available after deployment.
- [ ] README documents the project, AI prompts, grid math, audit, and local setup.
