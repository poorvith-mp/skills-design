---
name: interactive-prototype
last_reviewed: 2026-09-06
group: Interface
description: >-
  Turn a design into a clickable prototype with real flows, states and transitions, ready to put
  in front of users. Use when building clickable Figma prototypes, state flows, or
  micro-interactions.
---

# interactive-prototype

## Core Philosophy
A static, non-interactive Figma mockup is an optical illusion. Static designs hide layout jumping, state collisions, transition lag, edge-case validation errors, and user hesitation. An interactive prototype is an operational simulation of software reality. Prototyping is not about adding flashy animations; it is a hypothesis-testing engine that puts clickable, responsive, state-accurate user journeys in front of real users to uncover cognitive friction before engineering commits a single sprint.

---

## 4-Step Interactive Prototype Engineering

### Step 1: Flow Scoping & Critical User Journeys (CUJ)
1. **Identify the Core Hypothesis**:
   - Define the exact question the prototype must answer:
     - *"Can a first-time user configure a database webhook and test a mock event in under 3 minutes without consulting docs?"*
2. **Scope the Prototype Perimeter**:
   - Prototype strictly the "Happy Path" plus the 2 most dangerous failure modes (e.g. validation error and network timeout). Do not build every dead-end settings page.

### Step 2: State-Accurate Component Connections
1. **Simulating Real Dynamic States**:
   - Interactive components must respond to user actions:
     - Hover states on buttons.
     - Inputs accepting simulated typing.
     - Modals appearing with background scrim dimming (`rgba(0,0,0,0.6)`).
     - Checkbox and toggle switches changing state on click.
2. **Smart Animate & Transition Choreography**:
   - Use Figma Smart Animate with consistent physics:
     - Navigation page push: 300ms ease-out.
     - Modal entry: Scale 0.95 -> 1.0 with fade (200ms ease-out).
     - Accordion expand: 250ms ease-in-out.

### Step 3: Realistic Seed Data & Edge Cases
1. **No `Lorem Ipsum` or `User 1`**:
   - Use realistic, high-fidelity domain data (e.g. realistic customer names, real JSON payloads, realistic transaction amounts).
2. **Interactive Form Validation**:
   - Wire error states: If user clicks "Save" with empty input, trigger realistic red inline validation message.

### Step 4: Usability Testing Protocol & Task Metrics
1. **The Moderated Usability Protocol (5 Users)**:
   - Give the participant a concrete task scenario without guiding their clicks:
     - *"Imagine you are an engineering manager. Invite your teammate Sarah to the platform and restrict her access to read-only."*
2. **Quantitative Success Metrics**:
   - *Task Completion Rate*: Target $\ge 80\%$.
   - *Time on Task*: Compare against expected benchmark.
   - *System Usability Scale (SUS)*: Post-test 10-question standardized survey (Target score $\ge 75$).

---

## Deliverable Format: Prototype Test Plan & Results (`PROTOTYPE-SPEC.md`)

```markdown
# Interactive Prototype Specification: [Feature Flow]

## 1. Core Hypothesis & Target Flow
- **Prototype Link**: [Figma Interactive Prototype Share URL]
- **Target User Persona**: Senior DevOps Engineer
- **Core Hypothesis**: Users can successfully diagnose and restart a failed pod in under 60 seconds using the mobile responsive web interface.

## 2. Interactive States & Transitions
| Trigger | Source Frame | Destination Frame | Transition / Physics |
|---|---|---|---|
| Click "Cluster Alpha" | Cluster List | Cluster Telemetry | Smart Animate (300ms ease-out) |
| Click "Restart Pod" | Telemetry Modal | Confirmation Dialog | Dissolve (150ms) |
| Click "Confirm" | Confirmation Dialog | Toast Success Banner | Instant swap + Slide-in toast |

## 3. Usability Test Results (Cohort of 5 Target Users)
- **Task Completion Rate**: 100% (5/5 users completed task)
- **Mean Time on Task**: 42 seconds (Benchmark target: < 60s)
- **System Usability Scale (SUS)**: **82.5** (Grade A - Excellent)
- **Key Observation**: 3 out of 5 users hesitated looking for the "Restart" button inside the actions dropdown; recommend elevating to top-level toolbar.
```

---

## Worked Example: Payment Checkout Flow Prototype

- **Test**: Tested 2 checkout flows: a 3-step wizard vs a single-page accordion.
- **Finding**: Wizard flow suffered a 40% drop-off at Step 2 because users could not preview final tax and shipping calculations.
- **Pivot**: Replaced with single-page accordion prototype. Task completion jumped to 95%. Saved 4 weeks of engineering redesign.

---

## Verification Checklist

- [ ] Prototype simulates complete end-to-end critical user journey.
- [ ] Interactive states (Hover, Focus, Pressed, Loading) wired to components.
- [ ] Realistic seed data used across all screens (no dummy Latin text).
- [ ] Usability test scenario scripted with clear, non-leading participant tasks.
- [ ] Task completion rate and user friction points documented.

---

## Anti-Patterns

- **Clickable Wireframes with Zero Interactivity**: Connecting 3 static images and expecting users to evaluate real workflow usability.
- **Guiding the Participant**: Telling the user "Now click the blue button on the right" during a usability test.
- **Over-Prototyping**: Spending 3 weeks prototyping 40 peripheral pages that have zero impact on the core hypothesis.
