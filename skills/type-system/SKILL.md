---
name: type-system
group: Design system
description: >-
  Build the type scale, font pairing, hierarchy rules, line height and vertical rhythm. Use when
  defining typographic scales, modular ratios, fonts, or line-heights.
---

# type-system

## Core Philosophy
Typography is the voice of the interface. Over 90% of user interaction on the web is reading text. A type system is not simply choosing an attractive Google Font; it is a mathematical and architectural framework governing visual hierarchy, modular scale ratios, optical line-heights, character measure (line length), and vertical rhythm. A broken type system produces illegible text walls, disjointed heading hierarchies, and severe cognitive reader fatigue.

---

## 4-Step Typographic System Architecture

### Step 1: The Modular Scale & Type Ramp
1. **Mathematical Modular Scales**:
   - Choose a single modular ratio based on content density:
     - *Major Second (1.125)*: Ultra-dense dashboards, IDEs, data tables.
     - *Major Third (1.250)*: Modern software interfaces, web apps (Balanced standard).
     - *Perfect Fourth (1.333)*: Marketing pages, editorial blogs (High-contrast drama).
2. **Generating the Type Ramp (Base 16px @ Major Third 1.25)**:
   - `caption`: $16 / 1.25 = 12.8text{px} pprox 13text{px}$
   - `body-sm`: $14text{px}$
   - `body-base`: $16text{px}$ (The 1rem baseline)
   - `h4`: $16  imes 1.25 = 20text{px}$
   - `h3`: $20  imes 1.25 = 25text{px}$
   - `h2`: $25  imes 1.25 = 31.25text{px} pprox 31text{px}$
   - `h1`: $31.25  imes 1.25 = 39.06text{px} pprox 39text{px}$
   - `display`: $39.06  imes 1.25 = 48.8text{px} pprox 49text{px}$

### Step 2: Line-Height (Leading) & Vertical Rhythm
1. **Inverted Line-Height Principle**:
   - As font size increases, line-height ratio must **decrease**:
     - Body Text ($16text{px}$): Line-height **$1.5 - 1.6$** ($24text{px} - 26text{px}$). Generous space allows the eye to track long sentences.
     - Subheadings ($24text{px}$): Line-height **$1.3$** ($32text{px}$).
     - Display Headings ($48text{px}$): Line-height **$1.1 - 1.15$** ($54text{px}$). Tight leading keeps multi-line headlines visually bound as a single unit.

### Step 3: Measure (Line Length) & Letter-Spacing (Tracking)
1. **The 45–75 Character Measure Rule**:
   - The optimal line length for reading comprehension is **45 to 75 characters** (including spaces).
   - Constrain body text containers with CSS: `max-width: 65ch`.
   - Never let body text span unconstrained across a 1920px widescreen monitor.
2. **Dynamic Letter-Spacing (Tracking)**:
   - Large display headlines: Apply subtle negative tracking (`letter-spacing: -0.02em` to `-0.03em`) to tighten optical gaps.
   - Small uppercase labels / tags: Apply positive tracking (`letter-spacing: +0.05em` to `+0.08em`) to preserve character legibility.

### Step 4: Font Pairing & System Fallback Stacks
1. **Classification Contrast**:
   - Pair across distinct font classifications to avoid visual discord:
     - Primary UI / Display: Clean Geometric Sans (`Inter`, `Geist`, `Plus Jakarta Sans`).
     - Data / Code: Monospace (`JetBrains Mono`, `Fira Code`).
     - Editorial / Long-Form: Modern Humanist Serif (`Newsreader`, `Charter`).
2. **Robust System Fallbacks (Preventing Layout Shift - CLS)**:
   - Always include system fallback stacks to prevent Cumulative Layout Shift:
     ```css
     font-family: 'Geist', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
     font-family: 'JetBrains Mono', SFMono-Regular, Menlo, Monaco, Consolas, monospace;
     ```

---

## Deliverable Format: Typographic Scale Specification (`TYPE-SYSTEM.md`)

```markdown
# Typographic System Architecture: [Product Name]

## 1. Font Family Stacks
- **Primary Interface**: `Inter`, system-ui, -apple-system, sans-serif
- **Code & Telemetry**: `JetBrains Mono`, monospace
- **Editorial / Story**: `Newsreader`, Georgia, serif

## 2. Master Typographic Scale (Major Third 1.250)
| Level | Font Size | Line Height | Letter Spacing | Weight | Usage |
|---|---|---|---|---|---|
| `display` | 48px (3.0rem) | 52px (1.08) | -0.03em | 700 Bold | Hero banner headlines |
| `h1` | 36px (2.25rem) | 42px (1.16) | -0.025em | 700 Bold | Primary page titles |
| `h2` | 28px (1.75rem) | 34px (1.21) | -0.02em | 600 SemiBold | Section headers |
| `h3` | 22px (1.375rem) | 28px (1.27) | -0.01em | 600 SemiBold | Card titles / Subheadings |
| `body-base` | 16px (1.0rem) | 24px (1.50) | 0 | 400 Regular | Standard body paragraphs |
| `body-sm` | 14px (0.875rem) | 20px (1.42) | 0 | 400 Regular | Form inputs, table rows |
| `caption` | 12px (0.75rem) | 16px (1.33) | +0.02em | 500 Medium | Timestamps, badge pills |

## 3. Structural Measure Constraints
- Paragraph container max-width: `max-width: 65ch;`
- Heading container max-width: `max-width: 25ch;`
```

---

## Worked Example: Fixing Unreadable Documentation Typography

- **Problem**: Engineering docs were unreadable on widescreen monitors; users complained of headaches.
- **Diagnosis**: Line length stretched across 1,400px (180 characters per line); line-height was set to a tight 1.2 on 14px body text.
- **Remediation**: Set `max-width: 68ch` on prose containers; increased body font to 16px with line-height 1.6 (26px); adjusted code blocks to 14px JetBrains Mono.
- **Outcome**: Time-on-page increased 62%; reader completion rate doubled.

---

## Verification Checklist

- [ ] Typographic scale follows a consistent mathematical modular ratio.
- [ ] Line-height decreases progressively as font size increases.
- [ ] Body prose containers are constrained to 45–75 characters (`max-width: 65ch`).
- [ ] Large headings use subtle negative tracking; small uppercase text uses positive tracking.
- [ ] Font stacks include zero-shift system fallbacks to prevent CLS.

---

## Anti-Patterns

- **180-Character Line Sprawls**: Letting body text run full width on a 4K display.
- **Too Many Font Sizes**: Using 17 random font sizes across a web app instead of sticking to the defined ramp.
- **Tall Line-Height on Headings**: Giving a 48px heading a 1.6 line-height (76px), causing titles to look disconnected.
