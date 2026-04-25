# Design Guide

<!-- Placeholder — replace ALL_CAPS tokens with your tribe's values. Delete this comment when done. -->

Owned by the **WORKING_GROUP_ARCH_DESIGN**. This document tells agents what UI conventions the tribe has adopted. Read it before creating or modifying any component.

## Styling Approach (TBD by WORKING_GROUP_ARCH_DESIGN)

The tribe has not yet committed to a styling approach. **Do not assume Tailwind or any CSS framework.** The WORKING_GROUP_ARCH_DESIGN will make this decision in Iteration 0 and record it as an ADR.

Prompts for the guild's decision:
- Which approach: plain CSS modules, Tailwind, CSS-in-JS (styled-components / emotion), or something else?
- Does the chosen approach work well with Vite 8 and React 19?
- How are design tokens (colors, spacing, typography) defined and shared?
- What is the migration cost if we change our minds after Iteration 0?

Once decided, update this section to:
- Name the chosen approach and link to the ADR
- Describe how to add a new styled component
- Describe how to apply existing tokens

**Current status:** STYLING_APPROACH_STATUS

## When to Create a New Component vs Extend Existing

<!-- Guidelines for deciding whether new UI should be a new component, a variant of an existing one,
     or a modification to an existing component's props.
     Rule of thumb examples: single responsibility, duplication threshold, shared-state considerations. -->

COMPONENT_CREATION_GUIDELINES

## Component File Organization

<!-- Where do component files live? Co-located with feature folder? In a shared components folder?
     What files does a component consist of? (e.g., MyWidget.tsx, MyWidget.test.tsx, MyWidget.module.css) -->

COMPONENT_FILE_ORGANIZATION

## Color and Spacing Tokens

<!-- Once the styling approach is decided, document the token names here.
     E.g., --color-primary, --spacing-md, font-size scale. -->

COLOR_AND_SPACING_TOKENS

## Accessibility Minimums

Every component shipped to production must meet these minimums:

- All interactive elements have a visible focus indicator
- All images have meaningful `alt` text (or `alt=""` for decorative images)
- Color contrast meets WCAG AA (4.5:1 for normal text, 3:1 for large text)
- Forms use `<label>` elements associated with their inputs
- ADDITIONAL_A11Y_REQUIREMENTS

## Team Color Assignments (Iteration 0 Spike)

The Iteration 0 spike asks each team to build a small UI element in their team color. This is a coordination exercise, not a permanent design decision. Use these color values for the spike only:

| Team | Hex | Notes |
|---|---|---|
| Red | #D32F2F | Chosen for colorblind accessibility |
| Orange | #E65100 | Chosen for colorblind accessibility |
| Blue | #1565C0 | Chosen for colorblind accessibility |
| Yellow | #F9A825 | Chosen for colorblind accessibility |
