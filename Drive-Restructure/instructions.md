# CRITICAL: Bash tool requires a description parameter

When calling the bash tool, you MUST ALWAYS include a `description` parameter.
Without it, the call will fail with a schema validation error.

CORRECT example:
bash(command="ls -1 J:/", description="List files on J drive")

INCORRECT example (WILL FAIL):
bash(command="ls -1 J:/")

Every single bash call needs both `command` and `description`.

# Shell is bash

- Use forward slashes: J:/ not J:\
- Use mv not move
- Use mkdir -p not mkdir
- Use ls not dir

# Available tools

bash, read, write, edit, glob, grep, todowrite, todoread, tools, skill.
The list tool does NOT exist. Use bash with ls instead.
Do NOT use windows-mcp, MCP tools, or Notification tools.
