# Verification

Use this file after setup, MCP registration, or local skill changes.

## Restart Codex

After registering MCP servers or adding project-local skills, tell the user to restart Codex from the workspace root:

```bash
cd /absolute/path/to/researches
codex
```

New MCP tools and project-local skills may not appear in an already-running session.

## Verify Installation

Run:

```bash
test -f AGENTS.md
test -f README.md
test -f SETUP.md
test -f docs/setup/local-taxonomy.md
test -f .agents/skills/paper-research-team/SKILL.md
test -f .agents/skills/paper-research-team/config.yaml
test -f .agents/skills/paper-research-team/agents/openai.yaml
test -f papers/obsidian/_templates/paper-note-template.md
test -f papers/obsidian/_indexes/tag-registry.md
test -f papers/obsidian/_indexes/research-profile.example.md
test -f papers/obsidian/_indexes/research-profile.md
test -f papers/obsidian/_indexes/domain-registry.md
test -f papers/obsidian/_indexes/method-registry.md
test -f papers/obsidian/_indexes/venue-registry.md
test -f papers/obsidian/_indexes/keyword-registry.md
```

Validate YAML:

```bash
.agents/skills/paper-research-team/.venv/bin/python -c "import yaml; [yaml.safe_load(open(p, encoding='utf-8')) for p in ['.agents/skills/paper-research-team/config.yaml', '.agents/skills/paper-research-team/agents/openai.yaml']]; print('yaml ok')"
```

Check active policy text:

```bash
rg -n "create_process_log_by_default: false|process_log_only_when_user_requests: true|pending-notes|Summary Validation Agent|restart_full_cycle_when_review_says_insufficient|research-profile.md|domain-registry.md|keyword-registry.md" .agents/skills/paper-research-team
```

Check local taxonomy setup:

```bash
rg -n "#domain/|#method/|#venue/|#kw/" papers/obsidian/_indexes/research-profile.md papers/obsidian/_indexes/domain-registry.md papers/obsidian/_indexes/method-registry.md papers/obsidian/_indexes/venue-registry.md papers/obsidian/_indexes/keyword-registry.md
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

## First Test Prompt

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
- Selected papers with available PDFs have those PDFs attached to Zotero items; otherwise they remain pending or explicitly use a non-PDF confirmed full-text source.
- Missing full text is listed under pending handling and blocks final synthesis/review.
- `process-log.md` is not created unless the user explicitly requested process visibility.
