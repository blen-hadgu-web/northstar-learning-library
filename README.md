# Northstar Learning Library

Northstar Learning Library is a multi-week capstone project by **Blen Hadgu**. It uses **Archetype C: The Curation & Discovery Portal** to create a future web application for finding, filtering, comparing, and saving accessible technology-learning resources.

## Week 02 Milestone

The Week 02 deliverable is a visual **Design System Token Page** containing:

- Light and dark color tokens written with `oklch()`
- Background and text pairs that exceed WCAG AA contrast requirements
- Fluid typography variables created with `clamp()`
- Relative spacing constants written in `rem`
- A visual token reference page
- The required fluid-type calculation
- Manual verification notes for zoom, contrast, responsive layout, and milestone preservation

## Project Structure

```text
my-capstone-project/
├── index.html
├── README.md
├── SUBMISSION.txt
├── resume/
│   ├── index.html
│   └── styles.css
└── week02/
    ├── index.html
    └── styles.css
```

The root `index.html` is the global milestone landing page. It links directly to the preserved Week 02 page at `/week02/index.html`. The earlier resume webpage is preserved in `/resume/` so no previous work is lost.

## Run Locally

No package manager, build process, or JavaScript is required.

### Option 1: Open directly

1. Download or clone the repository.
2. Open the project folder.
3. Double-click `index.html`.

### Option 2: Use VS Code Live Server

1. Open the folder in Visual Studio Code.
2. Install the Live Server extension if needed.
3. Right-click `index.html`.
4. Choose **Open with Live Server**.

## Deployment

Expected GitHub Pages URLs:

- Global landing page: `https://blen-hadgu-web.github.io/`
- Week 02 milestone: `https://blen-hadgu-web.github.io/week02/`
- Preserved resume: `https://blen-hadgu-web.github.io/resume/`
- Public repository: `https://github.com/blen-hadgu-web/blen-hadgu-web.github.io`

## Selected Archetype

**Archetype C: The Curation & Discovery Portal**

Planned future structural elements:

- Top search header
- Filter sidebar
- Responsive resource-card grid
- Resource comparison widgets

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

Both ratios are above the WCAG AA minimum of 4.5:1 for normal text.

### Fluid Typography

```css
--size-base: clamp(1rem, 0.96rem + 0.2vw, 1.125rem);
--size-heading-md: clamp(1.25rem, 1.05rem + 0.85vw, 1.75rem);
--size-heading-lg: clamp(1.75rem, 1.31rem + 1.878vw, 3rem);
```

#### Main-title calculation

The requested range is 28px at 375px and 48px at 1440px.

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

The middle value combines `rem` and `vw`, so browser zoom still increases the text size.

### Spacing Scale

```css
--space-xs: 0.25rem;
--space-sm: 0.5rem;
--space-md: 1rem;
--space-lg: 2rem;
--space-xl: 4rem;
```

## AI Assistance

AI was used as a co-pilot to draft token ideas and explain the fluid-sizing calculation. The final token values were reviewed, adjusted, and implemented in the project.

### Palette prompt

> I am building a curation and discovery portal for accessible technology learning in OKLCH color space. I want a dark/light mode setup. Can you output a CSS :root block with color variables utilizing oklch()? The background and text colors must pass WCAG AA contrast guidelines. Please explain the math behind the Lightness (L) levels you chose for both light and dark mode to guarantee contrast.

### Fluid-scale prompt

> I need a CSS custom property for a main title font size that scales fluidly. It should have a minimum size of 1.75rem at 375px viewport width, and a maximum size of 3rem at 1440px viewport width. Can you write the clamp() property using a mix of rem and vw, and break down exactly how the middle viewport-width expression is calculated?

## Manual Verification

- Tested at 200% browser zoom
- Confirmed typography grows at zoom because the fluid expressions contain `rem`
- Confirmed the root page links to `/week02/`
- Confirmed the page adapts to mobile and desktop widths
- Confirmed keyboard focus indicators are visible
- Confirmed the repository can preserve later milestones in separate folders

## Author

**Blen Hadgu**

GitHub ID: `blenhadgu`
