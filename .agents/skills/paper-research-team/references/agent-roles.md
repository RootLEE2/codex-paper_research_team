# Agent Roles

This file is an index. Load only the role prompt needed for the current phase.

## Role Prompt Files

- Research Orchestrator: `references/agents/research-orchestrator.md`
- Search Strategist: `references/agents/search-strategist.md`
- Evidence Mapping Agent: `references/agents/evidence-mapping-agent.md`
- Screening Agent: `references/agents/screening-agent.md`
- Library Manager: `references/agents/library-manager.md`
- PDF Acquisition Agent: `references/agents/pdf-acquisition-agent.md`
- Paper Analyst: `references/agents/paper-analyst.md`
- Summary Validation Agent: `references/agents/summary-validation-agent.md`
- Citation Expansion Agent: `references/agents/citation-expansion-agent.md`
- Synthesis Agent: `references/agents/synthesis-agent.md`
- Professor Reviewer: `references/agents/professor-reviewer.md`

## Separation Rules

- Keep Professor Reviewer separate from Screening Agent.
- Keep candidate search separate from Zotero save decisions.
- Keep PDF acquisition separate from paper analysis.
- Keep paper-note writing separate from paper-note validation.
- Keep final synthesis separate from professor review.
- Use actual subagents when runtime support is available; see `references/policies/subagent-delegation.md`.

## Gating Rules

Before writing notes, synthesis, or professor review, load:

- `references/policies/note-language.md` when writing or updating notes
- `references/policies/pdf-gating.md`
- `references/policies/summary-validation.md` when validating newly written or materially updated notes before synthesis
- `references/policies/pending-papers.md` when selected papers are missing full text

Before writing session files, load:

- `references/schemas.md`
- the specific schema file under `references/schemas/` for the current output
