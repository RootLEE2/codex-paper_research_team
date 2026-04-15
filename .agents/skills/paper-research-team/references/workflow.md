# Paper Research Workflow

This file is an index. Load only the detailed workflow file needed for the current phase.

## Phase Order

0. Intake
1. Broad search
2. Evidence mapping
3. Screening
4. Zotero save
5. PDF acquisition
6. Paper analysis
7. Citation expansion
8. Summary validation
9. Synthesis
10. Professor review

## Detailed Workflow Files

- Phases 0-3: `references/workflows/intake-search-screen.md`
- Phases 4-6: `references/workflows/zotero-pdf-notes.md`
- Phases 7-9: `references/workflows/expansion-synthesis-review.md`

## Always Apply

- Source order: `references/source-priority.md`
- Subagent policy: `references/policies/subagent-delegation.md`
- PDF/full-text gating: `references/policies/pdf-gating.md` before notes, synthesis, or review
- Summary validation: `references/policies/summary-validation.md` before synthesis when notes were created or materially updated
- Pending paper lifecycle: `references/policies/pending-papers.md` when selected papers lack full text
- Professor-review loop: `references/policies/professor-review-loop.md` when review says coverage is insufficient
- Output schemas: `references/schemas.md`, then the specific schema file

## Stop Rule

If any required selected paper still lacks a PDF, preprint, or confirmed full text:

- continue only search, screening, PDF acquisition, resolved-paper note writing, and pending-list maintenance
- do not write final synthesis
- do not run final professor review
- use blocked placeholders only when useful for the session output

If Professor Reviewer says the investigation is insufficient for reasons other than missing full text:

- restart from broad search and evidence mapping using the review critique as the next-cycle brief
- rerun screening, PDF acquisition, notes, note validation, synthesis, and review
- repeat until Professor Reviewer passes or the user stops the loop
