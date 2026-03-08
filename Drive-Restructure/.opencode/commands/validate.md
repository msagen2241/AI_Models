# /validate

Agent: restructure-validator

## What to do

1. Use the read tool to load `.opencode/plans/restructure-plan.md`
2. Find the table with Step, Action, Source, Destination columns
3. Pick 3 to 5 rows where Action is `move`
4. For each picked row, call the bash tool with: `ls -d "SOURCE_PATH"`
5. Print PASS if the source exists, FAIL if it does not
6. Stop after reporting results

## Do NOT do these things
- Do not move, rename, or delete any files
- Do not modify the plan
- Do not use windows-mcp or MCP tools
- Do not send notifications
- Do not use the list tool (it does not exist)
