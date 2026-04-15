# PDF and Full-Text Gating Policy

Normal Obsidian notes require one of:

- PDF
- preprint
- confirmed full text

For selected papers with an available PDF file, attach the PDF to the corresponding Zotero item before treating Zotero storage as complete.

If a selected paper has confirmed full text but no PDF file, it can proceed to note writing only when the full-text source is recorded. In that case, mark Zotero PDF attachment as not applicable rather than pending.

If a selected paper lacks full text:

- do not create a normal note under `papers/obsidian/notes/`
- add it to `pending-papers.md`
- create a concise pending record under `papers/obsidian/pending-notes/` only when the user still needs to provide full text
- keep its conceptual role, such as `core` or `supporting`, in selected/pending records

If any required selected paper remains pending:

- stop before final synthesis
- do not run final professor review
- write blocked placeholders only when a session output file is useful

Resume only after:

- the missing full text is available, or
- the user explicitly narrows the scope or defers the pending paper

After full text is resolved, remove the paper from `papers/obsidian/pending-notes/` or leave only the active unresolved upload-needed list.
