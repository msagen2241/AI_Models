# MCP Guidance

MCP is optional in this workspace.

Use native tools for local repository editing, search, file inspection, refactoring, and validation.

Use MCP when external systems clearly benefit from it, including:
- GitHub workflows
- Playwright or other browser automation
- Documentation lookup
- Database access
- Cloud or remote systems

The operating rule is simple: native for the repo, MCP for the world outside the repo.

## Included MCP entries in this workspace
- `windows-mcp`: use for Windows-specific filesystem or shell context that goes beyond ordinary local repo operations.
- `github`: use for remote GitHub actions such as PRs, issues, and repo metadata.
- `brave-search`: use for live internet search.
- `obsidian`: use for notes or vault content.
- `docker-mcp` and `MCP_DOCKER`: use when Docker-backed MCP services are required.
- `coexistai`: use only when you intentionally want that remote MCP endpoint.
- `playwright`: use for browser automation.
- `docs-lookup`: use for external docs retrieval.
- `database`: use for database work.
- `cloud`: use for cloud systems.

## Default operating guidance
- Keep MCP optional.
- Prefer native tools for code generation, editing, search, validation, and restructuring inside project folders.
- Turn on only the MCPs needed for the current task.
- If a task is fully local to the repo, do not route it through MCP.