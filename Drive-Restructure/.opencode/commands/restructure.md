# /restructure

Agent: restructure-planner

## What to do

1. The user will tell you a drive or folder path.
2. Call the bash tool with: `ls -1 "J:/"` to see what is inside it. Use forward slashes.
3. Decide how to organize the contents into a clean folder structure.
4. Use the write tool to save the plan to `.opencode/plans/restructure-plan.md`

## Plan format

The plan MUST have a table like this:

| Step | Action | Source | Destination |
|------|--------|--------|-------------|
| 1 | mkdir | | J:/Personal |
| 2 | mkdir | | J:/Projects |
| 3 | move | J:/C-File | J:/Personal/Legal-Documents |
| 4 | move | J:/OldStuff | J:/Archives/OldStuff |

Rules for the table:
- Use forward slashes in all paths (J:/ not J:\)
- Action is either `mkdir` or `move`
- For mkdir rows, Source is empty, Destination is the folder to create
- For move rows, Source and Destination are full absolute paths
- Source names must EXACTLY match the output from `ls` — do not guess
- No wildcards. No vague descriptions. Every path must be exact.
- mkdir rows come before move rows that depend on them
- Destinations must NOT be inside source paths

## Do NOT do these things
- Do not move, rename, or delete any files
- Do not use windows-mcp or MCP tools
- Do not send notifications
- Do not scan drives the user did not name
- Do not use the list tool (it does not exist)
- After writing the plan, stop
