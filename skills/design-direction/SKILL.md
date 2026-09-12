---
name: design-direction
last_reviewed: 2026-09-06
group: Direction
description: >-
  Choose the visual genre fitting product and audience: editorial, brutalist, swiss, retro,
  soft-tech. Use when establishing visual direction or moodboards.
---

# design-direction

## Core Philosophy
Visual design direction is not choosing random colors from a moodboard on Pinterest. Design direction is the deliberate selection of an architectural visual genre that directly reinforces product credibility, audience expectations, and functional utility. Choosing the wrong visual direction—such as wrapping a serious database monitoring tool in a whimsical, pastel cartoon aesthetic—destroys market trust and sabotages conversion.

---

## 4-Step Strategic Design Direction Framework

### Step 1: Visual Genre Taxonomy
1. **The 5 Contemporary Digital Design Genres**:
   - *1. Swiss / International Typographic*:
     - Characteristics: Rigid grid alignment, stark sans-serif typography (`Inter`, `Helvetica`), asymmetrical balance, high contrast, zero ornamental fluff.
     - Best For: Developer platforms, cloud infra, high-density financial analytics.
   - *2. Editorial / High-Craft*:
     - Characteristics: Elegant serifs (`Newsreader`, `Canela`), generous whitespace, rich muted paper tones, journalistic photography.
     - Best For: Publishing platforms, thought leadership, intellectual tools, boutique SaaS.
   - *3. Neo-Brutalist*:
     - Characteristics: High-contrast 2px solid black borders, hard drop shadows (`4px 4px #000`), bold un-rounded buttons, vibrant primary colors, raw exposed structure.
     - Best For: Developer tools challenging bloated incumbents, Gen-Z creator tools, subversive apps.
   - *4. Soft-Tech / Minimal Ambient*:
     - Characteristics: Subtle gradient blurs, deep slate obsidian surfaces, fine 1px translucent borders (`rgba(255,255,255,0.08)`), micro-elevations.
     - Best For: AI platforms, modern productivity software (Linear, Raycast).
   - *5. Retro-Computing / Terminal*:
     - Characteristics: Monospace typography, CRT scan-lines, dark green/amber monochrome palettes, ASCII art box borders.
     - Best For: Hacker tools, cybersecurity platforms, low-level systems utilities.

### Step 2: Product & Audience Alignment Matrix
1. **The Persona-to-Genre Fit**:
   - Who is evaluating the tool?
     - Enterprise Security Chief -> Swiss or Soft-Tech (Signals rigor and compliance).
     - Individual Backend Hacker -> Terminal or Neo-Brutalist (Signals speed and anti-corporate posture).
     - Creative Director -> Editorial or Experimental.

### Step 3: Curated Moodboarding & Token Synthesis
1. **The Anti-Pinterest Moodboard Discipline**:
   - Collect 8–12 real-world artifacts: physical architecture, print magazine layouts, vintage computing hardware, and top-tier digital interfaces.
   - Extract the DNA: Typography weights, surface border radius, color contrast, and spacing density.

### Step 4: Concept Spikes & The Direction Matrix
1. **Generate 2 Radically Contrasting Concepts**:
   - Never design just 1 visual direction. Create 2 distinct design spikes for the core screen:
     - Direction A: Restrained Swiss / Monochromatic.
     - Direction B: Ambient Soft-Tech / High Contrast.
   - Put both in front of target users to test comprehension, speed, and trust.

---

## Deliverable Format: Visual Design Direction Brief (`DESIGN-DIRECTION.md`)

```markdown
# Visual Design Direction Specification: [Product Name]

## 1. Selected Visual Genre: **Swiss Industrial / High-Density**
- **Core Aesthetic**: Stark, grid-disciplined, utilitarian, high-contrast.
- **Target Audience**: Infrastructure engineers, database administrators.
- **Brand Feeling**: Precise, unpretentious, lightning-fast, dependable.

## 2. Foundational Design Primitives
- **Grid Structure**: 8px baseline grid; 12-column responsive layout.
- **Border Radius**: Sharp 4px radius on all containers; 0px on tables.
- **Borders**: 1px solid high-contrast dividers (`#27272A`).
- **Typography**: Monospace data display (`JetBrains Mono`); Sans-serif labels (`Inter`).
- **Surface Elevation**: Dark slate `#090D16` canvas with crisp `#18181B` card containers.

## 3. Competitive Visual Differentiation
- Competitors all use generic light-purple SaaS templates with stock 3D floating icons.
- Our direction uses authentic terminal captures, dense monospace telemetry tables, and stark black-and-white contrast with single emerald status indicators.
```

---

## Worked Example: Database Tool Visual Direction Selection

- **Challenge**: Database startup originally used soft pastel purple gradients; customers questioned whether the database could handle high-throughput enterprise workloads.
- **Pivot**: Shifted visual direction to Swiss Industrial: deep charcoal background, sharp 2px corners, high-density data tables, and stark neon-amber status indicators.
- **Impact**: Enterprise pilot conversions increased 40%; customers remarked that the software felt "solid as industrial steel".

---

## Verification Checklist

- [ ] Chosen visual genre explicitly matches audience persona and cognitive needs.
- [ ] At least 2 contrasting visual directions were developed and evaluated.
- [ ] Border radius, border stroke, typography, and spacing density are codified.
- [ ] Direction provides visible contrast against generic category competitor tropes.
- [ ] Direction supports high-density information architecture without legibility loss.

---

## Anti-Patterns

- **Designing in a Vacuum**: Picking a trendy aesthetic from Twitter/Dribbble that contradicts the software's functional utility.
- **The Generic Purple Blob**: Defaulting to purple gradients and floating 3D spheres for every B2B application.
- **Aesthetic Over Density**: Prioritizing huge whitespace and giant typography on an analytics dashboard where users need to see 50 rows of data.
