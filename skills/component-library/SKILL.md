---
name: component-library
last_reviewed: 2026-09-06
group: Design system
description: >-
  Design the component set with consistent structure, states and semantic naming. Use when
  creating reusable Figma components, variants, or design libraries.
---

# component-library

## Core Philosophy
A component library is not a random collection of buttons and modal components copied from tutorial repositories. A production component library is an ironclad, scalable UI contract between design and frontend engineering. Components must be structured with consistent anatomy, strict state matrices, accessible keyboard interactions, composable primitives, and 1:1 prop parity between Figma design components and React/Vue/Svelte code.

---

## 4-Step Component Library Architecture

### Step 1: Component Anatomy & Structural Hierarchy
1. **Deconstruct the Component Anatomy**:
   - Every complex component is composed of standard anatomical slots:
     - *Container / Wrapper*: Handles padding, surface background, border, and elevation.
     - *Leading Element*: Icon, avatar, or status badge.
     - *Content Area*: Label, description, children elements.
     - *Trailing Element*: Chevron, counter badge, action icon, or shortcut tag.

### Step 2: The Complete 7-State Matrix
1. **Mandatory State Coverage**:
   - Every interactive component (Button, Input, Select, Checkbox) must explicitly design and test **all 7 states**:
     - 1. **Default / Rest**: Standard resting appearance.
     - 2. **Hover**: Cursor over element (subtle lightness change).
     - 3. **Focused / Focus-Visible**: Keyboard focus ring active (2px high-contrast outline).
     - 4. **Pressed / Active**: Click/tap depressed state (scale down or deepened background).
     - 5. **Loading**: Interactive state locked, subtle spinner active, label preserved in DOM.
     - 6. **Disabled**: Pointer events disabled (`cursor: not-allowed`), contrast reduced.
     - 7. **Error / Invalid**: Border and label state flagged with semantic danger tokens and ARIA error messages.

### Step 3: Variants, Sizing & Prop Composability
1. **Variant Taxonomy**:
   - *Hierarchy Variants*: `primary`, `secondary`, `outline`, `ghost`, `destructive`.
   - *Size Ramps*: `sm` (32px height), `md` (40px height - default), `lg` (48px height).
2. **Prop Parity Between Figma & Code**:
   - Figma component variant names must match TypeScript component props verbatim:
     ```typescript
     interface ButtonProps extends React.ButtonHTMLAttributes<HTMLButtonElement> {
       variant?: 'primary' | 'secondary' | 'outline' | 'ghost' | 'destructive';
       size?: 'sm' | 'md' | 'lg';
       isLoading?: boolean;
       leadingIcon?: React.ReactNode;
       trailingIcon?: React.ReactNode;
     }
     ```

### Step 4: Headless Foundations & Accessibility Primitives
1. **Building on Battle-Tested Headless Engines**:
   - Do not reinvent dropdown focus management, ARIA popover positioning, and keyboard arrow navigation.
   - Build atop accessible headless primitives: **Radix UI**, **React Aria**, or **Floating UI**.
   - Ensure components pass complete keyboard audits (`Enter`, `Space`, `Escape`, Arrow navigation).

---

## Deliverable Format: Component Specification (`BUTTON-SPEC.md`)

```markdown
# Component Specification: Button (`<Button />`)

## 1. Anatomy & Layout
- **Layout Model**: Flexbox row, inline-flex, center aligned.
- **Gap**: 8px between icons and text label.
- **Border Radius**: 6px (`--radius-md`).

## 2. Variant & State Matrix
| Variant | Default BG | Hover BG | Active BG | Focus Ring | Text Color |
|---|---|---|---|---|---|
| `primary` | `--indigo-600` | `--indigo-700` | `--indigo-800` | 2px `--indigo-500` | `#ffffff` |
| `secondary` | `--slate-100` | `--slate-200` | `--slate-300` | 2px `--slate-400` | `--slate-900` |
| `destructive` | `--red-600` | `--red-700` | `--red-800` | 2px `--red-500` | `#ffffff` |
| `ghost` | `transparent` | `--slate-100` | `--slate-200` | 2px `--slate-400` | `--slate-800` |

## 3. Sizing Specifications
- **Small (`sm`)**: Height 32px | Padding 0 12px | Typography: 13px/18px
- **Medium (`md`)**: Height 40px | Padding 0 16px | Typography: 14px/20px
- **Large (`lg`)**: Height 48px | Padding 0 20px | Typography: 16px/24px

## 4. Accessibility & Keyboard Behavior
- Implements native `<button>` element.
- When `isLoading={true}`: Sets `aria-busy="true"` and `disabled`; spinner rendered without shifting button width.
```

---

## Worked Example: Design System Button Overhaul

- **Problem**: 14 different button styles existed across the web app with inconsistent focus states and layout jumping during loading spinners.
- **Solution**: Built a unified `<Button />` component on Radix UI primitives with 5 variants, 3 sizes, and fixed-width loading state overlays.
- **Outcome**: Eliminated 1,400 lines of duplicated CSS; zero layout shift on form submission.

---

## Verification Checklist

- [ ] Component satisfies all 7 states (Default, Hover, Focus, Active, Loading, Disabled, Error).
- [ ] TypeScript prop names match Figma component variants 1:1.
- [ ] Keyboard navigation and ARIA attributes tested via screen reader.
- [ ] Interactive heights adhere to touch target minimums (>= 40px for default).
- [ ] Documented in Storybook with visual regression test snapshots.

---

## Anti-Patterns

- **Div Buttons**: Using `<div onClick={...}>` instead of semantic `<button>`, breaking native keyboard focus and screen readers.
- **Layout-Shifting Loaders**: Replacing button text with a spinner that causes the button to shrink or grow on click.
- **Missing Focus Rings**: Forgetting the `:focus-visible` state, leaving keyboard navigators blind.
