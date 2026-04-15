# Codex Permission Configuration

Do not commit a full `~/.codex/config.toml` to this repository. User-level Codex config can contain API keys, Zotero credentials, OAuth state, absolute local paths, and machine-specific MCP commands.

For this workspace, document the required permission settings and let each user apply them to their own `~/.codex/config.toml`. Codex also supports project-scoped `.codex/config.toml` files, but they are loaded only when the project is trusted, so the trust entry still belongs in the user's private config.

Reference: <https://developers.openai.com/codex/config-reference>

## Recommended User-Level Settings

Add or merge the following into `~/.codex/config.toml`, replacing the path with the local absolute path to this repository:

```toml
# Keep shell commands sandboxed to the workspace, but allow normal paper
# research setup work such as dependency downloads and MCP network calls.
approval_policy = "on-request"
sandbox_mode = "workspace-write"

[sandbox_workspace_write]
network_access = true
writable_roots = [
  "/absolute/path/to/researches",
  "/tmp",
]

[projects."/absolute/path/to/researches"]
trust_level = "trusted"
```

This is the recommended default for shared research work. It reduces repeated permission prompts for ordinary networked setup while keeping writes scoped to the workspace and explicit writable roots.

## Low-Prompt Local Automation

For unattended or highly repetitive local runs, a user may choose:

```toml
approval_policy = "never"
sandbox_mode = "workspace-write"

[sandbox_workspace_write]
network_access = true
writable_roots = [
  "/absolute/path/to/researches",
  "/tmp",
]

[projects."/absolute/path/to/researches"]
trust_level = "trusted"
```

`approval_policy = "never"` suppresses approval prompts, but it does not grant filesystem access outside the sandbox. Use this only when the workspace and requested automation are trusted.

## Full Access Mode

Avoid documenting or committing full-access mode as the default. If a user intentionally wants Codex to run without sandboxing, they can set it privately:

```toml
approval_policy = "never"
sandbox_mode = "danger-full-access"
```

This is equivalent in risk to running arbitrary commands directly on the machine. Use it only in an externally sandboxed VM/container or a disposable environment.

## MCP Tool Approval Overrides

Per-tool MCP approval can be stored in the private user config. This is useful for frequently used paper-research tools:

```toml
[mcp_servers.openalex.tools.search_works]
approval_mode = "approve"

[mcp_servers.openalex.tools.get_work]
approval_mode = "approve"

[mcp_servers.paper-search.tools.search_semantic]
approval_mode = "approve"

[mcp_servers.paper-search.tools.download_with_fallback]
approval_mode = "approve"

[mcp_servers.zotero-full.tools.zotero_get_item_metadata]
approval_mode = "approve"

[mcp_servers.zotero-full.tools.zotero_get_item_children]
approval_mode = "approve"

[mcp_servers.zotero-full.tools.zotero_get_item_fulltext]
approval_mode = "approve"
```

Add more `approval_mode = "approve"` entries only for tools the user is comfortable running automatically. Keep MCP `env` blocks that contain API keys or user IDs in `~/.codex/config.toml`; never place secrets in repository files.
