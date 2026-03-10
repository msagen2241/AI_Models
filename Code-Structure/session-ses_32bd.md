# <seed:think>

**Session ID:** ses_32bde2ac4ffeedviHvGp3Occgd
**Created:** 3/9/2026, 12:45:13 PM
**Updated:** 3/9/2026, 12:47:56 PM

---

## User

# /plan-structure

Agent: project-planner

IMPORTANT: This is Windows with Git Bash.

PATH RULES — CRITICAL:
- ALWAYS use forward slashes: G:/MidTier/AI-Projects/
- NEVER use backslashes. NEVER use ../ or ..\ prefixes.
- The plan file path is exactly: G:/MidTier/AI-Projects/Code-Structure/.opencode/plans/code-structure-plan.md

## Tool parameter names

- read tool: use `filePath` parameter. Example: `{"filePath": "path/to/file"}`
- write tool: use `filePath` and `content` parameters.
- glob tool: use `pattern` and `path` parameters to list files.

## What to do

1. Read the user's project request and determine the target project folder.
2. If the user did not provide a target path, use G:/MidTier/AI-Projects/ as the root and append the project name. Example: if user says "MudCommands", use G:/MidTier/AI-Projects/MudCommands
3. To list files in a directory, use the glob tool with pattern `*` and path set to the directory.
4. Use the read tool with filePath to read files.
5. Write exactly one plan to `G:/MidTier/AI-Projects/Code-Structure/.opencode/plans/code-structure-plan.md` (use this exact relative path, no prefixes).
6. The plan MUST contain a markdown table with columns: Step, Action, Path, Details, Content
7. Allowed actions: mkdir, write, edit, bash
8. All paths must be absolute with forward slashes: G:/MidTier/AI-Projects/MyProject
9. One atomic action per row. Put mkdir rows before rows that depend on them.
10. For every write row, put the complete file contents in the Content column. Do not leave Content blank for write rows.
11. Leave Content blank for mkdir, edit, and bash rows unless inline payload text is explicitly required.
12. After writing the plan file, STOP IMMEDIATELY. Do NOT create folders, write code files, or run commands.

## Do NOT ... (line truncated to 2000 chars)