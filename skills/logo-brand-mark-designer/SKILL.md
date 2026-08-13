---
name: logo-brand-mark-designer
description: >-
  Conceptualizes brand identity marks including logomarks, logotypes, brandmarks, and adaptive logo systems with usage guidelines. Use when creating brand identities, designing logo variants, or writing brand identity guidelines.
---

# Logo & Brand Mark Designer

A logo has to work at both a 16px favicon and a building-sized sign — that constraint should shape every design decision, not just be a checklist item at the end. Prioritize a form that survives radical size and color reduction over one that only looks good at presentation size.

## Workflow

1. **Get the essentials**: the name/initials to work with, the industry/category, and 2-3 adjectives describing the desired feel (e.g. "trustworthy, modern, understated" vs. "playful, bold, energetic") — these adjectives should directly drive shape and weight choices, not just inform a mood board.
2. **Pick a mark type matched to the brand's needs:**
   - **Wordmark** (full name, typographically distinctive) — works well when the name itself is short, memorable, and worth building recognition around directly.
   - **Lettermark** (initials) — useful for longer names where a full wordmark gets unwieldy at small sizes.
   - **Icon + wordmark combination** — most flexible for real-world use (the icon alone can serve as an app icon/favicon once recognition builds), but takes longer to build equity in the icon alone.
   - **Abstract/iconographic mark alone** — highest risk (no inherent name recognition until the brand builds it), but distinctive at scale once established. Only recommend this if the user has the marketing runway to build recognition, and say so.
3. **Design for reduction, not addition.** Start from the simplest version that still reads clearly, rather than starting complex and simplifying later — a mark that only works with fine detail won't survive small-size or single-color use.
4. **Test the mark mentally against real constraints**: does it still read as intended in pure black, at favicon size, and reversed on a dark background? Flag if a concept fails any of these rather than presenting it as finished.
5. **Explain the reasoning**, not just the shapes — why this weight, why this level of geometric vs. organic form, why this specific color if included — so the user can evaluate the concept against their actual brand intent, not just aesthetic preference.

## Technical constraints for SVG output

- Build with clean, minimal path data — avoid unnecessary anchor points, which bloat file size and complicate later edits.
- Use a **single, ideally even-odd-safe path** for a monochrome mark where possible, so it scales and recolors cleanly.
- Keep the design within a square or defined bounding box (e.g. 100x100 viewBox) so it's simple to place consistently across contexts.

## Anti-Patterns & Constraints

- Don't reproduce or closely imitate any real, identifiable existing brand's logo — even as a "starting point" or "inspired by" reference, per copyright and trademark boundaries.
- Don't over-design with gradients, complex shadows, or fine detail that won't survive single-color or small-size reproduction — a logo isn't an illustration.

## Output format

Provide the mark as clean SVG code, plus a short rationale (2-4 sentences) connecting the specific design choices back to the brand adjectives given. If presenting multiple concepts, keep them genuinely distinct in approach (e.g. one wordmark-led, one icon-led), not variations on the same idea.

## Verification & Quality Checklist

- [ ] Contrast and legibility verified at the smallest intended display size.
- [ ] Dimensions, bleed, and safe areas match the named output medium.
- [ ] Colour is never the sole carrier of meaning - icons or text accompany it.
- [ ] Asset licensing and font embedding rights confirmed for the intended use.
