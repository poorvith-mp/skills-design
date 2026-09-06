# WCAG UI Design Guide

## Interactive Components
- All buttons, links, and form elements must be keyboard accessible
- Focus order must follow visual layout (left-to-right, top-to-bottom)
- Custom components need appropriate ARIA roles

## Form Design
- Labels must be visible and programmatically associated (`for`/`id`)
- Required fields indicated by more than just color (use asterisk + text)
- Error messages appear adjacent to the input with `aria-describedby`

## Modal & Dialog Patterns
- Focus trapped within modal while open
- Close on Escape key
- Focus returns to trigger element on close
- Background content marked `aria-hidden="true"`
