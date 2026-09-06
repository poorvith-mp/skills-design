---
name: motion-design
group: Interface
description: >-
  Specify UI animation and motion graphics: what moves, easing, timing, audio sync points and
  export settings. Use when designing UI transitions, spring physics, or micro-interactions.
---

# motion-design

## Core Philosophy
Motion design in software interfaces is not entertainment; it is cognitive spatial guidance and functional choreography. Unrestrained, sluggish animations make products feel bloated, slow, and amateur. Purposeful motion design operates under strict physical principles: establishing spatial continuity across screens, providing immediate tactile response to user touch, communicating state shifts, and adhering to strict timing budgets ($< 300text{ms}$) with spring physics.

---

## 4-Step UI Motion Design Engineering

### Step 1: Functional Roles of Motion
1. **The 3 Legitimate Purposes of UI Motion**:
   - *1. Spatial Continuity & Hierarchy*: Explaining where an element came from and where it went (e.g. clicking a card expands the card to fill the screen, rather than abruptly jumping).
   - *2. Feedback & Status Confirmation*: Proving the system registered input (button depress, checkmark morph, pull-to-refresh tension).
   - *3. Focus & Attention Direction*: Guiding the user’s eye to a high-priority change (subtle notification slide-in, badge pulse).

### Step 2: Timing Durations & Velocity Budgets
1. **The 300ms Rule**:
   - Micro-interactions (toggles, buttons, tooltips): **100–150ms**.
   - Standard UI components (dropdowns, accordions, toasts): **200–250ms**.
   - Full-screen transitions (modals, route changes, drawers): **250–350ms**.
   - Any animation exceeding **400ms** feels sluggish and induces user rage.

### Step 3: Easing Curves & Natural Spring Physics
1. **Why Linear Motion Fails**:
   - Nothing in the physical world moves at constant linear velocity and stops instantaneously. Linear motion feels mechanical, cheap, and unnatural.
2. **Cubic-Bezier Easing Standards**:
   - *Decelerate (Ease-Out - Entrances)*: Elements entering the screen start fast and decelerate to a stop:
     `cubic-bezier(0.0, 0.0, 0.2, 1)` or `cubic-bezier(0.16, 1, 0.3, 1)`
   - *Accelerate (Ease-In - Exits)*: Elements exiting the screen start slow and accelerate off-screen:
     `cubic-bezier(0.4, 0.0, 1, 1)`
3. **Spring Physics Parameters**:
   - Strive for critically damped or slightly under-damped springs:
     - Stiffness: $300 - 400$
     - Damping: $25 - 35$ (Clean snap with zero lingering wobble).

### Step 4: Orchestrated Choreography & Accessibility
1. **Staggered Sequences**:
   - When revealing lists or grids, stagger children by **20–30ms** per item (maximum 6 items staggered; items 7+ appear simultaneously to prevent total animation time exceeding 300ms).
2. **Mandatory Reduced Motion Safeguards**:
   - Always provide an instant cut fallback for users with vestibular disorders:
     ```css
     @media (prefers-reduced-motion: reduce) {
       .animated-element {
         transition: none !important;
         animation: none !important;
         opacity: 1 !important;
         transform: none !important;
       }
     }
     ```

---

## Deliverable Format: Motion Choreography Specification (`MOTION-SPEC.md`)

```markdown
# UI Motion & Animation Specification: [Component / Flow Name]

## 1. Transition: Modal Dialog Entry & Exit
- **Trigger**: Click "New API Key" button
- **Motion Role**: Spatial focus elevation

### Entry Animation
- **Properties**: `opacity: 0 -> 1` | `transform: scale(0.95) translateY(8px) -> scale(1) translateY(0)`
- **Duration**: 200ms
- **Easing**: `cubic-bezier(0.16, 1, 0.3, 1)` (Decelerate curve)

### Exit Animation
- **Properties**: `opacity: 1 -> 0` | `transform: scale(1) -> scale(0.98)`
- **Duration**: 150ms
- **Easing**: `cubic-bezier(0.4, 0, 1, 1)` (Accelerate curve)

## 2. Staggered List Reveal (Dashboard Metric Cards)
- **Item Count**: 4 cards
- **Base Duration**: 220ms per card
- **Stagger Offset**: 25ms delay between cards (Total sequence time: 295ms)
- **Physics**: Spring (`stiffness: 350`, `damping: 30`)

## 3. Accessibility Fallback
- `prefers-reduced-motion`: Modal displays instantly at `scale(1)` and `opacity: 1` with 0ms transition.
```

---

## Worked Example: Eliminating App Perceived Latency via Motion

- **Problem**: Opening a data drawer felt sluggish; users complained the application was slow.
- **Analysis**: The drawer animation took 500ms using a linear ease, blocking pointer clicks until completion.
- **Remediation**: Shortened duration to 220ms with an aggressive ease-out curve (`cubic-bezier(0.16, 1, 0.3, 1)`), unlocking pointer clicks on frame 1.
- **Outcome**: Users perceived the app as 2x faster without changing any backend code.

---

## Verification Checklist

- [ ] All animations stay within the $< 300text{ms}$ duration budget.
- [ ] Entrances use ease-out curves; exits use ease-in curves.
- [ ] No linear easing used on spatial movements.
- [ ] Staggered sequences cap total choreography under 350ms.
- [ ] Complete bypass provided for `prefers-reduced-motion: reduce`.

---

## Anti-Patterns

- **The Endless Bounce**: Using over-damped springs that bounce 6 times like jelly, making interfaces feel like a children's video game.
- **Blocking Clicks**: Preventing users from interacting with UI while an animation is playing.
- **Gratuitous Movement**: Animating every paragraph, icon, and card on page scroll for no functional reason.
