# Paper Research Skill

Use this file to restore or verify the project-local `$paper-research-team` skill.

## Root Router

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

## Skill Entrypoint

Ensure `.agents/skills/paper-research-team/SKILL.md` exists with frontmatter similar to:

```yaml
---
name: paper-research-team
description: Use when the user asks to search academic papers, conduct a literature review, find related work, expand references or citations, use OpenAlex, Semantic Scholar, or Consensus, save papers to Zotero, download PDFs, summarize PDFs into Obsidian, manage paper tags, synthesize literature, request missing full text, or run an iterative professor-reviewed paper research pipeline.
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
- Reuse existing Zotero items, PDF attachments, and Obsidian notes for selected core/supporting papers when appropriate.
- Treat a selected paper with an available PDF as incomplete until the PDF attachment is attached to or clearly linked from its Zotero item.
- Stop before final synthesis/review if required selected full text is missing.
- Resume pending papers after the user reports PDFs were added.
- Avoid default `process-log.md` creation.

## Runtime Config

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
  attach_available_pdfs_to_selected_items: true
  selected_with_available_pdf_must_not_remain_metadata_only: true
  do_not_defer_selected_import_for_process_visibility_runs: true
  save_statuses:
    - "core"
    - "supporting"

pdf:
  analyze_only_when_full_text_available: true
  attach_available_pdfs_to_zotero_items: true
  available_pdf_requires_zotero_attachment: true
  continue_when_full_text_missing: false
  continue_search_and_screening_when_full_text_missing: true
  block_synthesis_and_review_when_required_full_text_missing: true

obsidian:
  language: "ko"
  note_body_language: "ko"
  preserve_original_titles_terms_tags: true
  preserve_technical_terms_and_concepts: true
  paper_notes_are_deep_extraction_notes: true
  metadata_level_notes_forbidden_under_notes: true
  pending_notes_dir: "papers/obsidian/pending-notes"
  research_profile: "papers/obsidian/_indexes/research-profile.md"
  research_profile_example: "papers/obsidian/_indexes/research-profile.example.md"
  read_research_profile_before_taxonomy_registries: true
  domain_registry: "papers/obsidian/_indexes/domain-registry.md"
  method_registry: "papers/obsidian/_indexes/method-registry.md"
  venue_registry: "papers/obsidian/_indexes/venue-registry.md"
  keyword_registry: "papers/obsidian/_indexes/keyword-registry.md"
  local_taxonomy_registries_are_local_only: true
  auto_create_local_taxonomy_registries: true
  normal_notes_require_full_text: true

note_validation:
  required_before_synthesis: true
  use_separate_agent: true
  validate_extraction_depth: true
  shallow_notes_fail_validation: true
  metadata_level_notes_block_synthesis: true

review_loop:
  restart_full_cycle_when_review_says_insufficient: true
  repeat_until_professor_review_passes_or_user_stops: true
```

Search sources should include OpenAlex, Semantic Scholar, Consensus, and Zotero reuse.

## Python Fallback Environment

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
