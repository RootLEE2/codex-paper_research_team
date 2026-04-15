# Summary Validation Policy

Paper-note validation is required before final synthesis whenever notes were newly written or materially updated in the current session or cycle.

## Required Separation

- Paper Analyst writes or updates notes.
- Summary Validation Agent checks those notes against the source full text.
- Synthesis Agent uses only notes that passed validation or were repaired and revalidated.
- Professor Reviewer evaluates the final literature review after synthesis, not individual note extraction.

## Validation Scope

Check each note for:

- source availability: PDF, preprint, or confirmed full text exists
- bibliographic identity: title, authors, year, venue, DOI/URL
- factual fidelity: research question, method, participants/dataset, apparatus, measures, results, limitations, future work
- extraction depth: method, apparatus/system, task/procedure, conditions/baselines, participants/dataset, measures, analysis/statistics, and key findings are detailed enough for reuse when reported
- evidence discipline: no unsupported interpretations or cross-paper synthesis inside an individual paper note
- language policy: Korean explanatory prose; original titles, metadata, tags, technical terms, and concepts preserved

## Outcomes

- `pass`: note can be used for synthesis.
- `repair_required`: Paper Analyst must repair factual, missing-detail, or shallow-extraction issues and validation must rerun before synthesis.
- `blocked_missing_full_text`: move the item to pending handling; do not use the note for final synthesis.

Unresolved `repair_required` or `blocked_missing_full_text` items block final synthesis and professor review unless the user explicitly defers those papers.

## Thread Limit Handling

If the runtime cannot open another subagent because active agent threads are limited:

- close completed or obsolete subagents first
- batch multiple note checks into one Summary Validation Agent when papers are closely related
- run validation phase serially if needed
- record any inline fallback in the active session output; use `process-log.md` only when the user explicitly requested one for the session
