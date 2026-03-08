# Rules for all agents

1. Use ONLY these tools: bash, read, write, edit, glob, grep.
2. The list tool does NOT exist. To list files, call bash with: ls -1 "path"
3. When calling the bash tool, ALWAYS include a description field. It is required.
4. Do NOT use windows-mcp, MCP tools, or Notification tools.
5. Use forward slashes in all paths (J:/ not J:\).
6. This is a bash shell. Use mv not move. Use mkdir -p not mkdir.
7. Never delete user files.
8. Never put a destination folder inside a source folder.
9. Never use wildcards in move commands.
10. Only scan drives or folders the user explicitly names.
11. If a drive is unavailable, say so and stop.
12. If permissions block something, say what was blocked and stop.
