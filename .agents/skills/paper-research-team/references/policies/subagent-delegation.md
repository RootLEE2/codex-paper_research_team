# Subagent Delegation Policy

Use actual subagents for separable paper-research phases when the runtime supports it.

Good subagent boundaries:

- broad search by query family
- evidence mapping from an existing candidate set
- screening with a fixed rubric
- PDF availability checks for selected papers
- paper-note writing for disjoint PDFs
- verification/audit of generated outputs

Keep inline only when:

- no subagent tool is available
- the user explicitly forbids delegation
- the next step is a small blocking decision that would be slower to delegate

Record which agent handled each phase in the active session output or final report when process visibility is requested. Do not create `process-log.md` by default; create it only when the user explicitly asks for a process log, first-run trace, or separate process-visibility artifact.
