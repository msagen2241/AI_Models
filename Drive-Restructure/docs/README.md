# Drive-Restructure Workspace

## What This Is

A hardened OpenCode CLI workspace for safely restructuring large Windows hard drives. The workflow enforces a strict **plan → validate → execute** pipeline with approval gates at every step.

## Why Native Tools Instead of Filesystem MCP Servers

- Native tools (list, glob, read, bash) are directly controlled by OpenCode's permission system
- No third-party server dependencies or trust boundaries
- Permissions are defined in `opencode.json` and enforced consistently
- Bash commands require explicit user approval via `ask` permission

## Agent Roles

| Agent | Purpose | Can Move Files? |
|---|---|---|
| **restructure-planner** | Inspects directories, produces a restructuring plan | No |
| **restructure-validator** | Spot-checks the plan against live filesystem | No |
| **restructure-executor** | Executes approved moves from the plan only | Yes (with approval) |

## Commands

### /restructure
- Runs the **planner** agent
- You MUST specify a drive or path scope (e.g., "restructure D:\Projects")
- Produces a plan at `.opencode/plans/restructure-plan.md`
- Does NOT move any files

### /validate
- Runs the **validator** agent
- Reads the existing plan and spot-checks 3–5 source paths
- Verifies destination safety
- Reports PASS/FAIL for each check

### /execute-restructure
- Runs the **executor** agent
- Reads the approved plan and executes moves one at a time
- Every move requires your approval
- Never invents new targets beyond the plan

## Recursive Move Loop Risk

The most dangerous failure mode in file restructuring is a **recursive move loop**: when a destination folder is inside a source scan root, causing the system to move files into a subfolder, then discover them again and move them deeper, repeatedly.

This workspace prevents this by:
- Requiring destination paths to be outside source scan roots
- Normalizing and case-insensitively comparing all paths
- Never rescanning output, destination, staging, or log folders

## External Directory Restrictions

The `external_directory` rules in `opencode.json` control which paths the workspace can access. Currently allowed:

- `G:\Midtier\AI-Projects\Drive-Restructure` (workspace root)
- `C:\`, `D:\`, `E:\`, `F:\`, `G:\`, `H:\`, `I:\`, `J:\`

**Having access does NOT mean automatic scanning.** Drives are only inspected when you explicitly name them in a command.

To edit allowed drive roots, modify the `external_directory` array in `opencode.json`.

## Testing Path Behavior

Before running a real restructure, test that `list` and `glob` work correctly with your drive paths. See `docs/WINDOWS-PATH-TESTS.md` for a test procedure.

Windows path handling has undocumented edge cases (forward vs backslash, trailing slashes, UNC paths). Always test locally before trusting path comparisons.
