# Paper Note Depth Policy

Use this before writing, updating, validating, or repairing reusable paper notes under `papers/obsidian/notes/`.

Reusable paper notes are source-grounded extraction notes, not abstract summaries. They should let the user reuse the paper's method, experimental design, measures, and findings without reopening the PDF for basic details.

Depth means concrete explanation, not more headings. Do not satisfy this policy by adding empty or one-line subsections. Use paragraphs or compact bullets that preserve the paper's actual design, evidence, numbers, and reasoning.

## Source Requirement

- Read the PDF, preprint, or confirmed full text before writing a normal note.
- Do not create a normal note from metadata, abstract, or local memory alone.
- If full text was not reviewed, do not write under `papers/obsidian/notes/`; create or update pending handling instead.
- If an existing note says `metadata-level`, `full text was not reviewed`, or equivalent, treat it as `repair_required` or `blocked_missing_full_text` during validation.

## Minimum Extraction

For empirical or system papers, extract the following when reported:

- Research question or hypothesis, including the tested scope.
- Motivation and explicit gap in prior work.
- System, apparatus, sensing/input, feedback/output, algorithm, or model details.
- Experimental tasks, environment, procedure, training, trial structure, and duration.
- Conditions, baselines, comparison groups, randomization, and counterbalancing.
- Participants, recruitment, inclusion criteria, demographics, expertise, or dataset source and size.
- Measures, dependent variables, questionnaires, coding schemes, and statistical tests.
- Key findings by measure or condition, including concrete numbers, directions of effect, and significance when reported.
- Authors' limitations plus additional validity threats that follow directly from the design.
- Future work suggested by the paper's limitations.
- Important terms with paper-specific definitions.

For review, survey, theory, or position papers, adapt the same depth target:

- Scope and inclusion/exclusion criteria.
- Corpus size, search strategy, databases, years, and coding dimensions when reported.
- Taxonomy, framework, categories, or argument structure.
- Main claims and what evidence supports each claim.
- Gaps, limitations, and concrete implications for future work.

## Depth Bar

- Avoid one-sentence sections except when the source truly provides no more detail.
- Prefer fewer well-explained sections over many shallow headings.
- Optional subheadings are allowed for multi-study or complex papers, but each subheading must add substantive detail.
- Do not write `not verified`, `not available`, or `not reported` unless the full text was checked for that item.
- When a paper reports numbers, conditions, or participant counts, include them.
- When a paper has multiple studies or experiments, summarize each study separately enough to distinguish tasks, participants or datasets, measures, and findings.
- Keep current-project interpretation out of individual paper notes. Put cross-paper interpretation in synthesis.

## Validation Failures

Mark a note `repair_required` when:

- Any reported method, apparatus, condition, participant/dataset, measure, or result needed for reuse is missing.
- Key findings are only high-level claims without the evidence or measures that support them.
- The note uses metadata-level language despite a full text being available.
- The note lacks enough detail to support synthesis without reopening the source for basic experimental facts.

Mark a note `blocked_missing_full_text` when no PDF, preprint, or confirmed full text was checked.
