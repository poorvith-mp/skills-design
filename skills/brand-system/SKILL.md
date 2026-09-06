---
name: brand-system
group: Brand
description: >-
  Build brand identity end to end: voice, logomarks, adaptive logo systems and usage rules. Use
  when defining brand guidelines, logos, iconography, or visual assets.
---

# brand-system

## Core Philosophy
A brand identity system is not merely drawing a clever vector logo in Illustrator. A brand system is a scalable visual operating system. It codifies the psychological essence, typography, color tokens, iconography, layout grids, and voice of an organization across all touchpoints—from a 16px favicon in a browser tab to an enterprise keynote slide. Great brand systems eliminate design ambiguity and ensure instant recognition.

---

## 4-Step Brand System Architecture

### Step 1: Brand Position & Personality Spectrum
1. **The 5 Brand Personality Axes**:
   - Rate the brand on a 1–10 spectrum:
     - *Tone*: Playful / Whimsical (1) $\longleftrightarrow$ Serious / Authoritative (10)
     - *Audience*: Mass Consumer (1) $\longleftrightarrow$ Specialized Technical Expert (10)
     - *Energy*: Calm / Minimal (1) $\longleftrightarrow$ Dynamic / Bold (10)
     - *Era*: Heritage / Retro (1) $\longleftrightarrow$ Futuristic / Avant-Garde (10)
     - *Aesthetic*: Expressive / Maximal (1) $\longleftrightarrow$ Restrained / Utilitarian (10)
2. **The Brand Core Statement**:
   - Synthesize the brand promise into a single declarative thesis (e.g., "The minimalist toolkit for systems craftsmen").

### Step 2: Adaptive Logo Architecture & Clear-Space Rules
1. **The 4 Responsive Logo Variants**:
   - *Display Lockup*: Full wordmark + logomark + optional tagline (Used for hero banners, conference booths).
   - *Standard Lockup*: Logomark + Wordmark (Desktop navigation, investor decks).
   - *Compact Logomark*: Symbol only (Mobile nav, social avatars, app icons).
   - *Micro / Favicon*: Simplified, high-contrast glyph optimized for 16x16px and 32x32px rendering.
2. **The Clear-Space Formula**:
   - Define exclusion zones using a relative element from the logo (e.g. the height of the letter "X" or the width of the mark icon):
     $$text{Minimum Margin} = 1.0  imes text{Height of Symbol}$$
   - No external text, borders, or graphics may encroach within this clear zone.

### Step 3: Color Tokens, Hierarchy & Typography Pairing
1. **The 60-30-10 Rule of Visual Balance**:
   - *60% Dominant Base*: Neutral background (Crisp White or Deep Obsidian Slate).
   - *30% Secondary Structure*: Text, cards, structural borders, navigation headers.
   - *10% Brand Accent*: Vibrant signature color reserved strictly for primary actions, badges, and focal points.
2. **Typography Pairing Archetypes**:
   - *Technical / Systems*: Sans-serif display (`Geist`, `Inter`) paired with Monospace for data/code (`JetBrains Mono`).
   - *Editorial / Intellectual*: Modern Serif display (`Newsreader`, `Fraunces`) paired with clean geometric body (`Plus Jakarta Sans`).

### Step 4: Asset Governance & Brand Style Guide Specification
1. **Asset Export Packaging**:
   - Export all marks in SVG (vector), PDF (print vector), WebP/PNG (raster @ 1x, 2x, 3x).
   - Provide dark-mode, light-mode, and monochrome (all-black, all-white) variants for every mark.

---

## Deliverable Format: Master Brand Guidelines Specification (`BRAND-GUIDELINES.md`)

```markdown
# Brand Identity System Specification: [Brand Name]

## 1. Brand Essence & Personality
- **Core Stance**: [e.g. Developer-first, understated, high-precision]
- **Personality Scores**: Tone: 8/10 | Technicality: 9/10 | Restraint: 9/10

## 2. Logo System & Usage Rules
- **Primary Mark**: Geometric hexagonal core with internal single-pixel glyph.
- **Minimum Digital Size**: 24px height (Standard lockup); 16px (Micro mark).
- **Clear Space**: 1.5x width of the logomark symbol on all four sides.
- **Prohibited Alterations**: Never rotate, drop-shadow, stretch, or alter official brand colors.

## 3. Brand Color Palette (HEX / OKLCH)
| Role | Token Name | Value | Purpose |
|---|---|---|---|
| Background | `--brand-bg-canvas` | `#0A0D14` | Primary dark surface |
| Accent | `--brand-accent-primary` | `#00F0FF` | Electric Cyan (10% focal point) |
| Text Neutral | `--brand-text-primary` | `#F1F5F9` | High-contrast body text |
| Border | `--brand-border-subtle` | `#1E293B` | Structural dividers |

## 4. Typography Hierarchy
- **Display Headings**: `Geist Sans` (Bold, Tracking: -0.02em)
- **Body Text**: `Inter` (Regular, 16px, Line-height: 1.5)
- **Code & Metrics**: `JetBrains Mono` (Medium, Tracking: 0)
```

---

## Worked Example: Developer Infrastructure Tool Rebrand

- **Challenge**: Company had an amateur cartoon mascot logo that enterprise CISOs viewed as untrustworthy during procurement reviews.
- **System Built**: Designed a clean geometric vector glyph inspired by network routing nodes; established a restrained monochrome palette with an emerald accent; codified strict clear-space rules.
- **Impact**: Enterprise contract velocity accelerated; sales reps reported zero pushback on enterprise security perception.

---

## Verification Checklist

- [ ] Responsive logo variants exist for all sizes (Display, Standard, Compact, 16px Favicon).
- [ ] Clear-space rules and minimum scale boundaries are mathematically defined.
- [ ] Color tokens adhere to the 60-30-10 visual balance rule.
- [ ] Typography specifies fonts, weights, sizes, line heights, and letter-spacing (tracking).
- [ ] Prohibited logo manipulations (stretching, unapproved colors) are explicitly illustrated.

---

## Anti-Patterns

- **Single Rigid Logo**: Creating one complex logo illustration and trying to shrink it into a 16px favicon.
- **Color Overload**: Using 8 bright accent colors equally on a single page, destroying visual hierarchy.
- **Unenforced Guidelines**: Writing a 50-page PDF brand guide that nobody reads because assets aren't organized in accessible Figma libraries and code tokens.
