# Obsidian and Zotero Setup

Use this file to verify Obsidian note behavior, Zotero storage behavior, and PDF/full-text handling.

## Obsidian Files

Ensure `papers/obsidian/_templates/paper-note-template.md` summarizes only the paper itself. It must not include a section about the user's current research.

Required reusable note behavior:

- Explanatory body content in Korean.
- Original titles, authors, venues, DOI/URL, tags, technical terms, and concepts preserved.
- Normal notes only under `papers/obsidian/notes/`.
- Missing-full-text metadata or upload-needed records only under `papers/obsidian/pending-notes/`.
- Available PDF files must be attached to the corresponding selected Zotero item. A non-pending selected paper with PDF availability should not remain metadata-only in Zotero.
- Workflow and evidence tags come from `papers/obsidian/_indexes/tag-registry.md`.
- Domain, method, venue, and keyword tags come from `research-profile.md` and local taxonomy registries.
- `research-profile.md`, `domain-registry.md`, `method-registry.md`, `venue-registry.md`, and `keyword-registry.md` are local-only and should be ignored by Git.

Ensure `papers/obsidian/_indexes/tag-registry.md` contains controlled public tags for workflow and evidence role only. Keep actual reusable `#domain/*`, `#method/*`, `#venue/*`, and `#kw/*` tags in local taxonomy registries.

## Local Research Profile And Taxonomy Bootstrap

Initialize `research-profile.md` and local taxonomy registries during setup, before a real paper-research run. Detailed instructions are in [local-taxonomy.md](local-taxonomy.md).

## Zotero Desktop Check

Before running a real paper pipeline:

- Ask the user to open Zotero Desktop.
- Confirm Zotero local API/connector communication is enabled.
- Keep Zotero running during save/PDF operations.

If Zotero write/PDF operations fail, first check whether Zotero Desktop is open. If local MCP remains unavailable, fall back to Zotero Web API only when credentials are configured.

## Paper Storage Principles

- Search broadly, screen first, and save only selected `core` and approved `supporting` papers.
- Reuse existing Zotero items and existing Obsidian notes when they are genuinely core, seminal, or necessary for coverage.
- If a selected paper has an available PDF, attach the PDF to the corresponding Zotero item before treating storage as complete.
- If a selected paper has confirmed full text but no PDF, record the full-text source and mark PDF attachment as not applicable rather than pending.
- If selected full text is missing, keep the paper in pending handling and do not create a normal note under `papers/obsidian/notes/`.
- Do not run final synthesis or professor review while required selected full text is unresolved unless the user explicitly narrows or defers that paper.
