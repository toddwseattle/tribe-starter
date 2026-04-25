# Testing Guide

<!-- Placeholder — replace ALL_CAPS tokens with your tribe's values. Delete this comment when done. -->

Owned by **WORKING_GROUP_DEV_PRACTICES** (see `docs/tribe/guilds.md`). This document tells agents what to test, how to test it, and what naming conventions to follow. Read it alongside the story spec's test plan before writing any test.

## What Must Be Unit-Tested

Unit tests run in jsdom via Vitest. They must cover:

- **Pure functions:** any function that takes inputs and returns a value without side effects
- **Custom hooks:** use `renderHook` from React Testing Library to test hooks in isolation
- **UI state logic:** reducers, state machine transitions, derived values from context

Unit tests do NOT need to cover: Firestore SDK calls, Firebase Auth flows, or any I/O. Mock those at the boundary.

## What Must Be Integration-Tested

Integration tests exercise a component together with its Firestore reads/writes. These are harder to write and slower to run, so use them deliberately.

Integration tests must cover:

- **Components that read from Firestore** — verify the component renders the correct data given a known Firestore state
- **Components that write to Firestore** — verify the correct document is written when the user takes an action
- **Authentication-gated routes** — verify that unauthenticated users are redirected

_How to set up Firestore emulator for tests:_ FIRESTORE_EMULATOR_SETUP_NOTES

## What Is Manually Verified

Some things are not worth the cost of automated tests:

- Visual appearance and layout
- Animations and transitions
- Browser-specific behavior outside jsdom
- End-to-end happy paths in the deployed preview (run these before merging a sprint's worth of work)

ADDITIONAL_MANUAL_VERIFICATION_ITEMS

## Vitest Patterns the Tribe Has Adopted

```tsx
// Preferred: query by role (accessible and resilient to text changes)
screen.getByRole('button', { name: /submit/i })

// Preferred: userEvent over fireEvent for interactions
const user = userEvent.setup();
await user.click(screen.getByRole('button', { name: /submit/i }));

// Preferred: explicit waitFor when state updates are async
await waitFor(() => expect(screen.getByText('Saved')).toBeInTheDocument());
```

ADDITIONAL_VITEST_PATTERNS

## TDD Expectations

The tribe's expectation for test-driven development: TRIBE_TDD_POLICY

Suggested baseline: write the test for the acceptance criterion first, watch it fail, then implement. This ensures the test actually tests what the spec requires.

## Test Naming Convention

Test names should mirror the story spec's Given/When/Then acceptance criteria. This makes it easy to trace a failing test back to the spec.

```
// Story spec AC: "Given the user is not signed in, When they visit /dashboard, Then they are redirected to /login"
// Test name:
it('redirects unauthenticated users from /dashboard to /login', ...)

// Or using describe/it structure:
describe('Dashboard', () => {
  describe('when the user is not signed in', () => {
    it('redirects to /login', ...)
  })
})
```

## Coverage Thresholds

The `vite.config.ts` enforces 70% thresholds for statements, branches, functions, and lines. Do not lower these thresholds without an ADR. Teams may raise them for their slice.
