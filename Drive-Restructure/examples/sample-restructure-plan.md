# Restructure Plan — SAMPLE (Not Real)

> **This is a fake example showing the expected plan format. All paths are fictional. Do not execute.**

---

## 1. Summary

Restructuring `D:\ExampleProjects` to consolidate scattered project files into a clean taxonomy. Approximately 45 folders and 320 files identified.

## 2. Proposed Folder Taxonomy

```
D:\Organized\
├── WebApps\
├── Scripts\
├── Archives\
├── Documents\
└── Media\
```

## 3. Source → Destination Mappings

| # | Source | Destination |
|---|--------|-------------|
| 1 | `D:\ExampleProjects\old-site\` | `D:\Organized\WebApps\old-site\` |
| 2 | `D:\ExampleProjects\scripts\cleanup.ps1` | `D:\Organized\Scripts\cleanup.ps1` |
| 3 | `D:\ExampleProjects\scripts\deploy.sh` | `D:\Organized\Scripts\deploy.sh` |
| 4 | `D:\ExampleProjects\archive-2023.zip` | `D:\Organized\Archives\archive-2023.zip` |
| 5 | `D:\ExampleProjects\notes.docx` | `D:\Organized\Documents\notes.docx` |
| 6 | `D:\ExampleProjects\demo-video.mp4` | `D:\Organized\Media\demo-video.mp4` |

## 4. Ambiguities and Risk Notes

- `D:\ExampleProjects\misc\` contains 12 files with no clear category. Placed in `Documents\` by default — review recommended.
- `D:\ExampleProjects\old-site\node_modules\` is 800MB. Consider deleting instead of moving.
- Two files named `config.json` exist in different source folders — destinations are distinct so no conflict.

## 5. Validation Checklist

- [ ] Verify `D:\ExampleProjects\old-site\` still exists
- [ ] Verify `D:\ExampleProjects\scripts\cleanup.ps1` still exists
- [ ] Verify `D:\Organized\` is NOT a descendant of `D:\ExampleProjects\`
- [ ] Verify `D:\Organized\` does not already contain conflicting files
- [ ] Confirm no destination path is inside the source scan root

## 6. Execution Notes

- Create `D:\Organized\` and all subdirectories before moving files
- Move folders before individual files to preserve structure
- The executor should process moves in table order (1 through 6)
- If any move fails due to permissions, stop and report — do not skip
