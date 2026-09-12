---
name: design-taste
last_reviewed: 2026-09-06
group: Research and evaluation
description: Find and fix AI design signatures: gradient blobs, three identical cards, purple-on-white. Not for prose (see writing-taste). Use when eliminating generic AI design tropes and templates.
---

# design-taste

## Core Philosophy
Large language models and automated design tools naturally drift toward the generic average of the internet. The result is synthetic "AI slop" in UI design: oversized purple-to-cyan gradient blobs, identical three-column rounded feature cards, floating 3D holographic spheres, generic illustrated characters waving at laptops, and blinding white space with zero informational density. Design taste is the deliberate craft of human discernment: eliminating AI clichés, enforcing asymmetric balance, prioritizing data density, and designing for authentic utility.

---

## 4-Step Anti-AI Design Sanitization Protocol

### Step 1: The Banned AI Design Cliché Registry
1. **The Instant-Kill UI Tropes**:
   - *The Purple/Cyan Gradient Blob*: Giant blurred radial gradients floating uselessly in the background.
   - *The Triplet Feature Card Layout*: Three identical rounded cards with an icon in a colored circle, a bold 3-word title, and 2 lines of generic text.
   - *Floating 3D Glassmorphism*: Translucent frosted glass spheres or cubes with fake refraction that communicate zero information.
   - *Corporate Memphis / Startup Cartoon Art*: Featureless pastel vector humans with oversized limbs celebrating next to an abstract graph.
   - *Meaningless Glow Effects*: Glowing neon border outlines on every card.

### Step 2: Asymmetrical Composition & Dynamic Layouts
1. **Breaking the Grid Boredom**:
   - Replace the predictable 3-column card grid with **Bento Grid** layouts or asymmetric hierarchy:
     - 1 large anchor feature card (60% width) showcasing live interactive product UI.
     - 2 stacked secondary capability cards (40% width) displaying raw code or benchmark telemetry.
   - Vary visual rhythm across sections: juxtapose high-density data tables against focused text quotes.

### Step 3: Informational Density & Authentic Proof
1. **Show the Real Product**:
   - Eliminate abstract illustrations. Show the actual interface:
     - Real syntax-highlighted code blocks.
     - Real CLI terminal sessions with authentic output logs.
     - High-density data tables with genuine metrics (no placeholder `Lorem Ipsum` or `User 123`).
2. **Micro-Typography & Precision Borders**:
   - Replace bloated 24px container padding with crisp 12px or 16px padding for high-density tools.
   - Use crisp 1px borders with subtle contrast (`border: 1px solid rgba(255, 255, 255, 0.08)`) instead of heavy blurry drop shadows.

### Step 4: The 10-Second "AI Slop" Turing Test
1. **The Evaluation Question**:
   - Look at the design for 10 seconds and ask: *"Could an automated template generator have created this in 2 seconds?"*
   - If the answer is yes, strip the ornamentation and redesign around the product's primary functional data flow.

---

## Deliverable Format: Design Taste & Anti-Slop Audit (`DESIGN-TASTE-AUDIT.md`)

```markdown
# Design Taste & Anti-AI Slop Audit: [Page / App Name]

## 1. Slop Density Score
- **Generic AI Tropes Identified**: 4 critical violations
- **Information Density Rating**: 3/10 (Low - too much empty space)
- **Authenticity Rating**: 4/10 (Abstract illustrations used instead of real UI)

## 2. Identified Clichés & Architectural Remediations
| Element | The AI Slop Offense | Remediation Plan |
|---|---|---|
| Hero Section | Giant purple-to-pink gradient blob behind headline | Remove blob. Replace with a live interactive terminal emulator running CLI demo. |
| Feature Section | 3 identical rounded cards with generic icons | Rebuild as an asymmetric Bento Grid: 1 large card showing live table + 2 metric cards. |
| Graphics | Abstract 3D floating glass spheres | Replace with clean, vector architectural data-flow diagram. |
| Spacing | Excessive 64px padding between tiny text blocks | Tighten vertical rhythm; increase information density by 40%. |

## 3. Before-and-After Layout Shift
- **Before**: 3 identical cards with stock icons: "Fast", "Secure", "Scalable".
- **After**: Bento grid showing actual p99 latency benchmark chart (Fast), SOC 2 compliance control badges (Secure), and autoscaling node graph (Scalable).
```

---

## Worked Example: Overhauling an AI-Generated Landing Page

- **Original Design**: Produced by an AI site generator: white background, pastel purple blobs, 3 feature cards, generic stock cartoon illustrations.
- **Tasteful Redesign**: Dark slate theme, monospace typography for technical metrics, authentic code diff component in hero section, crisp 1px borders, zero floating blobs.
- **Result**: Conversion rate on demo signup jumped from 2.1% to 6.8%; developer feedback praised the clean, professional aesthetic.

---

## Verification Checklist

- [ ] All floating gradient blobs and meaningless background glows are purged.
- [ ] Three-identical-card grids are replaced with asymmetric or Bento layouts.
- [ ] Abstract illustrations are replaced with real product screenshots or code.
- [ ] Spacing and typography support high information density.
- [ ] Borders and surfaces communicate clean hierarchy without muddy glassmorphism.

---

## Anti-Patterns

- **Decorative Fluff**: Adding visual elements that serve no informational or navigational purpose.
- **The Dribbble Syndrome**: Designing an interface that looks pretty in a tiny screenshot but is completely unusable with real data.
- **Copying Generic SaaS**: Building another clone of an overused UI kit that makes your product look indistinguishable from 500 failed startups.
