# Paper Research Team Instructions

## Paper Research Requests

When the user asks to search papers, conduct a literature review, find related work, expand references or citations, manage papers in Zotero, download PDFs, summarize PDFs, write Obsidian paper notes, or run an iterative paper research pipeline, use the project-local skill:

`$paper-research-team`

The skill entry point is:

`.agents/skills/paper-research-team/SKILL.md`

Do not treat `papers/agents/` or any Markdown prompt folder as a Codex `/agent` registry. Specialist prompts are reference prompts loaded by the paper research skill and passed to subagents when useful.

## Paper Storage Policy

The `papers/` directory stores long-lived research assets:

- `papers/zotero/`: PDF files managed by Zotero/ZotMoov or user-provided PDFs.
- `papers/obsidian/`: reusable paper notes and indexes.
- `papers/state/`: machine-readable research state and queues.

Do not save every search candidate to Zotero. Search broadly, screen first, then save only selected `core` papers and approved `supporting` papers.

If a selected core paper already exists in Zotero or already has an Obsidian note, reuse it instead of creating a duplicate. Prefer newly discovered papers when quality is comparable, but include existing papers when they are seminal, central, or necessary for coverage.

## Literature Review Outputs

For a user-specified destination, write the literature review outputs there. Otherwise create:

`literature-reviews/YYYY-MM-DD-<topic-slug>/`

Use dated filenames and folders so multiple research requests remain distinguishable.
