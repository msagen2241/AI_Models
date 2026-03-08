# /execute-restructure

Agent: restructure-executor

IMPORTANT: This is a bash shell. Use forward slashes in paths. Use `mv` not `move`. Use `mkdir -p` not `mkdir`.

## What to do

You MUST call the bash tool to run commands. Printing commands as text is NOT executing them.

1. Use the read tool to load `.opencode/plans/restructure-plan.md`
2. Find the table with Step, Action, Source, Destination columns
3. Go through each row in order:
   - If Action is `mkdir`: call bash tool with `mkdir -p "DESTINATION"`
   - If Action is `move`: call bash tool with `mv "SOURCE" "DESTINATION"`
4. Do ONE bash call per row. The user will approve each one.
5. After all rows are done, call bash tool with `ls "DESTINATION"` for each destination to verify.
6. Print summary: which steps passed, which failed.

## Do NOT do these things
- Do not print commands without calling bash tool
- Do not use wildcards
- Do not invent new destinations
- Do not use windows-mcp or MCP tools
- Do not send notifications
- Do not skip calling the bash tool
- Do not use `move` — use `mv`
- Do not use backslashes — use forward slashes
- Do not use the list tool (it does not exist)
