# Screening Rubric

## Goal

Select a compact, high-value set of papers from a broad candidate pool. The target is not maximum paper count. The target is coverage strong enough to pass professor review.

## Statuses

### core

Use for papers that should be saved to Zotero, prioritized for PDF acquisition, and analyzed in Obsidian.

A paper can be `core` if it satisfies at least one high-value role and is not redundant:

- It directly addresses the research question.
- It is a seminal or highly cited paper required to understand the field.
- It is recent SOTA from a strong venue.
- It provides a method, experiment design, or measurement approach likely to be reused.
- It is a strong evaluation precedent.

### supporting

Use for useful context papers that strengthen interpretation but are not central enough to drive the synthesis.

Examples:

- Background theory.
- Adjacent application.
- Comparative system.
- Review article useful for orientation.

### maybe

Use when the paper might be useful but evidence is insufficient. Do not save to Zotero unless later upgraded.

### pending_full_text

Use when the paper is important enough to analyze but no PDF is available. It should also keep its conceptual status, such as core or supporting, in `selected-papers.md`, `pending-papers.md`, and any unresolved record under `papers/obsidian/pending-notes/`.

### reject

Use when the paper is off-topic, redundant, low quality for the request, inaccessible without enough metadata, or only keyword-matched.

## Balanced Selection

Prefer a balanced core set:

- Directly relevant papers: central match to the user's topic.
- Seminal papers: older but foundational work that reviewers would expect.
- Recent SOTA: recent papers from the last 3-5 years, especially strong venues.
- Methodology papers: reusable methods, models, tasks, instruments, or analysis procedures.
- Experiment precedents: study designs, participant protocols, evaluation metrics, or apparatus choices.

Avoid a core set made only of recent keyword matches. Also avoid a core set made only of famous older papers.

## Venue Weight

Give extra weight to strong venues for the user's field and topic. When a local venue registry exists, use it as the preferred venue vocabulary. Do not hard-code a field-specific venue list into public outputs.

Venue quality is not enough by itself. A strong-venue paper still needs a clear role in the evidence map.

## PDF Availability

PDF availability should not determine intellectual relevance. However:

- A high-value paper without a PDF, preprint, or confirmed full text should be marked `pending_full_text`.
- Do not write a detailed Obsidian paper note without a PDF, preprint, or confirmed full text.
- Do not store PDF-missing papers under `papers/obsidian/notes/`.
- Required selected papers without full text block final synthesis and professor review.
- A non-final partial or abstract-level memo is allowed only when the user explicitly requests it.

## Redundancy

When multiple papers make the same contribution:

1. Prefer the paper with stronger direct relevance.
2. Prefer the paper with better venue or citation context.
3. Prefer the paper with clearer methods or evaluation.
4. Keep the other paper as supporting or reject with redundancy noted.

## Required Screening Output

For every screened paper, provide:

- status
- evidence role
- one-sentence reason
- PDF priority
- whether it should be saved to Zotero
