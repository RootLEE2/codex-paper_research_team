# Paper Note Schema

Use for reusable notes under `papers/obsidian/notes/`.

The section headings remain template-controlled. With the current template, headings are English and body content is Korean.

Reusable notes must follow `references/policies/paper-note-depth.md`. They are source-grounded extraction notes, not abstract summaries. Quality is measured by concrete explanatory detail, not by the number of headings. For empirical or system papers, include enough system, method, task, condition, participant/dataset, measure, analysis, result, limitation, and future-work detail to support synthesis without reopening the PDF for basic facts.

Use `papers/obsidian/_indexes/tag-registry.md` for workflow and evidence tags. Read `papers/obsidian/_indexes/research-profile.md` when available, then use local taxonomy registries for `#domain/*`, `#method/*`, `#venue/*`, and `#kw/*` tags. Keep exact author keywords in `keywords:` when they are not promoted to reusable tags.

```markdown
---
title: "<original paper title>"
authors:
  - "<original author name>"
year: 2026
venue: "<original venue name>"
doi: "10.xxxx/yyyy"
zotero_key: ""
pdf_status: "pdf_available"
status: "core"
language: "ko"
body_language: "ko"
term_policy: "preserve_original_terms"
evidence_roles:
  - "directly_relevant"
keywords:
  - "<original or field-standard term>"
tags:
  - "#paper/core"
---

# Paper Summary

## Research Question

한국어 본문. 원문 technical term은 그대로 유지한다.

## Motivation

## Method

## Experiment Design

## Participants / Dataset

## Measures

## Key Findings

## Limitations

## Future Research Suggested By The Limitations

## Important Terms

## Notes
```
