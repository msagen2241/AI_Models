# Code-Structure Workspace

This workspace is for coding, project creation, codebase cleanup, repo structuring, architecture planning, validation, implementation, and review on Windows.

## Why native tools come first
Native local tools are the default for repository work because they are direct, fast, and well-suited to reading, editing, searching, listing, and validating files inside a local project. They should handle the normal coding loop for local repos without depending on MCP.

## When MCP makes sense
MCP is optional here. Use it when the workflow needs to interact with systems outside the local repository, such as GitHub, browser automation with Playwright, documentation lookup, databases, cloud services, or other remote tools. Native for the repo, MCP for the world outside the repo.

## When to turn MCPs on
- `windows-mcp`: turn on when you need Windows-specific filesystem browsing outside the normal local repo tool flow.
- `github`: turn on when you need repository, pull request, issue, or remote GitHub operations.
- `brave-search`: turn on when you need live web search.
- `obsidian`: turn on when you need to read from or write to your Obsidian vault.
- `docker-mcp` or `MCP_DOCKER`: turn on when the task depends on Docker-managed MCP services.
- `coexistai`: turn on only if you specifically need that remote MCP endpoint.
- `playwright`: turn on when browser automation or UI validation is required.
- `docs-lookup`: turn on when you need external documentation retrieval through MCP instead of local files.
- `database`: turn on when you need database inspection or queries outside the repo.
- `cloud`: turn on when you need cloud resource access.

Leave MCPs off for normal coding, file editing, refactoring, and project structure work inside `G:\MidTier\AI-Projects\...`.

## Agent roles
- Planner: analyzes the current repository or project request and writes an executable implementation plan.
- Validator: checks that the plan is valid and aligns with the project goals.
- Executor: runs the implementation plan to create, modify, or delete files as needed.

# Implementation Plan

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