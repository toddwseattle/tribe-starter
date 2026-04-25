# Data Model Guide

<!-- Placeholder — replace ALL_CAPS tokens with your tribe's values. Delete this comment when done. -->

Owned by the **WORKING_GROUP_ARCH_DESIGN**. This document defines the Firestore collections, shared TypeScript types, and state management rules. Read it before writing any code that reads from or writes to Firestore.

## Iteration 0 Requirement

**The shared `User` type must be defined and agreed upon in Iteration 0.** Every team's features depend on it. Until it is defined, stubs are acceptable, but all stubs must use the same shape. The WORKING_GROUP_ARCH_DESIGN owns this definition.

## The `User` Type

```typescript
// STATUS: TBD — WORKING_GROUP_ARCH_DESIGN must finalize this in Iteration 0
// Replace this stub with the agreed type and remove this comment.
export interface User {
  uid: string;           // Firebase Auth UID — primary key
  email: string;
  displayName: string;
  // TODO: add fields as the guild decides
}
```

_Once finalized, move this type to `src/shared/types/User.ts` and export it from `src/shared/types/index.ts`._

## Firestore Collection Shapes

For each collection, document: the collection path, the document ID strategy, the TypeScript type, and any subcollections.

### `users` collection

```
/users/{uid}
```

```typescript
// STATUS: TBD
interface UserDocument {
  // mirrors the User type above
}
```

### COLLECTION_NAME collection

```
/COLLECTION_PATH/{docId}
```

```typescript
// STATUS: TBD
interface COLLECTION_DOCUMENT_TYPE {
  // document fields
}
```

_Add a section per collection. Delete the placeholder section once real collections are defined._

## State Management Rules

1. **Firestore is the source of truth.** Do not duplicate Firestore data in local state unless you are caching a snapshot for performance.
2. **React Context is for session-scoped shared state** (e.g., the authenticated user, theme). Do not put frequently-updated domain data in context — use Firestore listeners instead.
3. **Props are for component-local data** that does not need to be shared outside the component tree.
4. **Avoid prop drilling beyond two levels.** If a value needs to go more than two levels deep, lift it to context or Firestore.

STATE_MANAGEMENT_ADDITIONS

## Serialization Rules

- All Firestore `Timestamp` fields must be converted to `Date` (or ISO string) before entering React state. Do not pass Firestore `Timestamp` objects directly to components.
- Do not store `undefined` in Firestore documents. Use `null` for absent optional fields.
- Do not use Firestore's `serverTimestamp()` in tests — use a fixed `Date` instead.

SERIALIZATION_ADDITIONS
