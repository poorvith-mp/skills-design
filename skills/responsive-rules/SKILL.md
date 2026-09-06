---
name: responsive-rules
group: Design system
description: >-
  Define breakpoint strategy, fluid type scales and adaptive layout behaviour across devices. Use
  when designing responsive grid breakpoints, fluid spacing, or adaptive layouts.
---

# responsive-rules

## Core Philosophy
Responsive web design is not shrinking a desktop layout onto a mobile screen and hoping the user pinches and zooms. Responsive architecture is fluid adaptation across continuous viewport variations. Designing responsive interfaces requires standardized breakpoint tiers, fluid typography scales powered by CSS `clamp()`, container queries (`@container`) for modular component independence, and ergonomic thumb-zone mobile navigation.

---

## 4-Step Responsive Layout Architecture

### Step 1: Breakpoint Strategy & Viewport Tiers
1. **The 5 Standard Breakpoint Tiers (Mobile-First)**:
   - *Mobile Portrait (`base`)*: `< 640px` (Single column, stacked layouts, thumb navigation).
   - *Tablet / Mobile Landscape (`sm`)*: `640px – 767px` (2-column grids, collapsed headers).
   - *Tablet Landscape (`md`)*: `768px – 1023px` (Sidebar drawer, expanded cards).
   - *Desktop (`lg`)*: `1024px – 1279px` (Full navigation, 12-column grid, max content width `1200px`).
   - *Wide / Ultrawide (`xl` / `2xl`)*: `>= 1280px` / `>= 1536px` (Centered container, capped max-width to prevent unreadable 2000px line lengths).
2. **Mobile-First CSS Architecture**:
   - Write default styles for mobile; layer complexity progressively using `min-width` media queries:
     ```css
     .grid-container { grid-template-columns: 1fr; }
     @media (min-width: 768px) { .grid-container { grid-template-columns: repeat(2, 1fr); } }
     @media (min-width: 1024px) { .grid-container { grid-template-columns: repeat(3, 1fr); } }
     ```

### Step 2: Fluid Typography & Spacing Scales (`clamp()`)
1. **Mathematical Fluid Scaling**:
   - Eliminate jarring font-size jumps across breakpoints. Use CSS `clamp(min, preferred, max)`:
     $$V_{text{font}} = text{clamp}(1.125text{rem}, 0.95text{rem} + 0.8text{vw}, 1.75text{rem})$$
   - Headings scale smoothly with screen width while staying locked between safe minimum and maximum sizes.
2. **Fluid Spacing Tokens**:
   - Apply `clamp()` to container padding and grid gaps:
     `--gap-fluid: clamp(16px, 2vw + 8px, 32px)`.

### Step 3: Container Queries (`@container`) over Viewport Queries
1. **Component Modular Independence**:
   - A card component shouldn't care how wide the entire browser window is; it should care how wide its **parent container** is.
   - Declare container context:
     ```css
     .card-wrapper { container-type: inline-size; }
     @container (min-width: 400px) {
       .card { display: flex; flex-direction: row; }
     }
     ```
   - Allows the same component to render in vertical stack inside a narrow sidebar and horizontal row in the main feed.

### Step 4: Ergonomic Thumb Zones & Table Adaptation
1. **The Mobile Thumb Zone Rule**:
   - Place primary interactive controls (floating action buttons, bottom navigation, drawer toggles) in the bottom 40% of the screen within comfortable thumb reach.
2. **Responsive Data Table Adaptation**:
   - Desktop tables with 8 columns cannot fit on a 375px mobile screen.
   - Patterns:
     - *Horizontal Scroll with Sticky Anchor*: Freeze the primary identification column (e.g. User Name) while allowing secondary metric columns to scroll horizontally.
     - *Card Transformation*: On mobile, transform each table row into an individual stacked card.

---

## Deliverable Format: Responsive Layout Specification (`RESPONSIVE-RULES.md`)

```markdown
# Responsive Layout & Breakpoint Specification: [Application Name]

## 1. Breakpoint Architecture & Grid Layout
| Breakpoint Token | Min Width | Max Width | Columns | Margins | Gutter Gap |
|---|---|---|---|---|---|
| `mobile` | `0px` | `639px` | 4 cols | 16px | 12px |
| `tablet` | `640px` | `1023px` | 8 cols | 24px | 16px |
| `desktop` | `1024px` | `1439px` | 12 cols | 32px | 24px |
| `ultrawide` | `1440px` | Infinite | 12 cols (Capped 1280px) | Auto | 32px |

## 2. Fluid Typography Tokens (CSS `clamp()`)
- **Display Heading (`--text-display`)**: `clamp(2.25rem, 1.5rem + 3vw, 4.0rem)`
- **H1 Heading (`--text-h1`)**: `clamp(1.75rem, 1.25rem + 2vw, 2.75rem)`
- **Body Regular (`--text-body`)**: `clamp(1.0rem, 0.95rem + 0.25vw, 1.125rem)`

## 3. Responsive Navigation Behavior
- **Desktop (>= 1024px)**: Left fixed vertical sidebar (260px width).
- **Tablet (768px - 1023px)**: Left collapsed icon-only sidebar (64px width).
- **Mobile (< 768px)**: Bottom navigation bar (4 primary tabs) + slide-up drawer for secondary items.
```

---

## Worked Example: High-Density Analytics Table Responsiveness

- **Challenge**: Financial telemetry table with 10 columns broke mobile layouts with severe text clipping.
- **Solution**: Implemented container queries: when container `< 500px`, table rows automatically transform into responsive Bento cards with key-value metric pills.
- **Outcome**: Mobile user engagement increased 54%; eliminated mobile zoom friction entirely.

---

## Verification Checklist

- [ ] Mobile-first CSS architecture verified (min-width media queries).
- [ ] Typography and spacing utilize fluid `clamp()` formulas.
- [ ] Container queries (`@container`) used for modular component layouts.
- [ ] Mobile navigation places critical actions inside the ergonomic thumb zone.
- [ ] Data tables adapt gracefully via sticky columns or card transformations.

---

## Anti-Patterns

- **Desktop-Only Testing**: Designing on a 32-inch 4K monitor and testing mobile by squishing the browser window for 5 seconds.
- **Horizontal Page Scroll**: Letting an unconstrained image or table force the entire body to scroll horizontally on mobile.
- **Fixed Pixel Widths**: Using hardcoded `width: 960px` in CSS stylesheets.
