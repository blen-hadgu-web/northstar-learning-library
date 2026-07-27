# Northstar Learning Library

Northstar Learning Library is a multi-week capstone project by **Blen Hadgu**. It uses **Archetype C: The Curation & Discovery Portal** to create a web application for finding, filtering, comparing, and saving accessible technology-learning resources.

## Week 02 Milestone

The Week 02 deliverable is a visual **Design System Token Page** containing:

- Light and dark color tokens written with `oklch()`
- Background and text pairs that exceed WCAG AA contrast requirements
- Fluid typography variables created with `clamp()`
- Relative spacing constants written in `rem`
- A visual token reference page
- The required fluid-type calculation
- The required AI prompts and design decisions
- Manual verification notes for zoom, contrast, responsiveness, and milestone preservation

## Selected Archetype

**Archetype C: The Curation & Discovery Portal**

Planned structural elements:

- Top search header
- Filter sidebar
- Responsive resource-card grid
- Resource comparison widgets

## Project Structure

```text
northstar-learning-library/
├── index.html
├── README.md
├── SUBMISSION.txt
└── week02/
    ├── index.html
    └── styles.css
```

The root `index.html` is the global milestone landing page. It links directly to `week02/index.html`. Future milestones will be preserved in directories such as `week03/`, `week04/`, and so on.

## Run Locally

No package manager, framework, build process, or JavaScript is required.

### Open directly

1. Download or clone the repository.
2. Open the project folder.
3. Double-click `index.html`.

### Use VS Code Live Server

1. Open the repository folder in Visual Studio Code.
2. Install Live Server if needed.
3. Right-click the root `index.html`.
4. Choose **Open with Live Server**.

## Deployment

Public repository:

```text
https://github.com/blen-hadgu-web/northstar-learning-library
```

Expected GitHub Pages URLs:

- Landing page: `https://blen-hadgu-web.github.io/northstar-learning-library/`
- Week 02: `https://blen-hadgu-web.github.io/northstar-learning-library/week02/`

Configure GitHub Pages to deploy from the `main` branch and `/(root)`.

## Design Tokens

### Light Mode

```css
--color-primary: oklch(48% 0.19 255);
--color-secondary: oklch(45% 0.13 170);
--color-background: oklch(97.5% 0.015 250);
--color-text: oklch(23% 0.035 255);
```

The background/text pair has an approximate contrast ratio of **15.71:1**.

### Dark Mode

```css
--color-primary: oklch(72% 0.15 250);
--color-secondary: oklch(76% 0.12 170);
--color-background: oklch(17% 0.025 255);
--color-text: oklch(94% 0.015 250);
```

The background/text pair has an approximate contrast ratio of **16.06:1**.

Both exceed the WCAG AA minimum of 4.5:1 for normal text.

## Lightness Decisions

- Light mode: background `L = 97.5%`, text `L = 23%`
- Dark mode: background `L = 17%`, text `L = 94%`

The large separation in OKLCH lightness creates strong visual contrast. Because lightness separation alone does not mathematically guarantee a WCAG ratio, the final pairs were also checked with contrast calculations.

## Fluid Typography

```css
--size-base: clamp(1rem, 0.96rem + 0.2vw, 1.125rem);
--size-heading-md: clamp(1.25rem, 1.05rem + 0.85vw, 1.75rem);
--size-heading-lg: clamp(1.75rem, 1.31rem + 1.878vw, 3rem);
```

### Main-title calculation

The required range is 28px at 375px and 48px at 1440px.

```text
slope = (48 - 28) / (1440 - 375)
      = 20 / 1065
      ≈ 0.01878

vw coefficient = 0.01878 × 100
               ≈ 1.878vw

intercept = 28 - (0.01878 × 375)
          ≈ 20.96px
          ≈ 1.31rem
```

Final property:

```css
--size-heading-lg: clamp(1.75rem, 1.31rem + 1.878vw, 3rem);
```

The middle value combines `rem` and `vw`, so browser zoom still enlarges the text.

## Spacing Scale

```css
--space-xs: 0.25rem;
--space-sm: 0.5rem;
--space-md: 1rem;
--space-lg: 2rem;
--space-xl: 4rem;
```

## AI Assistance

AI was used as a co-pilot to draft token ideas and explain the fluid-sizing calculation. The final values were reviewed and implemented by the project author.

### Palette prompt

> I am building a curation and discovery portal for accessible technology learning in OKLCH color space. I want a dark/light mode setup. Can you output a CSS :root block with color variables utilizing oklch()? The background and text colors must pass WCAG AA contrast guidelines. Please explain the math behind the Lightness (L) levels you chose for both light and dark mode to guarantee contrast.

### Fluid-scale prompt

> I need a CSS custom property for a main title font size that scales fluidly. It should have a minimum size of 1.75rem at 375px viewport width, and a maximum size of 3rem at 1440px viewport width. Can you write the clamp() property using a mix of rem and vw, and break down exactly how the middle viewport-width expression is calculated?

## Manual Verification

- Tested at 200% browser zoom
- Confirmed typography grows because the fluid expressions contain `rem`
- Confirmed the root page links directly to `week02/`
- Confirmed the layout adapts to mobile and desktop widths
- Confirmed keyboard focus indicators are visible
- Confirmed both background/text pairs exceed 4.5:1
- Confirmed future milestones can be added without overwriting Week 02

## Author

**Blen Hadgu**

GitHub ID: `blenhadgu`
