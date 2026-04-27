# Story: STORY_TITLE

**Slug:** `STORY_SLUG` | **Status:** Draft | Ready | In Progress | Done
**Issue:** #ISSUE_NUMBER | **Team:** TEAM_COLOR

---

## User Story

> As a USER_ROLE, I want DESIRED_ACTION so that BENEFIT.

## Acceptance Criteria

**AC-1:** Given GIVEN_CONDITION, When WHEN_ACTION, Then THEN_OUTCOME.
**AC-2:** Given GIVEN_CONDITION_2, When WHEN_ACTION_2, Then THEN_OUTCOME_2.
**AC-3 (error):** Given GIVEN_ERROR_CONDITION, When WHEN_ERROR_ACTION, Then THEN_ERROR_OUTCOME.

## Technical Approach

_2–3 paragraphs. Reference `docs/agent/` guides. Don't over-specify._

| File | Change |
|---|---|
| `src/PATH/FILE.tsx` | CHANGE_DESCRIPTION |

## Interfaces

```typescript
interface NEW_TYPE {
  field: TYPE;
}
```

## Test Plan

- **Unit:** UNIT_TEST_DESCRIPTION (mirrors AC-1)
- **Integration:** INTEGRATION_TEST_DESCRIPTION
- **Manual:** MANUAL_VERIFICATION_STEP

## Out of Scope

- OUT_OF_SCOPE_ITEM

## Done When

- [ ] All ACs pass (tests green)
- [ ] `npm run lint` and `npm run build` pass
- [ ] PR reviewed by owning team
- [ ] Deployed to preview and manually verified
- [ ] ADDITIONAL_DONE_CRITERION
