# Code-Structure Workspace

This workspace is for coding, project creation, codebase cleanup, repo structuring, architecture planning, validation, implementation, and review on Windows.

## Why native tools come first
Native local tools are the default for repository work because they are direct, fast, and well-suited to reading, editing, searching, listing, and validating files inside a local project. They should handle the normal coding loop for local repos without depending on MCP.

## When MCP makes sense
MCP is optional here. Use it when the workflow needs to interact with systems outside the local repository, such as GitHub, browser automation with Playwright, documentation lookup, databases, cloud services, or other remote tools. Native for the repo, MCP for the world outside the repo.

## When to turn MCPs on
- `windows-mcp`: turn on when you need Windows-specific filesystem browsing outside the normal local repo tool flow.
- `github`: turn on when you need repository, pull request, issue, or remote GitHub operations.
- `brave-search`: turn on when you need live web search.
- `obsidian`: turn on when you need to read from or write to your Obsidian vault.
- `docker-mcp` or `MCP_DOCKER`: turn on when the task depends on Docker-managed MCP services.
- `coexistai`: turn on only if you specifically need that remote MCP endpoint.
- `playwright`: turn on when browser automation or UI validation is required.
- `docs-lookup`: turn on when you need external documentation retrieval through MCP instead of local files.
- `database`: turn on when you need database inspection or queries outside the repo.
- `cloud`: turn on when you need cloud resource access.

Leave MCPs off for normal coding, file editing, refactoring, and project structure work inside `G:\MidTier\AI-Projects\...`.

## Agent roles
- Planner: analyzes the current repository or project request and writes an executable implementation plan.
- Validator: checks that changes are correct and meet the task requirements.
- Executor: runs the planned actions to implement changes.