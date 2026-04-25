# Architecture Guide

<!-- Placeholder — replace ALL_CAPS tokens with your tribe's values. Delete this comment when done. -->

Owned by **WORKING_GROUP_ARCH_DESIGN** (see `docs/tribe/guilds.md`). This document is the agent's primary reference for how the system is structured. Read it before making changes that touch more than one file or cross a team boundary.

## System Context

TRIBE_NAME builds a web application for CLIENT_NAME. The application is a single-page React app served from a static host (TBD by guild). It communicates with Firebase/Firestore for persistence and Firebase Authentication for identity. There are no other backend services in scope for 2026; all logic runs in the client except Firestore security rules.

## Container Overview (C4 Level 2)

_Text description — add a Mermaid diagram in the ADR or here once the guild has agreed on the shape._

**Containers:**

1. **React SPA** — the application the user runs in their browser. Built with Vite, hosted on HOSTING_PLATFORM_TBD.
2. **Firebase Authentication** — handles sign-in/sign-up. SDK imported directly into the SPA.
3. **Cloud Firestore** — document database. Accessed via the Firebase Web SDK. Security rules enforce access control server-side.
4. **Firebase Hosting** (optional) — static asset hosting. TBD by tribe.

**Key flows:**

- User signs in → Firebase Auth returns a token → SPA stores auth state in React context
- SPA reads/writes data → Firestore SDK → Firestore → returns documents or real-time snapshots
- Build pipeline → Vite → static bundle → deployed to HOSTING_PLATFORM_TBD

## Key Architectural Decisions

See `docs/agent/decisions/` for full ADR texts.

| ADR | Title | Status |
|---|---|---|
| 0001 | Use this harness structure | Accepted |
| NNNN | DECISION_TITLE | STATUS |

## Team Ownership Map

Each team owns a top-level directory under `src/`. Owning a directory means: the team writes and reviews code there, and no other team merges to that directory without the owning team's explicit approval in the PR.

| Team | Owned path(s) | Notes |
|---|---|---|
| Red | `src/TEAM_RED_SLICE/` | TEAM_RED_OWNERSHIP_NOTES |
| Orange | `src/TEAM_ORANGE_SLICE/` | TEAM_ORANGE_OWNERSHIP_NOTES |
| Blue | `src/TEAM_BLUE_SLICE/` | TEAM_BLUE_OWNERSHIP_NOTES |
| Yellow | `src/TEAM_YELLOW_SLICE/` | TEAM_YELLOW_OWNERSHIP_NOTES |
| Shared | `src/shared/` | Any team can use; WORKING_GROUP_ARCH_DESIGN reviews changes |

_Note: this map must be filled in during Iteration 0. Until it is filled in, treat all of `src/` as shared and require approval from the architecture working group lead for any structural change._

## Shared Dependencies and Contracts

<!-- List any shared utilities, context providers, or hooks that cross team boundaries.
     If team A's component depends on team B's hook, document it here. -->

SHARED_DEPENDENCIES_DESCRIPTION
