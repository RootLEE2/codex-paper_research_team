# Codex Setup for Paper Research Team

This document is the setup index for Codex agents installing, restoring, or verifying the paper research automation in this workspace. Human-facing usage guidance belongs in [README.md](README.md).

Detailed setup instructions live under `docs/setup/` so each topic stays small and reusable.

## Objective

Set up a project-local paper research system that can search papers broadly, screen candidates before Zotero storage, save only selected `core` and approved `supporting` papers, acquire PDFs when available, write source-grounded Obsidian notes, validate notes before synthesis, synthesize the literature review, and run a professor-style review gate.

## Non-Goals

- Do not save every search candidate to Zotero.
- Do not create normal Obsidian notes for papers without PDFs, preprints, or confirmed full text.
- Do not run final synthesis or final professor review while required selected full text is missing.
- Do not create `process-log.md` by default. Create it only when the user explicitly asks for a process log, first-run trace, or process-visibility artifact.

## Manual Prerequisites

Codex may create files, adjust project-local skill docs, register MCP servers, and install Python packages when approved. The user must install and sign into desktop tools:

- Zotero Desktop
- Obsidian
- Codex CLI
- Optional: browser Zotero Connector
- Optional: ZotMoov/ZotFile-style PDF management

Before running a real pipeline, ask the user to open Zotero Desktop and keep it running.

## Setup Order

1. Review Codex permission settings: [docs/setup/codex-permissions.md](docs/setup/codex-permissions.md)
2. Inspect/create runtime folders: [docs/setup/runtime-directories.md](docs/setup/runtime-directories.md)
3. Create/fill `research-profile.md` and initialize local taxonomy registries: [docs/setup/local-taxonomy.md](docs/setup/local-taxonomy.md)
4. Restore the local paper-research skill: [docs/setup/paper-research-skill.md](docs/setup/paper-research-skill.md)
5. Configure Obsidian and Zotero behavior: [docs/setup/obsidian-zotero.md](docs/setup/obsidian-zotero.md)
6. Configure MCP servers: [docs/setup/mcp-servers.md](docs/setup/mcp-servers.md)
7. Restart and verify installation: [docs/setup/verification.md](docs/setup/verification.md)
8. Use troubleshooting notes only when blocked: [docs/setup/troubleshooting.md](docs/setup/troubleshooting.md)

## Operating Rules

- Work from the workspace root.
- Preserve user changes unless the user explicitly says existing files can be overwritten.
- Inspect existing files before replacing them.
- Prefer `rg`, `find`, and targeted file reads for inspection.
- Use `apply_patch` for manual file edits.
- Request permission when a command needs network access, OAuth login, external package installation, GUI access, or destructive cleanup.
- Keep setup and policy docs hierarchical. Put reusable details in subfiles instead of making one huge instruction file.
- After setup changes, run the verification checklist in [docs/setup/verification.md](docs/setup/verification.md).

## Quick Checklist

- Root `AGENTS.md` routes paper research requests to `$paper-research-team`.
- `.agents/skills/paper-research-team/SKILL.md` exists and points to `config.yaml` and `references/workflow.md`.
- Runtime folders exist under `papers/`, `papers/obsidian/`, `papers/state/`, and `literature-reviews/`.
- `research-profile.md` exists and has local domain, method, venue, and keyword seeds for taxonomy registry initialization.
- Local taxonomy registries exist: `domain-registry.md`, `method-registry.md`, `venue-registry.md`, and `keyword-registry.md`.
- Python fallback environment exists at `.agents/skills/paper-research-team/.venv`.
- Expected MCP servers are registered: `openalex`, `paper-search`, `consensus`, and `zotero-full`.
- Zotero Desktop is open before Zotero write/PDF attachment operations.
- Obsidian note policy requires source-grounded deep extraction notes, not metadata-level notes.
- Missing full text remains in pending handling and blocks final synthesis/review.

## First Test Prompt

After restarting Codex from the workspace root, test with:

```text
$paper-research-team으로 논문 조사 시작해줘. 주제는 <조사할 주제>야. Zotero 저장 전 screening 결과부터 보여줘.
```

Expected behavior is documented in [docs/setup/verification.md](docs/setup/verification.md).

## Final Report to User

When installation or restoration is complete, report:

- Files created or updated.
- MCP servers registered.
- Which MCPs still need authentication or account verification.
- Whether Python venv verification passed.
- Whether a Codex restart is needed.
