# Zotero, PDF Acquisition, and Paper Notes

## Phase 4: Zotero Save

The Library Manager saves only selected `core` papers and approved `supporting` papers. This Zotero save phase is required by default after screening; skip it only when the user explicitly asks not to write to Zotero.

Use Zotero root collection `papers`. Create or reuse a topic subcollection under `papers`. Assign items to both the root collection and topic subcollection when the API permits it.

Prefer `zotero-full` for write operations, DOI import, collection/tag management, PDF attachment, and open-access PDF cascade. Keep the older `zotero` MCP as a read-only fallback.

If a selected paper already exists in Zotero, reuse it instead of creating a duplicate. If an existing Obsidian note is available, record the note path for synthesis.

Do not leave `Zotero status: deferred` as the final state for selected papers unless the user explicitly requested no Zotero writes. An explicitly requested process log or visibility run still records the Zotero import step and its results.

For selected papers, Zotero storage has two parts:

- `zotero_item`: metadata, collections, and tags
- `pdf_attachment`: Zotero attachment for any available PDF file

If a selected paper has an available PDF in Zotero, `papers/zotero/`, an open-access download, or a user-provided file, attach it to the selected Zotero item. Do not report the paper as fully saved when a PDF is available but the Zotero item remains metadata-only. If the source is confirmed full text but not a PDF, record the non-PDF full-text source and mark `pdf_attachment` as not applicable rather than pending.

Add workflow and evidence role tags from the public tag registry. Read the local research profile, then add domain, method, venue, and reusable keyword tags from local taxonomy registries.

## Phase 5: PDF Acquisition

Try open-access and library-supported PDF acquisition. Attach any retrieved PDF to the corresponding selected Zotero item. Record:

- `pdf_available`
- `pdf_downloaded`
- `pdf_attached_to_zotero`
- `pdf_missing`
- `manual_needed`

If PDFs or confirmed full text are missing, write `pending-papers.md` with title, DOI, URL, venue, priority reason, and what the user should provide.

Use:

- `references/policies/pdf-gating.md`
- `references/policies/pending-papers.md`
- `references/schemas/pending-papers.md`
- `references/schemas/pending-record.md` when creating pending records

Codex does not run a periodic background Zotero/PDF watcher. On resume after user-provided PDFs, process newly available PDFs, attach them to Zotero items, move resolved pending records into full notes, update synthesis, and rerun professor review when unblocked.

## Phase 6: Paper Analysis

For every selected paper with a PDF, preprint, or confirmed full text, write a reusable Obsidian note using:

`papers/obsidian/_templates/paper-note-template.md`

Store normal notes under:

`papers/obsidian/notes/`

Before writing, apply `references/policies/pdf-gating.md`.

For extraction depth, apply `references/policies/paper-note-depth.md`.

For note language, apply `references/policies/note-language.md`.

Individual paper notes summarize the paper itself. Do not include sections about the user's current project or research.

If a selected paper already has an Obsidian note, reuse it instead of writing a duplicate. Update only missing metadata, tags, or index links when needed.

After writing or materially updating notes, dispatch a separate Summary Validation Agent before synthesis. Record results in `note-validation.md` in the session or cycle folder.
