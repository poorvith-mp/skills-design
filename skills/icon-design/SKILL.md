---
name: icon-design
group: Brand
description: >-
  Write icon briefs specifying metaphor, style, grid, stroke weight and usage context. Use when
  crafting custom SVG icon sets, glyphs, or pixel-perfect grids.
---

# icon-design

## Core Philosophy
Icon design is not drawing tiny decorative illustrations. An icon is a high-density, language-agnostic visual sign engineered for instantaneous recognition at microscopic scales (16x16px). Flawed icon sets suffer from inconsistent optical weights, misaligned pixel grids, mismatched corner radii, and ambiguous visual metaphors. Professional icon systems require strict pixel-grid alignment, unified stroke geometry, optical balance over geometric perfection, and clean SVG path optimization.

---

## 4-Step Professional Icon System Architecture

### Step 1: Pixel Grid Hierarchy & Safe Zones
1. **The Two Core Grids**:
   - *16x16px (Dense UI / Tables / Input adornments)*: 1px stroke weight; 1px live safe margin.
   - *24x24px (Standard Action / Navbars / Buttons)*: 1.5px or 2px stroke weight; 2px live safe margin.
2. **The Safe Zone & Keyline Shapes**:
   - Never draw to the absolute edge of the canvas. Keep strokes inside the inner safe area (20x20px on a 24px grid).
   - Use standardized keyline shapes for visual mass parity:
     - Circle: 20px diameter.
     - Square: 18x18px.
     - Horizontal Rectangle: 20x16px.
     - Vertical Rectangle: 16x20px.

### Step 2: Optical Balancing vs Geometric Alignment
1. **The Triangle / Asymmetric Center Rule**:
   - Geometrically centered shapes often appear off-center to the human eye.
   - Example (Play Button Triangle): Geometrically centering a right-pointing triangle places its center of mass too far left. Shift the triangle **1–2 pixels to the right** to achieve true optical balance.
2. **Stroke Cap & Join Consistency**:
   - Standardize across the entire set:
     - `stroke-linecap: round` AND `stroke-linejoin: round` (or strictly `butt` / `miter`). Never mix rounded and sharp joins in the same icon set.

### Step 3: Metaphor Clarity & Cognitive Load
1. **Universal vs Novel Metaphors**:
   - Universal metaphors must not be reinvented:
     - Search = Magnifying glass (never binoculars or flashlights).
     - Settings = Gear (never wrench + screwdriver combination).
     - Delete = Trash can.
   - Only invent novel metaphors for domain-specific concepts (e.g. database shards, webhook endpoints), grounding them in established system symbols.

### Step 4: SVG Vector Hygiene & Optimization (SVGO)
1. **Vector Cleanliness**:
   - Convert all strokes to outlines (`Fill`) OR maintain pure strokes (`vector-effect="non-scaling-stroke"`).
   - Merge overlapping vector paths into a single clean compound path (`Path -> Union`).
2. **Automated SVGO Compression Pipeline**:
   - Strip metadata, comments, editor namespaces (Inkscape/Illustrator junk):
     ```bash
     npx svgo -f ./icons/src -o ./icons/dist --config svgo.config.js
     ```
   - Ensure root SVG sets `viewBox="0 0 24 24"`, `width="100%"`, `height="100%"`, and `fill="currentColor"`.

---

## Deliverable Format: Icon System Specification (`ICON-SYSTEM-SPEC.md`)

```markdown
# Custom Icon System Specification: [Product Name]

## 1. Grid & Geometry Standards
- **Standard Canvas**: 24x24px vector viewBox
- **Stroke Weight**: Uniform 1.5px
- **Terminal Caps**: `stroke-linecap="round"` | `stroke-linejoin="round"`
- **Corner Radius**: 2px on all outer corners
- **Safe Zone Margin**: 2px inset on all four sides

## 2. Icon Metaphor Dictionary
| Icon Name | Slug ID | Universal Metaphor | Usage Context |
|---|---|---|---|
| Search | `icon-search` | Magnifying glass (45° angle) | Global search bar |
| Webhook | `icon-webhook` | Diverging signal arrows | API configuration |
| Database | `icon-database` | 3-tier stacked cylinder | Data source selector |
| Incident | `icon-incident` | Octagon with exclamation mark | P1 alert banner |

## 3. SVG Clean Code Template
```xml
<svg xmlns="http://www.w3.org/2000/svg" 
     viewBox="0 0 24 24" 
     fill="none" 
     stroke="currentColor" 
     stroke-width="1.5" 
     stroke-linecap="round" 
     stroke-linejoin="round">
  <circle cx="12" cy="12" r="9" />
  <line x1="12" y1="8" x2="12" y2="12" />
  <line x1="12" y1="16" x2="12.01" y2="16" />
</svg>
```
```

---

## Worked Example: Resolving Fuzzy Icons on Non-Retina Displays

- **Problem**: Icons appeared blurry on standard 1080p monitors because strokes were aligned on fractional sub-pixel coordinates (e.g. `x="12.5"`).
- **Remediation**: Snapped all anchor points and line centerlines to integer pixel boundaries on the 24px grid.
- **Result**: Icons rendered razor-sharp across all displays; rendering artifacts eliminated.

---

## Verification Checklist

- [ ] All icons built on a standardized grid (16x16px or 24x24px).
- [ ] Stroke weights, joins, and corner radii are 100% uniform across the library.
- [ ] Asymmetrical shapes are optically centered rather than geometrically centered.
- [ ] SVGs use `fill="currentColor"` or `stroke="currentColor"` for dynamic CSS styling.
- [ ] Cleaned with SVGO with zero embedded editor metadata.

---

## Anti-Patterns

- **Sub-Pixel Coordinate Drift**: Placing paths at `x=14.32px`, guaranteeing blurry anti-aliased edges.
- **Inconsistent Stroke Weights**: Mixing 1px, 1.5px, and 2px lines randomly within the same application.
- **Overly Complex Illustrations**: Trying to cram an entire computer desk illustration into a 16px icon.
