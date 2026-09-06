---
name: delight
group: Interface
description: >-
  Add personality through microinteractions, copy moments and easter eggs, without harming
  usability. Use when adding tasteful Easter eggs, celebratory animations, or personality.
---

# delight

## Core Philosophy
Delight in user interface design is not cloying animations, slow floating cartoons, or annoying mascots that interrupt user workflows. Delight is the unexpected feeling of elegance, intelligence, and respect that occurs when software operates faster and more thoughtfully than expected. True delight is micro-ergonomic: instant keyboard shortcuts, thoughtful zero-states, celebratory completion moments that respect user time, and dry, tasteful easter eggs that bring a smile without creating friction.

---

## 4-Step Delight Engineering Framework

### Step 1: The "Peak-End Rule" of User Experience
1. **Targeting Emotional Anchors**:
   - Psychological research proves users judge an experience based on two moments: the **Peak** (the emotional high point of value) and the **End** (the final moment of workflow completion).
2. **Amplifying Milestone Moments**:
   - *Deploy Succeeded*: A crisp, 400ms micro-burst of confetti or a smooth green completion pulse.
   - *First Payment Processed*: A subtle sound design chime paired with an encouraging, understated copy moment.
   - *Inbox Zero Achieved*: A serene, non-condescending illustration celebrating finished work.

### Step 2: Microinteractions & Tactile Feedback
1. **Physics-Based UI Response**:
   - Interactive elements should respond with subtle, spring-based micro-movement:
     - Buttons depressing slightly (`scale: 0.98`) on tap.
     - Toggle switches snapping with an organic elastic spring curve.
     - Copy-to-clipboard actions providing immediate visual transformation (e.g. checkmark icon sliding in with "Copied!").
2. **Audio Design (Optional & Restrained)**:
   - Extremely subtle, low-frequency clicks or wooden thuds on completion actions (always respects system mute and includes an opt-out toggle).

### Step 3: Thoughtful Empty States & Error Compassion
1. **Empty States as Launchpads**:
   - Never show an empty gray box that says "No items found".
   - Turn zero-states into actionable, welcoming entry points:
     - *"Your project list is empty. Here is a 60-second starter template to deploy your first cluster."*
2. **Error Compassion**:
   - When users make an error, replace cold corporate alerts with helpful, human guidance.

### Step 4: The Golden Rule of Non-Intrusive Personality
1. **Never Block the Expert**:
   - Microinteractions must **never exceed 300ms** in duration.
   - Animations must never block pointer clicks or keyboard strokes.
   - Never force a user to watch an animation before proceeding with their job.

---

## Deliverable Format: Delight & Microinteraction Spec (`DELIGHT-SPEC.md`)

```markdown
# Delight & Microinteraction Specification: [Feature Name]

## 1. Interaction Trigger & Context
- **Feature Moment**: Successful PR Merge & Deployment
- **User Emotional State**: High satisfaction / Relief (Peak Moment)
- **Delight Mechanism**: Tactile completion checkmark + subtle particle cascade

## 2. Animation Physics & Timing
- **Duration**: 280ms total (Non-blocking)
- **Easing**: Spring curve: `cubic-bezier(0.16, 1, 0.3, 1)`
- **Visual Motion**:
  - Checkmark scale: `0.8 -> 1.05 -> 1.0`
  - Particle burst: 12 micro-particles emitting 40px radius, fading to 0 opacity.
- **Reduced Motion Fallback**: Instant icon swap to static checkmark with zero particle emission.

## 3. Personality Copy Moments
- **Standard Tooltip**: *"Copied to clipboard"*
- **Delight Variation (After 3 rapid clicks)**: *"Double copied! You're good to go."*
```

---

## Worked Example: Developer CLI Delight Moment

- **Implementation**: CLI tool added a subtle terminal ASCII art animation when running `deploy --prod`, finishing with execution duration: *"Deployed in 1.4s (3.2x faster than previous run) ⚡"*.
- **Impact**: Developers took screenshots and tweeted the terminal output organically, driving 4,000 GitHub stars in the launch week.

---

## Verification Checklist

- [ ] Microinteractions execute in $< 300text{ms}$ and do not block user input.
- [ ] Celebrations are aligned with genuine user accomplishments (Peak-End moments).
- [ ] Empty states provide a direct path to action and learning.
- [ ] Sound design is disabled by default or respects system volume and mute states.
- [ ] Full fallback provided when `prefers-reduced-motion` is active.

---

## Anti-Patterns

- **Clippy Syndrome**: Interrupting user focus with unwanted popups or animated mascots trying to be funny.
- **Sluggish Transitions**: Making users wait 1.5 seconds for a modal fade-in before they can click "Confirm".
- **Celebrate Failures**: Showing cartoon characters crying or acting whimsical when an error or billing failure occurs.
