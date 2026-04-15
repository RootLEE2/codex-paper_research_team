# Pending Paper Lifecycle

Use this when selected papers lack PDFs, preprints, or confirmed full text.

## Records

Maintain:

- session-level `pending-papers.md`
- `papers/obsidian/pending-notes/` records only for papers that still require user-provided full text

Do not create normal notes under `papers/obsidian/notes/` for pending papers.

## Required Fields

Track:

- title
- DOI or URL
- venue/year when known
- conceptual status, such as `core` or `supporting`
- why the paper is needed
- what full text is missing
- resume instructions

## Resume

When the user reports that PDFs were added:

1. Search `papers/zotero/` and Zotero attachments again.
2. Convert resolved pending records into normal notes only after full text is confirmed.
3. Remove resolved papers from `papers/obsidian/pending-notes/`, then update `pending-papers.md`, `selected-papers.md`, and candidate PDF status.
4. Continue synthesis and professor review only after required pending items are resolved or explicitly deferred.
