---
name: motion-graphics-producer
description: >-
  Specifies motion graphics: keyframes, timing, audio sync points and export settings for video
  and web. Use when producing an animated sequence or handing a motion spec to an editor.
---

# Motion Graphics Producer

Animation planning describes what should happen; this skill specifies exactly how — timing in milliseconds, easing curves, and layer-by-layer keyframe behavior precise enough that an animator or a developer implementing it in code doesn't have to guess at intent.

## Core principles to apply

1. **Easing communicates physicality and mood.** Linear motion reads as mechanical/robotic — almost never what's wanted for organic UI or brand motion. Default to eased curves and choose deliberately:
   - **Ease-out** (fast start, slow finish) — most natural default for elements entering/appearing; reads as responsive.
   - **Ease-in-out** — smooth for elements moving between two states, neither entering nor exiting.
   - **Spring/bounce easing** — communicates playfulness or physicality; overused, it reads as unpolished, so reserve it for brand-appropriate contexts, not every interaction.
2. **Duration should match the scale and importance of the motion.** Small UI micro-interactions (button press feedback, toggle switches): 100-200ms. Element transitions (modal open, page transition): 200-400ms. Larger narrative motion (logo reveal, brand animation): can run longer, but even then, avoid motion that makes a user wait — anything blocking interaction should stay under ~500ms unless it's a deliberate, skippable brand moment.
3. **Stagger related elements** rather than animating a group simultaneously — a list of items appearing with a small stagger (e.g. 30-50ms offset per item) reads as more polished and directs visual attention sequentially, versus everything appearing at once which reads as flat.
4. **Respect reduced-motion accessibility preferences** — always note that any animation spec should have a reduced-motion fallback (shorter duration or a simple fade instead of the full motion) for users with `prefers-reduced-motion` set, since motion can trigger vestibular discomfort for some users. Flag this even if not asked.

## Workflow

1. **Get the concept and platform target** — is this a logo animation, a UI micro-interaction, a page transition, or an explainer-style sequence? And is it being implemented in code (CSS/SVG/Lottie/JS) or handed to an animator working in After Effects? The output format differs significantly.
2. **Break the motion into discrete keyframe stages** — starting state, intermediate states if the motion isn't a simple two-point tween, and end state, each with explicit timing.
3. **Specify easing per stage explicitly** — don't leave it implicit; name the curve (e.g. `cubic-bezier(0.16, 1, 0.3, 1)` for a snappy ease-out, or the equivalent After Effects graph editor description).
4. **For code-implemented motion**, provide the actual CSS/SVG animation syntax or Lottie-compatible structure where feasible, not just a prose description — a developer implementing this shouldn't have to reverse-engineer intent from adjectives.

## Output format

```markdown
## Motion brief: <element/sequence name>

**Platform/implementation target:** [CSS / SVG / Lottie / After Effects handoff]

**Sequence:**
| Stage | Time (ms) | Property change | Easing |
|---|---|---|---|

**Reduced-motion fallback:** [specified explicitly]
```
Follow with the actual implementation code if the target is CSS/SVG/JS.

## Verification & Quality Checklist

- [ ] Contrast and legibility verified at the smallest intended display size.
- [ ] Dimensions, bleed, and safe areas match the named output medium.
- [ ] Colour is never the sole carrier of meaning - icons or text accompany it.
- [ ] Asset licensing and font embedding rights confirmed for the intended use.

## Anti-Patterns & Constraints

- NEVER deliver a design without stating the medium and its constraints.
- NEVER rely on colour alone to convey state, status, or meaning.
- NEVER hand off exports without confirming the target platform's specs.
