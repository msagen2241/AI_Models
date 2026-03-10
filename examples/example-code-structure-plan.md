# Summary

- Repository or project: `example-app`
- Target project folder: `G:\MidTier\AI-Projects\example-app`
- Date: 2026-03-08
- Scope: folder cleanup, helper consolidation, and feature boundary clarification
- Primary concerns: mixed feature and shared code, oversized utility layer, inconsistent folder naming

# Current state assessment

- Top-level layout: `src/`, `scripts/`, `components/`, `utils/`, and `misc/` overlap in purpose.
- Problem areas: feature code is split across root folders instead of grouped by domain.
- Tangled modules: `components/checkout` imports directly from `utils/api`, `misc/cart`, and `src/hooks`.
- Duplicate helpers or utilities: date formatting exists in both `utils/date.ts` and `src/lib/formatDate.ts`.
- Oversized files or folders: `utils/index.ts` re-exports unrelated helpers and has become a catch-all surface.
- Naming inconsistencies: `misc/`, `shared/`, and `common/` are all used for cross-cutting code.
- Architecture drift signals: recent feature additions bypass the intended `src/features/*` layout.

# Proposed target structure

- Target layout: move application code under `src/features`, `src/shared`, and `src/app` with clear ownership.
- Module boundaries: feature modules own feature-specific UI, hooks, and local helpers; shared code is reserved for stable cross-feature utilities.
- Ownership expectations: checkout code stays within `src/features/checkout`, while formatting helpers move to `src/shared/formatting`.
- Naming conventions: remove `misc` in favor of explicit feature or shared folder names.

# Exact file or folder create/move/refactor recommendations

- Move `components/checkout/*` to `src/features/checkout/components/*`.
- Move `misc/cart/*` to `src/features/cart/*` after updating imports.
- Consolidate date helpers into `src/shared/formatting/date.ts` and delete the duplicate implementation after references are updated.
- Split `utils/index.ts` into smaller entry points.

# Risks and compatibility concerns

- Import or path fallout:
- Runtime or build risk:
- Test risk:
- Rollback considerations:

# Validation checklist

- [ ] Verify every referenced existing file and folder exists.
- [ ] Verify planned file and folder creations do not conflict unexpectedly.
- [ ] Verify imports and references impacted by creates, moves, or renames.
- [ ] Verify public entry points remain intact.
- [ ] Verify generated or build-only folders are excluded.
- [ ] Confirm assumptions that need owner input.

# Implementation notes

- Edit order:
- Small reversible steps:
- File and folder creation order:
- Post-change checks:
- Review focus areas:

# Execution table

| Step | Action | Path | Details | Content |
|------|--------|------|---------|---------|
| 1 | mkdir | G:/MidTier/AI-Projects/Code-Structure/src | Create the src directory. |  |
| 2 | mkdir | G:/MidTier/AI-Projects/Code-Structure/scripts | Create the scripts directory. |  |
| 3 | mkdir | G:/MidTier/AI-Projects/Code-Structure/components | Create the components directory. |  |
| 4 | mkdir | G:/MidTier/AI-Projects/Code-Structure/utils | Create the utils directory. |  |
| 5 | mkdir | G:/MidTier/AI-Projects/Code-Structure/misc | Create the misc directory. |  |
| 6 | mv | G:/MidTier/AI-Projects/Code-Structure/components/checkout/* G:/MidTier/AI-Projects/Code-Structure/src/features/checkout/components/ | Move checkout components to src/features/checkout/components/. |  |
| 7 | mv | G:/MidTier/AI-Projects/Code-Structure/misc/cart/* G:/MidTier/AI-Projects/Code-Structure/src/features/cart/ | Move cart content to src/features/cart/. |  |
| 8 | write | G:/MidTier/AI-Projects/Code-Structure/src/shared/formatting/date.ts | Consolidate date helpers into a single file. | ```typescript
export function formatDate(date: Date): string {
  // Implementation of formatDate
}
``` |
| 9 | bash | rm -f G:/MidTier/AI-Projects/Code-Structure/utils/date.ts G:/MidTier/AI-Projects/Code-Structure/src/lib/formatDate.ts | Remove duplicate date helper files. |  |
| 10 | write | G:/MidTier/AI-Projects/Code-Structure/.opencode/plans/code-structure-plan.md | Write the execution plan to a file. | ```markdown
# Execution Plan

## Step 1: Create target directories
- Create `src/`
- Create `scripts/`
- Create `components/`
- Create `utils/`
- Create `misc/`

## Step 2: Move and consolidate files
- Move content from `components/checkout/*` to `src/features/checkout/components/*`.
- Move content from `misc/cart/*` to `src/features/cart/*` after updating imports.
- Consolidate date helpers into `src/shared/formatting/date.ts` and delete the duplicate implementation after references are updated.
- Split `utils/index.ts` into smaller entry points.

## Step 3: Update imports and references
- Ensure all internal imports and cross-references are correctly updated after file moves.

## Step 4: Clean up and finalize
- Remove unused files or folders.
- Verify the project structure aligns with the intended architecture.

# Validation Checklist

- [ ] Verify every referenced existing file and folder exists.
- [ ] Verify planned file and folder creations do not conflict unexpectedly.
- [ ] Verify imports and references impacted by creates, moves, or renames.
- [ ] Verify public entry points remain intact.
- [ ] Verify generated or build-only folders are excluded.
- [ ] Confirm assumptions that need owner input.

# Implementation Notes

- Follow the execution table to ensure each step is performed correctly and in order.
- Use native tools first when possible, such as `bash`, `read`, `write`, `edit`, etc.
- Pay attention to file paths and ensure they use forward slashes (`/`) as required by Git Bash on Windows.
``` |

# Risks and compatibility concerns

- Import or path fallout:
- Runtime or build risk:
- Test risk:
- Rollback considerations:

# Validation checklist

- [ ] Verify every referenced existing file and folder exists.
- [ ] Verify planned file and folder creations do not conflict unexpectedly.
- [ ] Verify imports and references impacted by creates, moves, or renames.
- [ ] Verify public entry points remain intact.
- [ ] Verify generated or build-only folders are excluded.
- [ ] Confirm assumptions that need owner input.

# Implementation notes

- Edit order:
- Small reversible steps:
- File and folder creation order:
- Post-change checks:
- Review focus areas: