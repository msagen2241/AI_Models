# CRITICAL: Execute, do not narrate

When the task is implementation, you must use tools to make changes before responding.

- Do not output a plan, checklist, or instructions instead of making changes.
- Do not mark a step complete unless the files were actually created or modified or the command was actually run.

# Shell and tool rules

- Use native tools first: bash, read, write, edit, glob, grep, tools, todowrite, todoread.
- The `list` tool does NOT exist. To list files, use bash with `ls`.
- Two MCPs are enabled: Context7 and Brave Search. All others are disabled.
- For documentation lookups: try Context7 first, then brave_web_search if Context7 has no results.
- NEVER skip the lookup. Do not rely on training knowledge alone for library/framework docs.
- Use the read tool with `filePath` parameter (not `file`).
- Use the bash tool with `command` parameter (not `cmd`, not `shell`).
- This is Windows with Git Bash. Use forward slashes. Use `mkdir -p`. Use `mv` not `move`.
- If a permission blocks a required action, report and stop.

# Planning and execution contract

- The planner must write `G:/MidTier/AI-Projects/Code-Structure/.opencode/plans/code-structure-plan.md`.
- The plan must include a markdown execution table with columns: `Step`, `Action`, `Path`, `Details`, `Content`.
- Allowed `Action` values are: `mkdir`, `write`, `edit`, `bash`.
- Every `write` row must include the complete file contents in `Content`.
- `mkdir`, `edit`, and `bash` rows should leave `Content` blank unless inline payload text is explicitly required.
- The executor must go through the execution table row by row and perform exactly one tool-backed action per row.
- The executor must never call `write` unless both `Path` and `Content` are non-empty strings; malformed `write` rows must be reported and skipped/stopped rather than guessed.
- After execution, the executor must verify the affected path or command result before marking the row complete.