# Story: STORY_TITLE

<!-- Placeholder — replace ALL_CAPS tokens with your tribe's values. Delete this comment when done. -->
<!-- This is an agent-ready story spec. Agents should read this entire file before writing any code. -->

**Slug:** `STORY_SLUG`

**Status:** Draft | Ready | In Progress | Done

---

## Links

- **Parent epic:** [EPIC_TITLE](../epics/EPIC_SLUG.md)
- **GitHub issue:** #ISSUE_NUMBER
- **Owning team:** TEAM_COLOR

---

## User Story

> As a USER_ROLE, I want DESIRED_ACTION so that BENEFIT.

---

## Acceptance Criteria

_Each criterion is a testable Given/When/Then condition. These become test names. Write them before writing code._

**AC-1:** Given GIVEN_CONDITION, When WHEN_ACTION, Then THEN_OUTCOME.

**AC-2:** Given GIVEN_CONDITION_2, When WHEN_ACTION_2, Then THEN_OUTCOME_2.

**AC-3 (error case):** Given GIVEN_ERROR_CONDITION, When WHEN_ERROR_ACTION, Then THEN_ERROR_OUTCOME.

---

## Technical Approach

_2–3 paragraphs. Enough context for an agent to start without guessing. Reference guides from `docs/agent/` where they apply. Do not over-specify — leave implementation details to the agent._

### Files to Change

| File | Change |
|---|---|
| `src/PATH/TO/FILE.tsx` | CHANGE_DESCRIPTION |

### Files to Create

| File | Purpose |
|---|---|
| `src/PATH/TO/NEW_FILE.tsx` | PURPOSE_DESCRIPTION |

### Patterns That Apply

- See `docs/agent/testing.md` §SECTION for testing patterns
- See `docs/agent/data-model.md` §SECTION for data shape
- See `docs/agent/design.md` §SECTION for component conventions

---

## Interfaces and Data Shapes

_Write out TypeScript types for any new or changed data. Do not leave this as "TBD" — if the type is genuinely unknown, that is a blocker; raise it before marking the story Ready._

```typescript
// New or changed types introduced by this story
interface NEW_TYPE {
  field: TYPE;
}
```

---

## Test Plan

**Unit tests:**
- UNIT_TEST_DESCRIPTION (mirrors AC-1)
- UNIT_TEST_DESCRIPTION (mirrors AC-2)

**Integration tests:**
- INTEGRATION_TEST_DESCRIPTION

**Manual verification:**
- MANUAL_VERIFICATION_STEP

---

## Out of Scope

_Explicit. If something seems related but is not included, name it here._

- OUT_OF_SCOPE_ITEM

---

## Done When

- [ ] All acceptance criteria pass (tests are green)
- [ ] `npm run lint` passes
- [ ] `npm run build` passes (TypeScript strict)
- [ ] PR has been reviewed by the owning team
- [ ] This spec has been updated to match what was actually built (update in-flight if it drifted)
- [ ] Deployed to preview environment and manually verified
- [ ] ADDITIONAL_DONE_CRITERION
