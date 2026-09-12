---
name: accessibility-review
last_reviewed: 2026-09-06
group: Research and evaluation
description: >-
  Check a design for contrast, target size, focus order and motion safety before anything gets
  built. Use when auditing color contrast, focus states, tap targets, or ARIA UX.
---

# accessibility-review

## Core Philosophy
Accessibility (a11y) is not an afterthought compliance checklist to run the week before product launch. Accessibility is core design and software architecture. Designing for accessibility ensures that digital products are usable by people with visual, auditory, motor, and cognitive disabilities. Compliance with WCAG 2.2 (Level AA and AAA) is legally mandated under the Americans with Disabilities Act (ADA Title III) and European Accessibility Act (EAA).

---

## 4-Step Systematic Accessibility Review Protocol

### Step 1: Color Contrast & Visual Perception (WCAG 2.2 SC 1.4.3 / 1.4.11)
1. **Mathematical Contrast Ratios**:
   - *Body Text (< 18pt or < 14pt bold)*: Minimum **4.5:1** contrast ratio against background.
   - *Large Text (>= 18pt or >= 14pt bold)*: Minimum **3.0:1** contrast ratio.
   - *UI Components & Graphical Objects*: Active borders, form input outlines, and icons must meet **3.0:1** against adjacent background.
2. **Never Rely on Color Alone (SC 1.4.1)**:
   - Error states, status indicators, and chart lines must include text labels, icons, or distinct dash patterns in addition to color hues.

### Step 2: Touch Target Sizes & Spacing (SC 2.5.8)
1. **Target Dimensions**:
   - WCAG 2.2 Target Size (Minimum): At least **24x24 CSS pixels**, or sufficient spacing so a 24px diameter circle centered on each target does not overlap adjacent targets.
   - AAA / Native Standard: **44x44px** (Apple iOS HIG) and **48x48dp** (Google Material Design).
2. **Clickable Padding**:
   - Increase interactive bounding boxes using CSS `padding` while maintaining compact visual labels.

### Step 3: Keyboard Focus & Navigation Order
1. **Logical Tab Sequence (SC 2.4.3)**:
   - DOM order must match visual reading order (left-to-right, top-to-bottom).
   - Never use positive `tabindex` (`tabindex="1"`); use strictly `tabindex="0"` (natural focusable) or `tabindex="-1"` (programmatic focus).
2. **Focus Visible Indicators (SC 2.4.7 / 2.4.13)**:
   - Never remove outline with `outline: none` without providing a high-contrast replacement.
   - Enforce a visible focus ring: minimum 2px solid with >= 3:1 contrast against both the component and surrounding background.
3. **No Keyboard Traps (SC 2.1.2)**:
   - Users must be able to navigate into and out of modals, drawers, and dropdowns using exclusively `Tab`, `Shift+Tab`, and `Esc`.

### Step 4: Motion Sensitivity & Cognitive Load
1. **Motion Safety (SC 2.3.3)**:
   - Respect user OS settings via CSS media query:
     ```css
     @media (prefers-reduced-motion: reduce) {
       *, *::before, *::after {
         animation-duration: 0.01ms !important;
         transition-duration: 0.01ms !important;
       }
     }
     ```
2. **Three-Flash Threshold (SC 2.3.1)**:
   - Ensure no animation or strobe effect flashes more than 3 times in any 1-second period to prevent photosensitive seizures.

---

## Deliverable Format: Accessibility Audit Report (`A11Y-AUDIT.md`)

```markdown
# Accessibility (WCAG 2.2 AA) Audit: [Component / Page Name]

## 1. Executive Summary & Compliance Score
- **Page / Flow Evaluated**: Checkout & Payment Form
- **Standard**: WCAG 2.2 Level AA Compliance
- **Pass Rate**: 92% (23/25 criteria met | 2 P0 remediation blockers)

## 2. Identified Violations & Remediation Matrix
| Criterion | Severity | Element Selector | Issue Description | Required Code Fix |
|---|---|---|---|---|
| SC 1.4.3 | P0 (Critical) | `button.btn-secondary` | Gray text `#94A3B8` on white `#FFF` has 2.4:1 contrast | Darken text to `#475569` (5.4:1 ratio) |
| SC 2.4.7 | P0 (Critical) | `input.form-control` | `outline: none` hides focus indicator on keyboard tab | Add `focus-visible: ring-2 ring-indigo-500` |
| SC 2.5.8 | P1 (Medium) | `.icon-delete` | Trash icon target is 16x16px with 2px padding | Expand clickable target to 44x44px |

## 3. Screen Reader & ARIA Verification
- [x] Modal dialog includes `role="dialog"`, `aria-modal="true"`, and `aria-labelledby`.
- [x] Form inputs have explicit `<label for="...">` associations (no unlabelled placeholders).
- [x] Decorative icons marked with `aria-hidden="true"`.
```

---

## Worked Example: Checkout Modal a11y Remediation

- **Issue**: Modal had no keyboard focus trap; pressing `Tab` moved focus to background elements behind the overlay, while screen readers failed to announce modal opening.
- **Remediation**: Trapped focus within modal container; shifted initial focus to modal H2; added `Esc` key listener to close and return focus to triggering button.
- **Outcome**: Passed automated Axe tests and verified complete voiceover keyboard navigation with zero cursor usage.

---

## Verification Checklist

- [ ] All body text meets minimum 4.5:1 contrast ratio against background.
- [ ] Interactive touch targets measure >= 44x44px (or satisfy 24px spacing rule).
- [ ] Visible keyboard focus indicator (2px outline) active on all interactive elements.
- [ ] No positive `tabindex` attributes used in HTML.
- [ ] `prefers-reduced-motion` media query disables non-essential animations.

---

## Anti-Patterns

- **Outline Zero**: Writing `* { outline: none; }` in global CSS, making the site unusable for keyboard-only users.
- **Color-Only States**: Indicating form errors solely by changing an input border to red without an error text label or icon.
- **Unlabeled Icon Buttons**: Using `<button><svg>...</svg></button>` without an `aria-label` or visually hidden screen reader text.
