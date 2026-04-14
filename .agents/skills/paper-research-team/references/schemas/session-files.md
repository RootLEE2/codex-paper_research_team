# Session Files

Default session path:

`literature-reviews/YYYY-MM-DD-<topic-slug>/`

Always required files:

- `research-brief.md`
- `candidate-papers.json`
- `evidence-map.md`
- `screening-results.md`
- `selected-papers.md`
- `pending-pdfs.md`

Conditionally required files:

- `synthesis.md` only after required selected papers have PDFs, preprints, or confirmed full text, or after the user explicitly narrows/defers pending papers.
- `note-validation.md` when paper notes were newly written or materially updated in the session/cycle.
- `professor-review.md` only after unblocked synthesis, or as a blocked placeholder when required selected papers lack full text.
- `process-log.md` only when the user explicitly asks for a process log, first-run trace, or process-visibility artifact. It is not a default session file.

Detailed schemas:

- `references/schemas/candidate-paper-json.md`
- `references/schemas/evidence-map.md`
- `references/schemas/screening-results.md`
- `references/schemas/selected-papers.md`
- `references/schemas/pending-pdfs.md`
- `references/schemas/pending-record.md`
- `references/schemas/note-validation.md`
- `references/schemas/blocked-outputs.md`
