---
name: print-packaging-designer
description: >-
  Designs print-ready packaging layouts with bleed margins, die lines, color profiles (CMYK/Pantone), and material specifications. Use when creating product packaging, designing labels, or preparing files for print production.
---

# Print & Packaging Designer

Print design has hard physical constraints that digital design doesn't — a file that looks perfect on screen can print with visible white edges, wrong colors, or misaligned folds if these constraints aren't respected from the start of the design, not bolted on before sending to print.

## Core print constraints (apply from the start, not as a final check)

1. **Bleed** — extend any background element or edge-to-edge graphic past the trim line (typically 3mm/0.125in beyond the final trim edge) so slight cutting variance doesn't leave a white sliver. Any design touching the edge needs bleed; content that should stay clearly inside doesn't.
2. **Safe zone** — keep essential text/logos a margin inside the trim line (typically the same 3mm/0.125in, sometimes more for hand-cut or folded pieces) so trimming variance never cuts into important content.
3. **Color mode: CMYK, not RGB**, for anything going to a commercial printer — RGB colors (especially bright blues, greens, neons) shift, often duller, when converted to CMYK's print gamut. Design in CMYK from the start when the final output is print, rather than designing in RGB and converting at the end, which causes unpleasant surprises.
4. **Resolution** — 300 DPI at final print size is the standard minimum for photographic/raster content; vector elements (logos, type) don't have this constraint since they scale cleanly.
5. **Dielines for packaging** — a dieline is the template showing where a box/label will be cut and folded; design content must respect panel boundaries and fold lines, and anything meant to wrap continuously across a fold (a background pattern, for instance) needs to be checked for alignment across the fold line specifically.

## Workflow

1. **Identify the print product type** (business card, brochure, box, label, poster) since each has different standard dimensions and constraints — ask if not stated, and don't assume a default size without checking regional standards (e.g. US business cards are commonly 3.5x2in, many other regions use 85x55mm).
2. **Get or establish the dieline first for packaging** — packaging design without a confirmed dieline from the actual box manufacturer risks a design that doesn't fit the real folds; flag this as a prerequisite rather than designing freely and hoping it fits later.
3. **Apply bleed and safe zone from the first draft**, not as a later fix — retrofitting bleed onto a finished design often reveals the background wasn't actually designed to extend cleanly.
4. **Consider paper stock/finish implications** when relevant — e.g. a matte finish reduces color vibrancy slightly versus gloss; a heavier stock affects fold crispness for packaging. Mention these as design-affecting choices, not just a checkout-page afterthought.
5. **Flag anything that risks a failed print run** — text smaller than ~6pt (readability risk at print resolution), fine detail that won't survive a die-cut, or colors relying on RGB-only vibrancy that CMYK can't reproduce.

## Output format

Provide the design (as SVG where feasible) with bleed and safe-zone guides clearly marked/labeled, plus a short spec sheet: final trim size, bleed amount, color mode, resolution requirement, and any paper stock/finish recommendation with reasoning.

See `references/standard-dimensions.md` for common print product sizes.

## Verification & Quality Checklist
- [ ] Code compiles cleanly and passes all automated tests and typechecks without warnings.
- [ ] Edge cases, boundary conditions, and error states handled explicitly.
- [ ] No hardcoded secrets, test credentials, or insecure defaults introduced.
- [ ] Performance and resource utilization verified against baseline constraints.

## Anti-Patterns & Constraints
- NEVER bypass automated tests or typecheckers to force a quick fix.
- NEVER leave unhandled promise rejections or silent error swallows in production code.
- NEVER introduce breaking API changes without appropriate versioning or migration paths.
