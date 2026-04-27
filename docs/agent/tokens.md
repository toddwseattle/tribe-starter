# Harness Tokens

All `ALL_CAPS` placeholders that must be replaced before agents can be fully useful. Replace global tokens first (they appear in multiple files), then per-file tokens.

## Global Setup Tokens

| Token | Description |
|---|---|
| `TRIBE_NAME` | Your tribe/team name |
| `CLIENT_NAME` | Client the app is built for |
| `WORKING_GROUP_ARCH_DESIGN` | Architecture & design guild name |
| `WORKING_GROUP_DEV_PRACTICES` | Dev practices guild name |

## Architecture Tokens

| Token | Description |
|---|---|
| `TEAM_RED_SLICE` | Red team's `src/` subdirectory name |
| `TEAM_ORANGE_SLICE` | Orange team's `src/` subdirectory name |
| `TEAM_BLUE_SLICE` | Blue team's `src/` subdirectory name |
| `TEAM_YELLOW_SLICE` | Yellow team's `src/` subdirectory name |
| `TEAM_*_OWNERSHIP_NOTES` | Scope notes for each team |
| `SHARED_DEPENDENCIES_DESCRIPTION` | Cross-team shared utilities/contracts |
| `DECISION_TITLE` / `STATUS` | Placeholder row in ADR index |

## Data Model Tokens

| Token | Description |
|---|---|
| `COLLECTION_NAME` / `COLLECTION_PATH` | Firestore collection name and path |
| `COLLECTION_DOCUMENT_TYPE` | TypeScript interface name for the collection |
| `STATE_MANAGEMENT_ADDITIONS` | Tribe-specific state management rules |
| `SERIALIZATION_ADDITIONS` | Tribe-specific serialization rules |

## Design Tokens

| Token | Description |
|---|---|
| `STYLING_APPROACH_STATUS` | Current styling decision status |
| `COMPONENT_CREATION_GUIDELINES` | When to create new vs extend a component |
| `COMPONENT_FILE_ORGANIZATION` | Component file co-location convention |
| `COLOR_AND_SPACING_TOKENS` | Design token names (colors, spacing) |
| `ADDITIONAL_A11Y_REQUIREMENTS` | Extra accessibility requirements |

## Testing Tokens

| Token | Description |
|---|---|
| `FIRESTORE_EMULATOR_SETUP_NOTES` | Firestore emulator setup instructions |
| `TRIBE_TDD_POLICY` | Tribe's TDD expectation |
| `ADDITIONAL_VITEST_PATTERNS` | Extra Vitest code patterns |
| `ADDITIONAL_MANUAL_VERIFICATION_ITEMS` | Extra manual verification steps |

## Per-Story Tokens (fill in for each story spec)

| Token | Description |
|---|---|
| `STORY_TITLE` / `STORY_SLUG` | Display title and kebab-case identifier |
| `ISSUE_NUMBER` | GitHub issue number |
| `TEAM_COLOR` | Owning team |
| `USER_ROLE` / `DESIRED_ACTION` / `BENEFIT` | User story parts |
| `GIVEN_CONDITION` / `WHEN_ACTION` / `THEN_OUTCOME` | AC-1 parts (repeat for AC-2, AC-3) |
| `CHANGE_DESCRIPTION` / `PURPOSE_DESCRIPTION` | File change and new-file purpose |
| `UNIT_TEST_DESCRIPTION` / `INTEGRATION_TEST_DESCRIPTION` / `MANUAL_VERIFICATION_STEP` | Test plan entries |
| `OUT_OF_SCOPE_ITEM` | Explicitly excluded item |
| `ADDITIONAL_DONE_CRITERION` | Extra done criteria |

## Per-ADR Tokens (fill in for each ADR)

| Token | Description |
|---|---|
| `GUILD_OR_TEAM_NAME` | ADR decider(s) |
| `CONTEXT_DESCRIPTION` | Situation forcing the decision |
| `DECISION_DESCRIPTION` | What was decided and why |
| `POSITIVE_CONSEQUENCE` / `NEGATIVE_CONSEQUENCE` | Trade-off summary |
| `FOLLOWUP_ITEM` | Required follow-up action |

---

## How to Find and Replace Tokens

### VS Code (recommended for initial setup)

**See all remaining tokens at once:**
1. Open Search: `⌘⇧F` (Mac) / `Ctrl+Shift+F` (Windows/Linux)
2. Enter `[A-Z_]{5,}` in the search box
3. Click the `.*` button to enable **Use Regular Expression**
4. Set **files to include** to `docs/**` to limit scope

**Replace a single token across all files:**
1. Open Find & Replace: `⌘⇧H` (Mac) / `Ctrl+Shift+H` (Windows/Linux)
2. Enable `.*` (regex) if needed; enter the token in **Find**, your value in **Replace**
3. Set **files to include** to `docs/**`
4. Click the **Replace All** button (or `⌥↵` / `Alt+Enter`) — VS Code will show a confirmation dialog with the match count before replacing

### macOS / Linux Command Line

Find all occurrences of a token:
```bash
grep -r "TRIBE_NAME" docs/
```

Replace in all markdown files (macOS):
```bash
find docs -name "*.md" -exec sed -i '' 's/TRIBE_NAME/YourTribeName/g' {} +
```

Replace in all markdown files (Linux):
```bash
find docs -name "*.md" | xargs sed -i 's/TRIBE_NAME/YourTribeName/g'
```

List all remaining unreplaced tokens:
```bash
grep -roh '[A-Z_]\{5,\}' docs/agent/ | sort -u
```

### Windows (PowerShell)

Find all occurrences of a token:
```powershell
Get-ChildItem -Path docs -Recurse -Filter "*.md" | Select-String "TRIBE_NAME"
```

Replace a token in all markdown files:
```powershell
Get-ChildItem -Path docs -Recurse -Filter "*.md" | ForEach-Object {
  (Get-Content $_.FullName) -replace 'TRIBE_NAME', 'YourTribeName' | Set-Content $_.FullName
}
```

List all remaining unreplaced tokens:
```powershell
Get-ChildItem -Path docs\agent -Recurse -Filter "*.md" |
  Select-String -Pattern '[A-Z_]{5,}' -AllMatches |
  ForEach-Object { $_.Matches.Value } | Sort-Object -Unique
```
