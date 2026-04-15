# Runtime Directories

Use this file to inspect the workspace and create runtime directories required by the paper research workflow.

## Expected Structure

```text
AGENTS.md
README.md
SETUP.md
.agents/skills/paper-research-team/SKILL.md
.agents/skills/paper-research-team/agents/openai.yaml
.agents/skills/paper-research-team/config.yaml
.agents/skills/paper-research-team/references/workflow.md
.agents/skills/paper-research-team/references/agent-roles.md
.agents/skills/paper-research-team/references/schemas.md
.agents/skills/paper-research-team/references/screening-rubric.md
.agents/skills/paper-research-team/references/agents/*.md
.agents/skills/paper-research-team/references/policies/*.md
.agents/skills/paper-research-team/references/workflows/*.md
.agents/skills/paper-research-team/references/schemas/*.md
papers/zotero/
papers/obsidian/notes/
papers/obsidian/pending-notes/
papers/obsidian/_templates/paper-note-template.md
papers/obsidian/_indexes/tag-registry.md
papers/obsidian/_indexes/research-profile.example.md
papers/obsidian/_indexes/research-profile.md
papers/obsidian/_indexes/domain-registry.md
papers/obsidian/_indexes/method-registry.md
papers/obsidian/_indexes/venue-registry.md
papers/obsidian/_indexes/keyword-registry.md
literature-reviews/
```

If instruction files are missing and the user provided equivalents, create them in the target structure. If only a subset is available, create runtime directories and report which instruction files are missing.

## Inspect Current State

Run:

```bash
pwd
find . -maxdepth 3 -name AGENTS.md -o -path './.agents/skills/*/SKILL.md' -o -path './papers/obsidian/_templates/*' -o -path './papers/obsidian/_indexes/*'
codex mcp list
```

Determine:

- Workspace root path.
- Whether `.agents/skills/paper-research-team` exists.
- Whether root `AGENTS.md` routes paper research requests to `$paper-research-team`.
- Whether Obsidian templates and indexes exist.
- Which MCP servers are registered.

## Create Runtime Directories

Run:

```bash
mkdir -p papers/zotero
mkdir -p papers/obsidian/notes
mkdir -p papers/obsidian/pending-notes
mkdir -p papers/obsidian/syntheses
mkdir -p papers/obsidian/reviews
mkdir -p papers/state/sessions
mkdir -p papers/state/candidates
mkdir -p papers/state/screened
mkdir -p papers/state/pending_full_text
mkdir -p literature-reviews
mkdir -p .agents/skills/paper-research-team/agents
mkdir -p .agents/skills/paper-research-team/references/agents
mkdir -p .agents/skills/paper-research-team/references/policies
mkdir -p .agents/skills/paper-research-team/references/schemas
mkdir -p .agents/skills/paper-research-team/references/workflows
```
