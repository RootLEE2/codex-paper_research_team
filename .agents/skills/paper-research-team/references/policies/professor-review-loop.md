# Professor Review Loop Policy

Professor Reviewer is the quality gate for the research cycle.

## If Review Finds Coverage Gaps

If Professor Reviewer says the investigation, coverage, evidence map, or novelty claim is insufficient:

- do not stop after a small patch unless the review explicitly asks for a bounded patch
- start a new full research cycle from broad search and evidence mapping
- include the reviewer's gap list as the next cycle's research brief
- rerun screening, PDF acquisition, paper analysis, paper-note validation, synthesis, and professor review
- repeat until Professor Reviewer passes or the user stops the loop

The next cycle can be focused by the reviewer's critique, but it must still pass through the full phase order:

`search -> evidence map -> screening -> PDF/full-text gate -> notes -> note validation -> synthesis -> professor review`

## If Review Is Blocked By PDFs

Missing PDFs are not a review failure. They are a PDF gate.

When required selected papers lack PDF, preprint, or confirmed full text:

- stop before final synthesis and professor review
- record only user-upload-needed papers in `papers/obsidian/pending-notes/pending-papers.md`
- keep broader candidate and triage details in the session folder, not in `pending-notes`
- resume after the PDFs are available or after the user explicitly defers those papers

## Stop Condition

The research request is done only when:

- required selected papers have full text or are explicitly deferred
- paper notes created or materially updated in the cycle have passed validation or been repaired and revalidated
- synthesis has been rerun from the analyzed papers
- Professor Reviewer passes without requiring another cycle
