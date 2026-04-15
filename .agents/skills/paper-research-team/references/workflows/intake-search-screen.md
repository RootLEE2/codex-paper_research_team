# Intake, Search, Evidence Mapping, and Screening

## Phase 0: Intake

Create a session directory. If the user names an output folder, use it. Otherwise use:

`literature-reviews/YYYY-MM-DD-<topic-slug>/`

Write `research-brief.md` with user request, scope, constraints, venues/fields, inclusion/exclusion criteria, and output expectations.

If ambiguity changes search direction, ask one concise clarification. Otherwise proceed with documented assumptions.

## Phase 1: Broad Search

Use `references/source-priority.md`.

Search broadly and save candidate metadata to `candidate-papers.json`. Do not save candidates to Zotero in this phase.

When a candidate appears to already exist in Zotero, keep it in the candidate set and mark it as existing. Existing Zotero presence is not a rejection reason.

Capture title, authors, year, venue, DOI/URL, abstract, citation count when available, source database, search query, reason found, Zotero existence, Zotero key, and existing Obsidian note path when known.

Use `references/schemas/candidate-paper-json.md` for structure.

## Phase 2: Evidence Mapping

Classify candidates into evidence roles:

- `directly_relevant`
- `seminal`
- `recent_sota`
- `methodology`
- `evaluation_precedent`
- `application_context`
- `theoretical_background`
- `adjacent_useful`

Write `evidence-map.md` with coverage, gaps, duplicates, and candidate clusters.

Use `references/schemas/evidence-map.md`.

## Phase 3: Screening

Use `references/screening-rubric.md`.

Assign each candidate one status:

- `core`
- `supporting`
- `maybe`
- `pending_full_text`
- `reject`

Write `screening-results.md` and `selected-papers.md`.

Use:

- `references/schemas/screening-results.md`
- `references/schemas/selected-papers.md`

Ask before saving a large or uncertain selected set. If the selected set is small and clearly aligned, proceed and document the assumption.
