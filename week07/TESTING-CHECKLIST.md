# Week 07 Testing & Quality Assurance Checklist

Use this checklist during your video demonstration and code review.

## 1. Archive Preservation & Progressive Enhancement

- [ ] Week 02 loads properly at `/week02/`.
- [ ] Week 03 loads properly at `/week03/`.
- [ ] Week 04 loads properly at `/week04/`.
- [ ] Week 05 loads properly at `/week05/`.
- [ ] Week 06 loads properly at `/week06/`.
- [ ] Historical milestone files (Weeks 02–06) remain completely untouched.
- [ ] Week 07 is stored in its own dedicated directory `/week07/`.
- [ ] Week 07 local assets are located in `week07/assets/`.

## 2. High-Performance Micro-Interactions

- [ ] **Resource Cards**: Hovering or focusing into `.resource-card` smoothly elevates the card (`translateY(-0.35rem) scale(1.012)`) and deepens its shadow.
- [ ] **Card Media**: Hovering over a card subtly scales the image (`scale(1.05)`) within its clipping boundary.
- [ ] **Action Links**: Hovering or focusing over card links slides the arrow icon (`translateX(0.4rem)`).
- [ ] **Buttons**: Clicking or activating buttons triggers a tactile scale feedback (`scale(0.97)`).
- [ ] **Navigation Links**: Hovering over header/footer links produces smooth background tinting and micro-lift (`translateY(-0.0625rem)`).
- [ ] **Form Controls**: Checkbox hover shows subtle scaling; labels subtly highlight and translate.
- [ ] **Brand Icon**: Hovering over the brand icon produces a playful rotation (`rotate(45deg) scale(1.15)`).
- [ ] **Hardware Acceleration**: Only composited properties (`transform`, `opacity`, `background-color`, `box-shadow`) are transitioned. Zero layout-thrashing properties (`width`, `height`, `margin`, `top`) are animated.

## 3. Active & Focus States (`:focus-visible`)

- [ ] Every interactive element displays a high-contrast focus ring (`:focus-visible`) utilizing `--color-focus`.
- [ ] Focus states trigger card and button micro-interactions equally as mouse hover (accessible to keyboard users).
- [ ] Tab order proceeds logically through header navigation, filter form, sidebar spotlight card, catalog items, and footer.

## 4. Modern CSS Scroll-Driven Animations

- [ ] **Option A (Reading Progress Bar)**:
  - Top fixed progress bar (`.scroll-progress-bar`) fills from 0% to 100% horizontally as the page is scrolled.
  - Progress bar is bound natively via `animation-timeline: scroll(root)`.
- [ ] **Option B (Scroll-Reveal Elements)**:
  - Catalog cards (`.catalog-item`) and sidebar spotlight (`.sidebar-spotlight`) fade in and slide upward as they scroll into view.
  - Elements use native `animation-timeline: view()` and `animation-range: entry 10% cover 35%`.
- [ ] **Zero JavaScript**: Animations run 100% in CSS without external JavaScript libraries.

## 5. Reduced-Motion Accessibility (`prefers-reduced-motion`)

- [ ] Enable "Reduce Motion" in your operating system (Windows: Settings > Accessibility > Visual Effects > Animation effects OFF / macOS: System Settings > Accessibility > Display > Reduce motion).
- [ ] Refresh the page in the browser:
  - All transitions shut off instantly (`transition-duration: 0s !important`).
  - All scroll animations shut off instantly (`animation-duration: 1ms !important`).
  - The scroll progress bar is cleanly hidden (`display: none !important`).
  - The interface remains 100% usable, readable, and static.

## 6. Performance & Paint Flashing Audit

- [ ] Open Chrome DevTools > More tools > **Rendering**.
- [ ] Check **Paint flashing**.
- [ ] Hover and interact with cards, buttons, and navigation links.
- [ ] Verify that hover interactions only repaint the affected local component, not the entire page layout.

## 7. Responsive & Zoom Verification

- [ ] Verify functionality across viewports: 320px, 375px, 768px, 1024px, 1440px, 2560px.
- [ ] Test at 200% zoom: ensure text wrapping and micro-interactions remain fully functional without overflow.
- [ ] Light and dark color schemes preserve contrast and accessibility.

## 8. Deployment & Submission Verification

- [ ] GitHub repository visibility is set to **Public**.
- [ ] GitHub Pages deploys from the `main` branch and `/(root)` directory.
- [ ] Live URL loads cleanly in an Incognito / Private browsing window.
- [ ] `README.md` documents Week 07 micro-interactions, scroll animations, AI prompts, and test results.
