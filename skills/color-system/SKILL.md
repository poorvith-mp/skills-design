---
name: color-system
group: Design system
description: >-
  Turn a chosen direction into a real palette: tints, WCAG contrast, dark mode mapping, elevation
  and tokens. Use when building semantic color tokens, dark mode palettes, or contrast scales.
---

# color-system

## Core Philosophy
A production color system is not a static Figma swatch board of 5 favorite hex codes. A true color system is a mathematically coherent, tokenized software architecture. It governs contrast ratios, elevation surface ramps, perceptual lightness distribution, semantic state bindings, and flawless bidirectional light/dark mode transitions without manual per-screen overrides.

---

## 4-Step Scalable Color System Engineering

### Step 1: The 3-Tier Token Architecture
1. **The Token Hierarchy**:
   - *Tier 1: Global Primitives (Raw Values)*:
     - `blue-500: #3B82F6`, `slate-900: #0F172A`. Never consume primitives directly in components.
   - *Tier 2: Semantic Tokens (System Purpose)*:
     - `surface-canvas: var(--slate-900)`, `action-primary: var(--blue-500)`.
   - *Tier 3: Component Tokens (Scoped Overrides)*:
     - `button-primary-bg: var(--action-primary)`.

### Step 2: Perceptual Color Spaces (OKLCH) & Shade Generation
1. **Why sRGB/HSL Fails**:
   - HSL is mathematically flawed: pure yellow ($H=60$) has vastly higher perceived luminance than pure blue ($H=240$), making consistent lightness across hues impossible.
2. **The OKLCH Standard**:
   - Use **OKLCH** (`oklch(L C H)`):
     - $L$ = Perceptual Lightness (0% to 100%).
     - $C$ = Chroma / Saturation (0 to ~0.37).
     - $H$ = Hue angle ($0^\circ$ to $360^\circ$).
   - Generating consistent shades (50 to 950): Fix Hue and Chroma, and step Lightness mathematically from 95% down to 10%.

### Step 3: Elevation Ramps & Dark Mode Surface Parity
1. **The Elevation Surface Ladder in Dark Mode**:
   - In light mode, elevation is communicated via drop shadows (`box-shadow`).
   - In dark mode, shadows are invisible against dark backgrounds. Elevation must be communicated via **surface lightness stepping**:
     - `surface-base (0dp)`: `oklch(14% 0.02 260)` (Canvas background)
     - `surface-raised (1dp)`: `oklch(18% 0.02 260)` (Card background)
     - `surface-overlay (4dp)`: `oklch(22% 0.02 260)` (Dropdown menu)
     - `surface-modal (8dp)`: `oklch(26% 0.02 260)` (Floating dialog)
2. **Never Use Pure Black (`#000000`) for Dark Mode**:
   - Pure black causes harsh pixel smearing on OLED screens and severe contrast strain against pure white text. Use deep slate/navy tints ($L pprox 12–15\%$).

### Step 4: Semantic State Mapping & Automated Contrast Gates
1. **Interactive State Offsets**:
   - Hover: Adjust lightness by $\pm 5\%$ in OKLCH.
   - Pressed / Active: Adjust lightness by $\pm 10\%$.
   - Disabled: Lock Chroma to 0 (grayscale) and set opacity to 40%.
2. **Contrast Verification**:
   - Automatically assert that every text semantic token against its assigned surface token achieves $\ge 4.5:1$ WCAG contrast.

---

## Deliverable Format: Color Tokens Definition (`tokens.css`)

```css
/* ==========================================================================
   PRODUCTION COLOR SYSTEM TOKENS (OKLCH)
   ========================================================================== */

:root {
  /* 1. Global Primitives (Indigo Scale) */
  --indigo-50:  oklch(96% 0.02 270);
  --indigo-500: oklch(58% 0.22 270);
  --indigo-600: oklch(50% 0.22 270);
  --indigo-900: oklch(24% 0.12 270);

  /* Slate Scale */
  --slate-50:  oklch(98% 0.005 250);
  --slate-100: oklch(94% 0.010 250);
  --slate-800: oklch(22% 0.020 250);
  --slate-900: oklch(14% 0.020 250);

  /* 2. Semantic Mappings (Light Mode Default) */
  --surface-canvas: var(--slate-50);
  --surface-card:   #ffffff;
  --text-primary:   var(--slate-900);
  --text-muted:     var(--slate-800);
  --border-subtle:  var(--slate-100);
  
  --action-primary-bg:    var(--indigo-500);
  --action-primary-hover: var(--indigo-600);
  --action-primary-text:  #ffffff;
}

/* 3. Dark Mode Overrides (Automatic Surface Inversion) */
[data-theme="dark"] {
  --surface-canvas: var(--slate-900);
  --surface-card:   var(--slate-800);
  --text-primary:   var(--slate-50);
  --text-muted:     var(--slate-100);
  --border-subtle:  var(--slate-800);

  --action-primary-bg:    var(--indigo-500);
  --action-primary-hover: var(--indigo-600);
  --action-primary-text:  #ffffff;
}
```

---

## Worked Example: Automated CI Contrast Gate

- **Tooling**: Integrated `stylelint-color-contrast` into frontend test suite.
- **Detection**: PR attempted to set secondary text to `#888888` on `#FFFFFF` (contrast 3.5:1; fails WCAG AA).
- **Resolution**: CI failed build automatically; developer adjusted token to `#6B7280` (4.6:1), maintaining full accessibility compliance.

---

## Verification Checklist

- [ ] Tokens structured into 3 distinct tiers (Primitives -> Semantics -> Components).
- [ ] Color shades generated in perceptual color space (OKLCH or Lab).
- [ ] Dark mode surfaces use stepped elevation lightness ramps rather than pure black.
- [ ] All interactive states (Hover, Active, Focus, Disabled) mathematically derived.
- [ ] Automated tests verify $\ge 4.5:1$ contrast across all text/surface pairings.

---

## Anti-Patterns

- **Hardcoding Hex Codes in Components**: Writing `color: #4F46E5` directly inside a React component stylesheet.
- **Inverted Dark Mode Negatives**: Inverting black text to white while leaving bright background containers blindingly white.
- **Pure Black OLED Traps**: Setting `#000000` as the global background, causing severe text smearing on mobile scrolling.
