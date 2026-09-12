---
name: ui-copy
last_reviewed: 2026-09-06
group: Interface
description: >-
  Write interface microcopy — buttons, errors, empty states, tooltips — and replace placeholder
  text with real copy. Use when writing UI microcopy, button labels, empty states, or error
  messages.
---

# ui-copy

## Core Philosophy
User Interface (UI) copy—microcopy on buttons, error banners, input placeholders, empty states, and modal dialogs—is functional interaction design. UI copy is not marketing copy; its purpose is to reduce cognitive load, guide immediate physical action, clarify consequences, and eliminate user anxiety. Vague, passive, or blame-shifting microcopy destroys usability and multiplies customer support tickets.

---

## 4-Step UI Microcopy Crafting Framework

### Step 1: Button Labels: Verb-First & Outcome-Driven
1. **The Verb-Noun Standard**:
   - Buttons must clearly declare the exact action that will occur upon clicking:
     - *Bad (Vague / Passive)*: "Submit", "OK", "Click Here", "Proceed", "Yes".
     - *Good (Specific & Active)*: "Create Project", "Save Changes", "Download Invoice", "Deploy Cluster".
2. **Destructive Confirmation Actions**:
   - In deletion dialogs, mirror the action explicitly:
     - *Bad*: `[Cancel]` and `[OK]`
     - *Good*: `[Keep Project]` and `[Delete Project permanently]`

### Step 2: The 3-Part Error Message Architecture
1. **The Anatomy of a Perfect Error Message**:
   - *1. What Happened (Clear & Non-Technical)*: State the problem without blaming the user.
   - *2. Why It Happened (Root Cause)*: Provide concise context.
   - *3. How to Fix It (Immediate Concrete Next Step)*: Give a single actionable resolution.
   - *Bad*: "Error 500: An unexpected database failure occurred."
   - *Good*: "Payment could not be processed. Your card was declined by the bank due to insufficient funds. Please update your payment method or contact your card issuer."

### Step 3: Thoughtful Empty States as Action Launchpads
1. **The 3 Elements of High-Converting Empty States**:
   - *1. Acknowledgment of State*: "No active clusters found."
   - *2. Educational Value*: "Clusters run your container workloads across isolated cloud regions."
   - *3. Primary Launch Action*: `[Create Your First Cluster]` (Direct button, not a link to docs).

### Step 4: Input Placeholders vs Helper Text
1. **The Placeholder Trap**:
   - Never use placeholder text as a replacement for an input label (placeholders disappear when the user types, destroying context).
   - Use labels for *what* the field is ("API Token").
   - Use helper text below the input for *formatting requirements* ("Must be at least 32 characters, starting with `sk_live_`").
   - Use placeholder text strictly as a transient syntax example (e.g. `e.g. sk_live_51M...`).

---

## Deliverable Format: UI Microcopy Specification Matrix (`UI-COPY-SPEC.md`)

```markdown
# UI Microcopy & Interaction Copy Matrix: [Feature / Flow Name]

## 1. Action Buttons & Modals
| Component | Default Copy | Bad Cliché Alternative | Context / UX Rationale |
|---|---|---|---|
| Primary Save | `[Save Changes]` | `[Submit]` | Explains exact state update |
| Destructive Modal | `[Delete API Key]` | `[Confirm]` | Eliminates ambiguity on irreversible actions |
| Secondary Dismiss | `[Keep API Key]` | `[Cancel]` | Explicitly confirms non-destructive choice |

## 2. Error Message Taxonomy
- **Scenario**: Invalid Email Format
  - *Copy*: "Please enter a valid email address (e.g. name@company.com)."
- **Scenario**: API Rate Limit Reached
  - *Copy*: "Rate limit reached (100 req/min). Your quota resets in 42 seconds. [Upgrade Plan] to increase throughput."
- **Scenario**: Session Expired
  - *Copy*: "Your session expired after 30 minutes of inactivity. Please log in again to continue your work."

## 3. Empty State Blueprint: Team Members List
- **Headline**: "You haven't added any team members yet"
- **Body**: "Collaborate with your team by sharing environments, reviewing pull requests, and assigning permissions."
- **Primary CTA**: `[Invite Team Member]`
```

---

## Worked Example: Form Error Microcopy Overhaul

- **Original Error**: "Invalid input in field 4."
- **Rewritten Copy**: "Password must be at least 12 characters and include at least one number."
- **Outcome**: Form abandonment dropped from 28% to 6% on the registration page; support inquiries regarding signup fell 80%.

---

## Verification Checklist

- [ ] All button labels start with an active, specific verb ("Create", "Export", "Delete").
- [ ] Error messages provide the 3 parts (What happened, Why, How to fix).
- [ ] Destructive dialog buttons explicitly name the item being deleted.
- [ ] Input fields have permanent labels (not relying on vanishing placeholders).
- [ ] Empty states provide educational context and a direct primary action button.

---

## Anti-Patterns

- **Blaming the User**: Writing "You entered the wrong data!" instead of explaining the formatting requirement.
- **Generic Submit Buttons**: Using "Submit" on 10 different forms across the application.
- **Jargon Error Codes**: Displaying raw backend stack traces or `ERR_SOCKET_TIMEOUT` to non-technical users.
