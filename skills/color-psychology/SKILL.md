---
name: color-psychology
group: Direction
description: >-
  Define color meaning: category conventions, emotional resonance, cultural symbolism, and owner
  gaps. Use when analyzing color psychology or brand palettes.
---

# color-psychology

## Core Philosophy
Color choice in product design and branding is not an arbitrary aesthetic preference. Colors carry profound cognitive, physiological, and cultural associations that influence perceived trust, urgency, and category positioning. Effective color psychology goes beyond pop-science clichés ("blue means trust") to analyze category conventions, identify uncontested competitive color gaps, and map emotional valence directly to user action states.

---

## 4-Step Color Psychology & Strategic Palette Mapping

### Step 1: Emotional & Functional Valence Mapping
1. **The Behavioral Semiotics of Color**:
   - *Blue (Navy / Cobalt / Electric)*: Stability, institutional trust, architectural rigor. (Default for enterprise B2B, cloud infrastructure, and traditional banking).
   - *Green (Emerald / Sage / Mint)*: Growth, liquidity, financial prosperity, health, affirmative success states.
   - *Purple / Violet (Iris / Amethyst)*: Intelligence, luxury, creative power, frontier AI capabilities.
   - *Orange / Amber (Tangerine / Copper)*: High energy, developer speed, warmth, non-blocking warning states.
   - *Red / Crimson*: Immediate urgency, critical danger, passion, stop actions, loss.
   - *Obsidian / Charcoal (Dark Slates)*: Premium craft, focus, executive authority, technical sophistication.

### Step 2: Category Competitive Landscape & The "Owner Gap"
1. **Mapping the Competitive Matrix**:
   - Audit the primary brand colors of the top 10 competitors in your software category.
   - Example (Cloud APM): Datadog (Purple), New Relic (Green), Dynatrace (Blue), Splunk (Orange).
2. **Exploiting the Uncontested Space**:
   - Do not pick a color identical to the category market leader (doing so surrenders brand recall).
   - Identify the "Owner Gap"—a distinct hue with positive category emotional resonance that no major incumbent currently owns.

### Step 3: Cultural Semiotics & Cross-Border Nuance
1. **Global Variations in Color Meaning**:
   - *Financial Markets*: In Western stock markets, Red = Loss / Decline, Green = Gain. In China, Taiwan, and East Asian exchanges, **Red = Gain / Prosperity**, Green = Loss.
   - *White*: Purity and minimalism in the West; traditional mourning and funerals in East Asia.
2. **Accessibility Overrides Emotion**:
   - Regardless of psychological intent, emotional colors must never compromise accessibility. Contrast thresholds (WCAG 4.5:1) always take precedence over emotional saturation.

### Step 4: Semantic Color Token Architecture
1. **Partitioning Brand from System Semantics**:
   - *Brand Colors*: Used for identity, marketing, and personality (1–2 primary hues).
   - *Functional / Semantic UI Colors*: Universal operational meanings that must remain immutable across products:
     - Success: Green (e.g. `#10B981`)
     - Warning: Amber / Yellow (e.g. `#F59E0B`)
     - Danger / Error: Red (e.g. `#EF4444`)
     - Info: Blue (e.g. `#3B82F6`)
   - Never use your brand color as an error state unless your brand color is red (and even then, keep semantic tokens distinct).

---

## Deliverable Format: Color Strategy & Psychology Specification (`COLOR-STRATEGY.md`)

```markdown
# Color Psychology & Strategic Positioning: [Product Name]

## 1. Category Audit & Competitive Color Mapping
- **Category**: High-Performance Cloud Database
- **Competitor A (Leader)**: Azure Blue (#0078D4) -> Institutional, corporate
- **Competitor B**: Green (#00ED64) -> Fast, modern
- **Competitor C**: Bright Orange (#FF6B00) -> Dynamic, chaotic
- **The Owner Gap**: **Deep Violet / Electric Indigo (#6366F1)** — Unclaimed; signals mathematical precision and deep AI intelligence.

## 2. Emotional & Behavioral Rationale
- **Primary Brand Color**: Obsidian Slate (`#0B0F19`) + Electric Indigo (`#6366F1`)
- **Psychological Thesis**: Deep slate minimizes eye fatigue for developer night coding; indigo accent creates an aura of sophisticated, high-compute intelligence without looking like a legacy corporate bank.

## 3. Semantic UI Color Mappings
| Functional Role | Semantic Token | Color Code | Behavioral Intent |
|---|---|---|---|
| Success | `--color-feedback-success` | `#059669` (Emerald 600) | Validates build completion |
| Warning | `--color-feedback-warning` | `#D97706` (Amber 600) | Flags approaching query limits |
| Danger | `--color-feedback-danger` | `#DC2626` (Red 600) | Hard stops table-drop queries |
| Neutral Action | `--color-action-secondary` | `#475569` (Slate 600) | Routine configuration |
```

---

## Worked Example: Fintech Color Strategy Pivot

- **Context**: A personal wealth management app used bright red for negative transaction amounts and budget alerts.
- **Issue**: User research revealed the frequent red badges triggered acute financial anxiety, causing users to avoid opening the app.
- **Solution**: Replaced harsh red with a neutral charcoal strike-through for normal expenses; reserved red strictly for catastrophic overdraft warnings.
- **Outcome**: 30-day user retention increased 22%; daily app opens grew 34%.

---

## Verification Checklist

- [ ] Category competitor color audit completed and "owner gap" identified.
- [ ] Brand colors are strictly decoupled from functional UI semantic tokens (Success, Warning, Danger).
- [ ] Cultural color semiotics reviewed for all core geographic target markets.
- [ ] All chosen color pairings meet WCAG AA 4.5:1 contrast standards.
- [ ] Palette tested in both light and dark mode contexts.

---

## Anti-Patterns

- **Copying the Incumbent**: Adopting "Salesforce Blue" for a new CRM, blending into the incumbent's shadow.
- **Using Red for Brand Buttons**: Choosing bright red as your primary CTA button color, making users feel like they are triggering an emergency alarm.
- **Ignoring Saturation Fatigue**: Using 100% saturated neon colors for large surface backgrounds, inducing severe visual fatigue.
