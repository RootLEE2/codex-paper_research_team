---
name: paper-research-team
description: Use when the user asks to search academic papers, conduct a literature review, find related work, expand references or citations, use OpenAlex, Semantic Scholar, or Consensus, save papers to Zotero, download PDFs, summarize PDFs into Obsidian, manage paper tags, synthesize literature, request missing full text, or run an iterative professor-reviewed paper research pipeline.
metadata:
  short-description: Search, screen, save, analyze, and synthesize papers.
---

# Paper Research Team

Use this skill to run focused academic paper research from the `researches` project.

## Activation

On activation:

1. Read `config.yaml`.
2. Read `references/workflow.md`.
3. Read `references/source-priority.md` only when planning or changing search sources.
4. Read policy and schema subfiles only when the current phase needs them.
5. Start with the Research Orchestrator role.
6. Search broadly but do not save unscreened candidates to Zotero.
7. Save only `core` and approved `supporting` papers after screening.
8. Apply `references/policies/subagent-delegation.md` when coordinating separable phases.

## Default Workflow

1. Create a research brief from the user's request.
2. Search broadly using available academic tools.
3. Build an evidence map from candidate papers.
4. Screen candidates into `core`, `supporting`, `maybe`, `pending_full_text`, and `reject`.
5. Save selected `core` and approved `supporting` papers to the `papers` Zotero collection and the topic subcollection unless the user explicitly asks to skip Zotero writes.
6. Ask before saving only when the set contains non-selected candidates, `maybe` papers, or papers outside the screened scope.
7. Acquire PDFs when possible and attach every available PDF file to the corresponding selected Zotero item.
8. Put unavailable full text into a pending list and ask the user for it.
9. Write Obsidian notes only for papers with confirmed PDFs, preprints, or full text.
10. Reuse existing Zotero items and existing Obsidian notes for important core papers when available.
11. Expand through references, citations, and related works.
12. Validate generated paper notes against the source PDFs/full text with a separate Summary Validation Agent before synthesis.
13. If any required selected paper still lacks full text, stop before final synthesis and professor review.
14. Synthesize analyzed papers only after required PDFs/full text are available, paper-note validation has passed or been explicitly repaired, or the user explicitly narrows/defers the pending papers.
15. Run professor review as the final quality gate only after synthesis is unblocked.
16. If professor review finds important gaps or says the investigation is insufficient, restart a full research cycle from search/evidence mapping, not just a small patch, and repeat until professor review passes or the user stops the loop.

## Role Files

Use these prompts when delegating or simulating specialist work:

- `references/agents/research-orchestrator.md`
- `references/agents/search-strategist.md`
- `references/agents/evidence-mapping-agent.md`
- `references/agents/screening-agent.md`
- `references/agents/library-manager.md`
- `references/agents/pdf-acquisition-agent.md`
- `references/agents/paper-analyst.md`
- `references/agents/summary-validation-agent.md`
- `references/agents/citation-expansion-agent.md`
- `references/agents/synthesis-agent.md`
- `references/agents/professor-reviewer.md`

Codex does not require these files to be registered as `/agent` entries. They are prompt references loaded by this skill and sent to `spawn_agent` workers when parallel or isolated work is useful.

## Required References

- For phase order and stop rules, read `references/workflow.md`.
- For role boundaries, read `references/agent-roles.md`.
- For source priority, read `references/source-priority.md`.
- For reusable policies, read the needed file under `references/policies/`.
- For output formats, read `references/schemas.md`, then the needed file under `references/schemas/`.
- For paper selection, read `references/screening-rubric.md`.

## Core Rules

- Prefer high-quality coverage over raw paper count.
- Keep candidate discovery broad but Zotero storage selective.
- Prefer newly discovered papers, but reuse papers already in Zotero when they are genuinely core, seminal, or necessary for coverage.
- Do not treat a selected paper with an available PDF as complete in Zotero until the PDF is attached to or clearly linked from the Zotero item.
- Do not defer Zotero writes for a process-visibility run. Process visibility may be documented in requested session files while selected Zotero import still runs.
- Do not create `process-log.md` by default. Create it only when the user explicitly asks for a process log, first-run trace, or separate process-visibility artifact.
- Keep Professor Reviewer separate from Screening Agent.
- Use the public tag registry for pipeline tags. Read the local research profile before using local taxonomy registries for `#domain/*`, `#method/*`, `#venue/*`, or `#kw/*` tags.
- Individual paper notes must summarize the paper itself and must not include a section about the user's current research.
- Apply `references/policies/note-language.md` when writing or updating paper notes.
- Apply `references/policies/local-taxonomy-tags.md` before writing or updating domain, method, venue, or keyword tags in paper notes.
- Apply `references/policies/pdf-gating.md` before writing notes, synthesis, or professor review.
- Apply `references/policies/summary-validation.md` before synthesis whenever notes were newly written or materially updated.
- Apply `references/policies/pending-papers.md` when selected papers lack full text.
- Apply `references/policies/professor-review-loop.md` when Professor Reviewer asks for more work or says coverage is insufficient.
- Apply `references/policies/subagent-delegation.md` when splitting work across agents.
- Codex does not run a periodic background watcher by default. When the user later provides missing full text, resume the session, process any new PDFs, convert pending records into full paper notes, update synthesis, and rerun professor review.
