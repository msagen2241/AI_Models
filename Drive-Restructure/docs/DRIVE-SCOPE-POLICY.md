# Drive Scope Policy

## Approved Drives

The following drives are approved for access in `opencode.json`:

| Drive | Type | Notes |
|-------|------|-------|
| C:\ | System | Windows system drive |
| D:\ | Local | |
| E:\ | Local | |
| F:\ | Local | |
| G:\ | Local | Contains this workspace |
| H:\ | Local | |
| I:\ | Removable | May not always be available |
| J:\ | Removable | May not always be available |

## Access Does Not Mean Automatic Scanning

Having a drive in the approved list means the workspace **can** access it — not that it **will**. No drive is scanned unless you explicitly name it in a command, plan input, or approved task scope.

For example:
- `/restructure D:\Projects` — scans only `D:\Projects`
- `/restructure` with no scope — the agent will ask you to specify one

## Removable Drives (I:\ and J:\)

Removable drives may not always be connected. When a command or plan references I:\ or J:\:

1. The agent will attempt to verify the drive is accessible (e.g., `list I:\`)
2. If the drive is **unavailable**, the agent will:
   - Report clearly: "Drive I:\ is not currently available"
   - Stop any step that depends on that drive
   - NOT substitute another path
   - NOT silently skip the step

## Why Wide Access Scope + Narrow Task Scope

The workspace has access to many drives because restructuring projects may span multiple drives. But each individual run should target only the specific paths relevant to that task.

Wide access scope = you don't have to reconfigure permissions for each drive.
Narrow task scope = you stay in control of what gets scanned and moved.

## Editing Approved Drives

To add or remove approved drives, edit the `external_directory` array in `opencode.json`. The array uses last-match-wins ordering: the first entry denies everything (`*`), and subsequent entries allow specific paths.
