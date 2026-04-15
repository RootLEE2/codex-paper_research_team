# Troubleshooting

Use this file only when setup or a paper research run is blocked.

## Skill Not Detected

If `$paper-research-team` is not detected, verify `.agents/skills/paper-research-team/SKILL.md` exists and restart Codex from the workspace root.

## Consensus Auth

If Consensus tools do not appear or auth expires:

```bash
codex mcp logout consensus
codex mcp login consensus
```

If Codex prints an OAuth URL, tell the user to approve access in the browser and wait for login success.

## Zotero Full Unavailable

If `zotero-full` is unavailable:

```bash
which zotero-mcp
zotero-mcp version
codex mcp list
```

If Zotero operations fail, ask the user to open Zotero Desktop and retry.

## Python Install Fails

If package installation fails because of network restrictions, request approval and rerun the install command from [paper-research-skill.md](paper-research-skill.md). If system Python is externally managed, do not use `--break-system-packages`; use the skill-local venv.

## Summary Validation Agent Blocked

If active subagent thread limits prevent a separate Summary Validation Agent, close completed agents first. If that still fails, run validation serially and record the fallback in the active session output, not in `process-log.md` unless the user requested one.
