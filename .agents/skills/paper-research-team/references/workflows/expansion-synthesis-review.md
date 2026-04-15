# Citation Expansion, Summary Validation, Synthesis, and Professor Review

## Phase 7: Citation Expansion

Use core papers to expand through:

- backward references
- forward citations
- related works
- key authors
- venue trails

New candidates return to evidence mapping and screening before Zotero storage. Do not bypass screening.

## Phase 8: Summary Validation

Before writing synthesis, apply `references/policies/summary-validation.md` when any selected paper note was newly written or materially updated.

The Summary Validation Agent checks each note against its PDF, preprint, or confirmed full text. Record findings in `note-validation.md` in the session or cycle folder.

If validation finds factual errors, unsupported claims, missing critical methods/results, or citation mismatches, repair the paper notes and rerun validation before synthesis.

## Phase 9: Synthesis

Before writing synthesis, apply `references/policies/pdf-gating.md` and confirm paper-note validation is passed or not needed because all reused notes were already accepted for this session.

Write `synthesis.md` only when required selected papers have available full text, or when the user explicitly narrows the scope to exclude/defer pending papers.

If required selected papers remain pending, use `references/schemas/blocked-outputs.md` for a blocked placeholder instead of synthesis.

Do not write partial synthesis by default. A partial synthesis is allowed only when the user explicitly asks for a partial or abstract-level interim memo, and it must be labeled non-final.

The synthesis should cover research landscape, clusters, methods, experiment patterns, robust findings, disagreements, gaps, claim-paper anchors, and pending evidence limits.

## Phase 10: Professor Review

Run Professor Reviewer only after unblocked synthesis.

If required selected papers remain pending, do not run professor review. Write a blocked placeholder or stop with the pending list. A professor review of partial or abstract-level synthesis is allowed only when the user explicitly asks for it and must be labeled non-final.

Use `references/schemas/blocked-outputs.md` when review is blocked.

If review fails because coverage, evidence, novelty checking, or synthesis quality is insufficient, start another full research cycle using the reviewer's critique as the next-cycle brief. Do not stop after only a citation-expansion patch unless the review explicitly asks for a bounded patch.

The repeated cycle still follows:

`search -> evidence mapping -> screening -> PDF/full-text gate -> notes -> note validation -> synthesis -> professor review`

Repeat until Professor Reviewer passes or the user stops the loop.

If the issue is missing full text for required selected papers, this is a full-text gate rather than a review failure. Stop before final synthesis/review, record only user-upload-needed papers in `papers/obsidian/pending-notes/pending-papers.md`, and resume after the full text is available or explicitly deferred.
