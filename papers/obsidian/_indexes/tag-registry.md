# Tag Registry

Use this registry before adding pipeline-level tags to paper notes. Prefer existing tags.

Research-taxonomy tags are managed separately in local-only registries because they vary by person, field, and project:

- `research-profile.md`: local seed profile for the user's domains, methods, venues, and keyword seeds
- `domain-registry.md`: `#domain/*`
- `method-registry.md`: `#method/*`
- `venue-registry.md`: `#venue/*`
- `keyword-registry.md`: `#kw/*`

These local registry files should be ignored by Git because they can reveal active research interests.

## Workflow

- #paper/core
- #paper/supporting
- #paper/pending-pdf
- #paper/screened
- #paper/rejected
- #paper/summarized
- #paper/reviewed

## Evidence Role

- #evidence/directly-relevant
- #evidence/seminal
- #evidence/recent-sota
- #evidence/methodology
- #evidence/evaluation-precedent
- #evidence/application-context
- #evidence/theoretical-background
- #evidence/adjacent-useful

## Local Taxonomy Rules

- Copy `research-profile.example.md` to `research-profile.md` and fill it in before the first paper-research run.
- Read `research-profile.md` before creating or updating local taxonomy registries.
- Read the matching local registry before adding or reusing `#domain/*`, `#method/*`, `#venue/*`, or `#kw/*` tags.
- If a local registry does not exist, create it locally.
- Use lowercase kebab-case after the namespace prefix.
- Add new taxonomy tags only when they are reusable across multiple papers or useful for later graph navigation.
- Keep exact author keywords in note frontmatter `keywords:` when they are not promoted to reusable `#kw/*` tags.
