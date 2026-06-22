# Claude Code Guide

Follow `AGENTS.md` for repository ownership, security, implementation, and
verification rules.

## MCP

This repository ships a project-scoped Claude Code MCP configuration in
`.mcp.json`. When Claude Code opens the repository, approve the
`x-search-plugin` MCP server if prompted, then check `/mcp`.

Equivalent manual registration:

```bash
claude mcp add --transport stdio --scope project x-search-plugin -- uv run --quiet --locked python "$PWD/scripts/x_search_mcp.py"
```

The server is read-only and exposes X/Twitter research tools backed by xAI
`x_search`. Do not use it for posting, liking, following, DMs, or any account
mutation.

## Auth

Prefer local xAI OAuth:

```bash
uv run --quiet --locked python scripts/x_search_auth.py login
```

Do not read or print local credential files. OAuth state is stored at
`~/.x-search-plugin/auth.json` by default, with legacy fallback to
`~/.x-search-codex/auth.json`.

