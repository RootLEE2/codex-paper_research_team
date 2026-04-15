# Codex Setup for Paper Research Team

This document is for Codex agents installing, restoring, or verifying the paper research automation in this workspace. Human-facing usage guidance belongs in [README.md](README.md).

## Objective

Set up a project-local paper research system that can:

- Search academic papers broadly.
- Screen candidates before Zotero storage.
- Save only selected `core` and approved `supporting` papers to Zotero.
- Reuse existing Zotero items, PDFs, and Obsidian notes when appropriate.
- Acquire PDFs when available.
- Ask the user for missing PDFs.
- Write reusable Obsidian paper notes only from confirmed full text.
- Validate notes with a separate Summary Validation Agent before synthesis.
- Synthesize the literature review.
- Run a professor-style review gate and repeat full cycles until the review passes or the user stops the loop.

## Non-Goals

- Do not save every search candidate to Zotero.
- Do not create normal Obsidian notes for papers without PDFs, preprints, or confirmed full text.
- Do not run final synthesis or final professor review while required selected PDFs are missing.
- Do not create `process-log.md` by default. Create it only when the user explicitly asks for a process log, first-run trace, or process-visibility artifact.

## Manual Prerequisites

Codex may create files, adjust project-local skill docs, register MCP servers, and install Python packages when approved. The user must install and sign into desktop tools:

- Zotero Desktop
- Obsidian
- Codex CLI
- Optional: browser Zotero Connector
- Optional: ZotMoov/ZotFile-style PDF management

Before running a real pipeline, ask the user to open Zotero Desktop and keep it running.

## Operating Rules

- Work from the workspace root.
- Preserve user changes unless the user explicitly says existing files can be overwritten.
- Inspect existing files before replacing them.
- Prefer `rg`, `find`, and targeted file reads for inspection.
- Use `apply_patch` for manual file edits.
- Request permission when a command needs network access, OAuth login, external package installation, GUI access, or destructive cleanup.
- Keep setup and policy docs hierarchical. Put reusable details in subfiles instead of making one huge instruction file.
- After setup changes, run the verification checklist below.

## Expected Structure

```text
AGENTS.md
README.md
SETUP.md
.agents/skills/paper-research-team/SKILL.md
.agents/skills/paper-research-team/agents/openai.yaml
.agents/skills/paper-research-team/config.yaml
.agents/skills/paper-research-team/references/workflow.md
.agents/skills/paper-research-team/references/agent-roles.md
.agents/skills/paper-research-team/references/schemas.md
.agents/skills/paper-research-team/references/screening-rubric.md
.agents/skills/paper-research-team/references/agents/*.md
.agents/skills/paper-research-team/references/policies/*.md
.agents/skills/paper-research-team/references/workflows/*.md
.agents/skills/paper-research-team/references/schemas/*.md
papers/zotero/
papers/obsidian/notes/
papers/obsidian/pending-notes/
papers/obsidian/_templates/paper-note-template.md
papers/obsidian/_indexes/tag-registry.md
papers/obsidian/_indexes/keyword-registry.md
literature-reviews/
```

If instruction files are missing and the user provided equivalents, create them in the target structure. If only a subset is available, create runtime directories and report which instruction files are missing.

## Step 1: Inspect Current State

Run:

```bash
pwd
find . -maxdepth 3 -name AGENTS.md -o -path './.agents/skills/*/SKILL.md' -o -path './papers/obsidian/_templates/*' -o -path './papers/obsidian/_indexes/*'
codex mcp list
```

Determine:

- Workspace root path.
- Whether `.agents/skills/paper-research-team` exists.
- Whether root `AGENTS.md` routes paper research requests to `$paper-research-team`.
- Whether Obsidian templates and indexes exist.
- Which MCP servers are registered.

## Step 2: Create Runtime Directories

Run:

```bash
mkdir -p papers/zotero
mkdir -p papers/obsidian/notes
mkdir -p papers/obsidian/pending-notes
mkdir -p papers/obsidian/syntheses
mkdir -p papers/obsidian/reviews
mkdir -p papers/state/sessions
mkdir -p papers/state/candidates
mkdir -p papers/state/screened
mkdir -p papers/state/pending_pdf
mkdir -p literature-reviews
mkdir -p .agents/skills/paper-research-team/agents
mkdir -p .agents/skills/paper-research-team/references/agents
mkdir -p .agents/skills/paper-research-team/references/policies
mkdir -p .agents/skills/paper-research-team/references/schemas
mkdir -p .agents/skills/paper-research-team/references/workflows
```

## Step 3: Ensure Root Router

Ensure `AGENTS.md` contains routing instructions equivalent to:

```markdown
# Researches Project Instructions

## Paper Research Requests

When the user asks to search papers, conduct a literature review, find related work, expand references or citations, manage papers in Zotero, download PDFs, summarize PDFs, write Obsidian paper notes, or run an iterative paper research pipeline, use the project-local skill:

`$paper-research-team`

The skill entry point is:

`.agents/skills/paper-research-team/SKILL.md`
```

Merge with unrelated project instructions instead of replacing the whole file.

## Step 4: Ensure Skill Entrypoint

Ensure `.agents/skills/paper-research-team/SKILL.md` exists with frontmatter similar to:

```yaml
---
name: paper-research-team
description: Use when the user asks to search academic papers, conduct a literature review, find related work, expand references or citations, use OpenAlex, Semantic Scholar, or Consensus, save papers to Zotero, download PDFs, summarize PDFs into Obsidian, manage paper tags, synthesize literature, request missing PDFs, or run an iterative professor-reviewed paper research pipeline.
metadata:
  short-description: Search, screen, save, analyze, and synthesize papers.
---
```

The body must instruct Codex to:

- Read `config.yaml`.
- Read `references/workflow.md`.
- Start with Research Orchestrator.
- Search broadly but not save unscreened candidates to Zotero.
- Save only screened `core` and approved `supporting` papers.
- Use actual subagents for separable phases when feasible.
- Keep Paper Analyst, Summary Validation Agent, Synthesis Agent, and Professor Reviewer separate.
- Reuse existing Zotero items and Obsidian notes for selected core/supporting papers when appropriate.
- Stop before final synthesis/review if required selected full text is missing.
- Resume pending papers after the user reports PDFs were added.
- Avoid default `process-log.md` creation.

## Step 5: Ensure Runtime Config

Ensure `.agents/skills/paper-research-team/config.yaml` includes current policy values:

```yaml
agents:
  use_actual_subagents_when_feasible: true
  inline_only_when_subagents_unavailable_or_user_forbids: true
  record_agent_assignments_in_session_outputs: true
  create_process_log_by_default: false
  process_log_only_when_user_requests: true

zotero:
  auto_save_selected_after_screening: true
  do_not_defer_selected_import_for_process_visibility_runs: true
  save_statuses:
    - "core"
    - "supporting"

pdf:
  analyze_only_when_pdf_available: true
  continue_when_pdf_missing: false
  continue_search_and_screening_when_pdf_missing: true
  block_synthesis_and_review_when_required_pdf_missing: true

obsidian:
  language: "ko"
  note_body_language: "ko"
  preserve_original_titles_terms_tags: true
  preserve_technical_terms_and_concepts: true
  pending_notes_dir: "papers/obsidian/pending-notes"
  keyword_registry: "papers/obsidian/_indexes/keyword-registry.md"
  keyword_registry_is_local_only: true
  auto_create_keyword_registry: true
  normal_notes_require_full_text: true

note_validation:
  required_before_synthesis: true
  use_separate_agent: true

review_loop:
  restart_full_cycle_when_review_says_insufficient: true
  repeat_until_professor_review_passes_or_user_stops: true
```

Search sources should include OpenAlex, Semantic Scholar, Consensus, and Zotero reuse.

## Step 6: Ensure Obsidian Files

Ensure `papers/obsidian/_templates/paper-note-template.md` summarizes only the paper itself. It must not include a section about the user's current research.

Required reusable note behavior:

- Explanatory body content in Korean.
- Original titles, authors, venues, DOI/URL, tags, technical terms, and concepts preserved.
- Normal notes only under `papers/obsidian/notes/`.
- Missing-PDF metadata or upload-needed records only under `papers/obsidian/pending-notes/`.
- Non-keyword tags come from `papers/obsidian/_indexes/tag-registry.md`.
- Keyword tags come from `papers/obsidian/_indexes/keyword-registry.md`.
- `keyword-registry.md` is local-only and should be ignored by Git.

Ensure `papers/obsidian/_indexes/tag-registry.md` contains controlled public tags for workflow, evidence role, domain, method, and venue. Keep actual reusable `#kw/*` tags in `keyword-registry.md`.

## Step 7: Install Python Fallback Environment

Do not copy an existing `.venv` from another machine. Recreate it.

Run:

```bash
python3 -m venv .agents/skills/paper-research-team/.venv
.agents/skills/paper-research-team/.venv/bin/pip install pyzotero requests watchdog pyyaml
```

Verify:

```bash
.agents/skills/paper-research-team/.venv/bin/python -c "import pyzotero, requests, watchdog, yaml; print('paper research venv ok')"
```

Expected output:

```text
paper research venv ok
```

If install fails because of network restrictions, request approval and rerun the install. If system Python is externally managed, do not use `--break-system-packages`; use the venv above.

## Step 8: Configure MCP Servers

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

### OpenAlex

Register an OpenAlex MCP server as `openalex`. Use it as the primary source for broad search, metadata, venues, citation/reference expansion, and related works.

### Paper Search / Semantic Scholar

Register the paper-search MCP server as `paper-search`. It should expose Semantic Scholar search and PDF fallback tools such as `search_semantic`, `download_with_fallback`, and DOI lookup helpers.

### Consensus

Register the official Consensus MCP:

```bash
codex mcp add consensus --url https://mcp.consensus.app/mcp
codex mcp login consensus
```

If Codex prints an OAuth URL, tell the user to approve access in the browser and wait for login success.

### Zotero Full

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

## Step 9: Zotero Desktop Check

Before running a real paper pipeline:

- Ask the user to open Zotero Desktop.
- Confirm Zotero local API/connector communication is enabled.
- Keep Zotero running during save/PDF operations.

If Zotero write/PDF operations fail, first check whether Zotero Desktop is open. If local MCP remains unavailable, fall back to Zotero Web API only when credentials are configured.

## Step 10: Restart Codex

After registering MCP servers or adding project-local skills, tell the user to restart Codex from the workspace root:

```bash
cd /absolute/path/to/researches
codex
```

New MCP tools and project-local skills may not appear in an already-running session.

## Step 11: Verify Installation

Run:

```bash
test -f AGENTS.md
test -f README.md
test -f SETUP.md
test -f .agents/skills/paper-research-team/SKILL.md
test -f .agents/skills/paper-research-team/config.yaml
test -f .agents/skills/paper-research-team/agents/openai.yaml
test -f papers/obsidian/_templates/paper-note-template.md
test -f papers/obsidian/_indexes/tag-registry.md
```

Validate YAML:

```bash
.agents/skills/paper-research-team/.venv/bin/python -c "import yaml; [yaml.safe_load(open(p, encoding='utf-8')) for p in ['.agents/skills/paper-research-team/config.yaml', '.agents/skills/paper-research-team/agents/openai.yaml']]; print('yaml ok')"
```

Check active policy text:

```bash
rg -n "create_process_log_by_default: false|process_log_only_when_user_requests: true|pending-notes|Summary Validation Agent|restart_full_cycle_when_review_says_insufficient|keyword-registry.md" .agents/skills/paper-research-team
```

Run:

```bash
codex mcp list
```

Expected active MCPs:

```text
openalex
paper-search
consensus
zotero-full
```

Optional:

```text
zotero
```

## Step 12: First Test Prompt

After restarting Codex from the workspace root, test with:

```text
$paper-research-team으로 논문 조사 시작해줘. 주제는 <조사할 주제>야. Zotero 저장 전 screening 결과부터 보여줘.
```

Expected behavior:

- The skill activates.
- OpenAlex and Semantic Scholar are used before Zotero reuse.
- Zotero is checked for deduplication and existing PDFs/notes after seed discovery.
- Consensus may be used for structured validation.
- Unscreened candidates are not saved to Zotero.
- Selected `core` and approved `supporting` papers are saved to Zotero unless the user explicitly skips Zotero writes.
- Missing PDFs are listed under pending handling and block final synthesis/review.
- `process-log.md` is not created unless the user explicitly requested process visibility.

## Troubleshooting

If `$paper-research-team` is not detected, verify `.agents/skills/paper-research-team/SKILL.md` exists and restart Codex from the workspace root.

If Consensus tools do not appear or auth expires:

```bash
codex mcp logout consensus
codex mcp login consensus
```

If `zotero-full` is unavailable:

```bash
which zotero-mcp
zotero-mcp version
codex mcp list
```

If Zotero operations fail, ask the user to open Zotero Desktop and retry.

If active subagent thread limits prevent a separate Summary Validation Agent, close completed agents first. If that still fails, run validation serially and record the fallback in the active session output, not in `process-log.md` unless the user requested one.

## Final Report to User

When installation or restoration is complete, report:

- Files created or updated.
- MCP servers registered.
- Which MCPs still need authentication or account verification.
- Whether Python venv verification passed.
- Whether a Codex restart is needed.
