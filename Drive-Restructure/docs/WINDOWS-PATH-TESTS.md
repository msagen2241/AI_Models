# Windows Path Behavior Tests

Windows path behavior is not fully documented and should be tested locally before relying on it for file restructuring.

## Purpose

Verify that `list` and `glob` tools handle Windows drive paths correctly in your environment.

## Test Procedure

For each drive path below, run `list` and `glob` and compare results. Note any differences in behavior between forward-slash and backslash variants.

### Tests

| # | Path | Tool | Expected | Actual | Notes |
|---|------|------|----------|--------|-------|
| 1 | `G:\` | list | Lists G: root | | |
| 2 | `G:/` | list | Lists G: root | | |
| 3 | `G:\` | glob `*` | Lists G: root entries | | |
| 4 | `G:/` | glob `*` | Lists G: root entries | | |
| 5 | `C:\` | list | Lists C: root | | |
| 6 | `C:/` | list | Lists C: root | | |
| 7 | `C:\` | glob `*` | Lists C: root entries | | |
| 8 | `C:/` | glob `*` | Lists C: root entries | | |
| 9 | `D:\` | list | Lists D: root | | |
| 10 | `D:/` | list | Lists D: root | | |
| 11 | `D:\` | glob `*` | Lists D: root entries | | |
| 12 | `D:/` | glob `*` | Lists D: root entries | | |
| 13 | `I:\` | list | Lists I: root or reports unavailable | | |
| 14 | `I:/` | list | Lists I: root or reports unavailable | | |
| 15 | `I:\` | glob `*` | Lists I: root entries or reports unavailable | | |
| 16 | `I:/` | glob `*` | Lists I: root entries or reports unavailable | | |
| 17 | `J:\` | list | Lists J: root or reports unavailable | | |
| 18 | `J:/` | list | Lists J: root or reports unavailable | | |
| 19 | `J:\` | glob `*` | Lists J: root entries or reports unavailable | | |
| 20 | `J:/` | glob `*` | Lists J: root entries or reports unavailable | | |

## What to Watch For

- Do `G:\` and `G:/` produce identical results?
- Does `glob *` at a drive root behave the same as `list`?
- Do removable drives (I:\, J:\) produce a clear error when unavailable, or do they silently return empty?
- Are trailing backslashes required, optional, or problematic?
- Does case matter for drive letters? (Test `g:\` vs `G:\`)

## Action

Fill in the "Actual" and "Notes" columns by running each test. If any test produces unexpected results, document the discrepancy before running a real restructure.
