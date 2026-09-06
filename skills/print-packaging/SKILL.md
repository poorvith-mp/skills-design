---
name: print-packaging
group: Brand
description: >-
  Produce print-ready packaging with bleed, die lines, CMYK/Pantone profiles and material specs.
  Use when designing physical packaging, die-lines, CMYK swag, or print assets.
---

# print-packaging

## Core Philosophy
Print and packaging design is governed by unforgiving physical and chemical realities. In digital design, a broken pixel can be patched in production in 3 minutes; in physical packaging, a 1mm alignment error on a die-line or an unconverted RGB color profile ruins a $50,000 production run of 10,000 physical boxes. Professional print engineering requires exact die-line mechanics, bleed and safety margin discipline, Pantone/CMYK color conversions, high-resolution vector assets, and material substrate awareness.

---

## 4-Step Physical Packaging & Print Engineering

### Step 1: Die-Line Engineering & Structural Geometry
1. **The Vector Die-Line Layer**:
   - Create a dedicated top-level layer named `DIE-LINE` set to a distinct non-printing **Spot Color** (typically 100% Magenta named `Dieline`).
   - Set stroke to **Overprint Stroke** so the die-line does not knock out underlying background artwork.
2. **The 3 Die-Line Stroke Styles**:
   - *Solid Line*: Cut line (where the physical metal blade cuts through the paperboard).
   - *Dashed Line*: Score / Crease line (where the paperboard folds).
   - *Dotted Line*: Perforation line (tear strips).
3. **Flap Geometry & Glue Tabs**:
   - Account for tuck flaps, dust flaps, and glue tabs (minimum 12–15mm glue flap width for structural carton integrity).

### Step 2: Bleed, Trim & Safety Margin Discipline
1. **The 3 Critical Boundary Lines**:
   - *Trim Line*: The exact dimension of the finished physical cut product.
   - *Bleed Line (Exterior)*: Artwork must extend at least **3mm (0.125 inches)** past the trim line on all sides. For heavy corrugated boxes, extend to **6mm (0.25 inches)**.
   - *Safety / Live Margin (Interior)*: All critical text, barcodes, and logos must remain at least **3mm to 5mm** inside the trim line to prevent being trimmed off by mechanical blade drift.

### Step 3: Color Models: CMYK, Pantone (PMS) & Rich Black
1. **RGB vs CMYK Conversion**:
   - All raster images and colors must be converted to **CMYK** (e.g. `ISO Coated v2` or `GRACoL 2006`). Neon RGB colors will shift and muddy in 4-color process printing.
2. **Pantone Matching System (PMS)**:
   - For exact brand color fidelity, use specified Pantone Spot Colors (e.g. *Pantone Reflex Blue C*).
3. **The Rich Black Formula**:
   - Never use 100% K (`C:0 M:0 Y:0 K:100`) for large background floods—it prints as dull, washed-out charcoal.
   - Use **Rich Black** for dark backgrounds:
     $$C: 60\% \quad M: 40\% \quad Y: 40\% \quad K: 100\% \quad (text{Total Ink Limit } = 240\%)$$
   - Use 100% Plain Black (`C:0 M:0 Y:0 K:100`) strictly for small body text to prevent four-color registration misalignments.

### Step 4: Resolution, Barcodes & Pre-Flight Verification
1. **Resolution & Vector Standards**:
   - All raster images must be strictly **300 DPI (or PPI)** at 100% final physical print size.
   - Convert all typography to vector outlines (`Type -> Create Outlines`) prior to export to eliminate missing font errors.
2. **GS1 Barcode Compliance**:
   - Barcodes (UPC / EAN-13) must be printed at 100% black on a crisp white background with official quiet zones ($\ge 3.63text{mm}$ blank space on left and right sides).

---

## Deliverable Format: Print Packaging Production Spec (`PACKAGING-SPEC.md`)

```markdown
# Physical Packaging Production Specification: [Product Box]

## 1. Box Specifications & Substrate
- **Box Style**: Straight Tuck End (STE) Folding Carton
- **Finished Dimensions**: 120mm (W) x 180mm (H) x 45mm (D)
- **Substrate Material**: 18pt SBS (Solid Bleached Sulfate) Paperboard (350 GSM)
- **Finish / Coating**: Soft-touch matte lamination + Spot UV on primary logo

## 2. Print Mechanics & Geometry
- **Bleed Allowance**: 3.0mm (0.125 in) past trim
- **Safety Margin**: 5.0mm inside all cut and crease lines
- **Die-Line Layer**: Vector Spot Color `Dieline` (Overprint enabled)

## 3. Color Separation Matrix
| Color Plate | Formulation | Usage Context |
|---|---|---|
| Process Cyan | Standard Cyan | 4-Color photographic imagery |
| Process Magenta | Standard Magenta | 4-Color imagery |
| Process Yellow | Standard Yellow | 4-Color imagery |
| Process Black | Standard Black | Text typography & photographic darks |
| Spot Color 1 | **Pantone 286 C** | Primary brand logo & accent borders |
| Rich Black (Floods)| C:60 M:40 Y:40 K:100 | Outer box flood background |

## 4. Pre-Flight Checklist
- [x] All fonts converted to vector outlines.
- [x] All images verified >= 300 DPI at full scale.
- [x] Barcode verified: EAN-13 with compliant quiet zones.
- [x] Exported to PDF/X-4:2010 standard with trim and bleed marks.
```

---

## Worked Example: Preventing a $30,000 Print Run Failure

- **Issue**: Pre-flight audit caught an artwork file using pure RGB neon green `#00FF00` on a dark background flood with zero bleed.
- **Remediation**: Converted green to a dedicated Pantone 802 C spot plate; expanded background artwork 3.5mm past the die cut line; adjusted black background to Rich Black (`60/40/40/100`).
- **Outcome**: Box printed with vibrant brand color accuracy and razor-sharp borders; zero production delays.

---

## Verification Checklist

- [ ] Bleed extends minimum 3mm (0.125 in) past all trim boundaries.
- [ ] Safety margin keeps critical text >= 5mm inside fold and cut lines.
- [ ] Die-line resides on a separate overprinted spot color layer.
- [ ] All raster assets verified at $\ge 300text{ DPI}$ in CMYK color mode.
- [ ] All fonts converted to vector outlines in final print-ready PDF/X export.

---

## Anti-Patterns

- **Submitting RGB Files**: Sending RGB images to an offset printer, producing murky brown color shifts.
- **Zero Bleed Artwork**: Cropping artwork exactly at the cut line, resulting in white paper edges when the cutting blade shifts 0.5mm.
- **Small Text in Rich Black**: Printing 8pt body text in 4-color Rich Black, resulting in blurry, misregistered text halos.
