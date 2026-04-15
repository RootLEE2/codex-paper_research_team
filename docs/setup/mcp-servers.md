# MCP Servers

Use this file to configure MCP servers for the paper research workflow.

## Expected Servers

Run:

```bash
codex mcp list
```

Register missing servers. Do not duplicate servers already present.

Expected MCP names:

```text
openalex
paper-search
consensus
zotero-full
```

Optional read fallback:

```text
zotero
```

## OpenAlex

Register an OpenAlex MCP server as `openalex`. Use it as the primary source for broad search, metadata, venues, citation/reference expansion, and related works.

## Paper Search / Semantic Scholar

Register the paper-search MCP server as `paper-search`. It should expose Semantic Scholar search and PDF fallback tools such as `search_semantic`, `download_with_fallback`, and DOI lookup helpers.

## Consensus

Register the official Consensus MCP:

```bash
codex mcp add consensus --url https://mcp.consensus.app/mcp
codex mcp login consensus
```

If Codex prints an OAuth URL, tell the user to approve access in the browser and wait for login success.

## Zotero Full

Install:

```bash
uv tool install zotero-mcp-server
```

Find the executable:

```bash
which zotero-mcp
```

Register with local Zotero:

```bash
codex mcp add zotero-full --env ZOTERO_LOCAL=true -- /absolute/path/to/zotero-mcp serve --transport stdio
```

If local Zotero MCP cannot write reliably in the current environment, configure Zotero Web API credentials through `codex mcp add` env values instead of placing secrets in repository files.

Use `zotero-full` for Zotero write operations, DOI import, collection/tag management, existing PDF lookup, and open-access PDF cascade.

## Secrets

Keep MCP `env` blocks that contain API keys, user IDs, or OAuth data in `~/.codex/config.toml` or through `codex mcp add --env`. Never place secrets in repository files.
