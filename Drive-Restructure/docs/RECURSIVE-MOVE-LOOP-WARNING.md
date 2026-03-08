# Recursive Move Loop Warning

## What Is a Recursive Move Loop?

A recursive move loop happens when a file restructuring system moves files into a folder that it is also scanning as a source. The system finds the files again in their new location and moves them again, creating an endless cycle of nested moves.

## How It Happens

### Example 1: Destination Inside Source

You are restructuring `D:\Projects` and your plan says:

```
D:\Projects\old-app\*.js  ->  D:\Projects\Archived\old-app\*.js
```

The destination `D:\Projects\Archived\` is inside the source root `D:\Projects\`. If the system rescans `D:\Projects` after the first move, it will find the files under `D:\Projects\Archived\old-app\` and try to move them again — possibly to `D:\Projects\Archived\Archived\old-app\`, and so on.

### Example 2: Re-scanning Output Folders

You move files from `E:\Downloads` into `E:\Sorted\Documents`. Then the system scans `E:\Sorted` as part of a second pass. It finds the files you just moved and tries to move them again.

### Example 3: Staging Folder Treated as Source

Your workspace uses `staging\` as a temporary holding area. If the planner scans the staging folder, it will try to "organize" the staged files, creating a loop.

## Why It's Dangerous

- Files end up deeply nested: `Archived\Archived\Archived\Archived\file.txt`
- Original directory structure is destroyed
- Recovery requires manual unwinding of potentially thousands of nested moves
- The loop may consume disk space by creating deeply nested directory trees

## How This Workspace Prevents It

1. **Destination paths must never be descendants of source scan roots** — enforced in planning and execution
2. **Path comparisons are normalized and case-insensitive** — `D:\projects` and `D:\Projects` are correctly recognized as the same path
3. **Output folders are never rescanned** — staging, logs, plans, and destination folders are excluded from source input
4. **The executor refuses destination-inside-source moves** — even if a plan somehow contained one, the executor would reject it
