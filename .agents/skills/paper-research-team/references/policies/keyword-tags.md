# Keyword Tag Policy

Use `papers/obsidian/_indexes/tag-registry.md` for public non-keyword tags such as workflow, evidence role, domain, method, and venue.

Use `papers/obsidian/_indexes/keyword-registry.md` for `#kw/*` tags. The keyword registry is local-only and should be ignored by Git because it can reveal active research interests.

## Rules

- Read `keyword-registry.md` before adding or reusing a `#kw/*` tag.
- If `keyword-registry.md` does not exist, create it locally.
- Use lowercase kebab-case after `#kw/`.
- Add a new `#kw/*` tag only when the keyword is reusable across multiple papers or likely to support later graph navigation.
- Do not promote a phrase to `#kw/*` when it is useful for only one paper.
- Keep exact author keywords in the paper note frontmatter `keywords:` when they are not promoted to tags.
- Add a new reusable keyword tag to `keyword-registry.md` before using it in paper note `tags:`.
