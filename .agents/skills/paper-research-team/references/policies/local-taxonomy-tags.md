# Local Taxonomy Tag Policy

Use `papers/obsidian/_indexes/tag-registry.md` only for public pipeline tags such as workflow and evidence role.

Use local-only registries for research-taxonomy tags:

- `papers/obsidian/_indexes/research-profile.md` as the user's local seed profile
- `papers/obsidian/_indexes/domain-registry.md` for `#domain/*`
- `papers/obsidian/_indexes/method-registry.md` for `#method/*`
- `papers/obsidian/_indexes/venue-registry.md` for `#venue/*`
- `papers/obsidian/_indexes/keyword-registry.md` for `#kw/*`

These local files should be ignored by Git because they can reveal active research interests, methods, venues, and field focus.

## Rules

- Read `research-profile.md` before creating or updating taxonomy registries.
- If `research-profile.md` is missing and `research-profile.example.md` exists, tell the user to copy it to `research-profile.md` and fill in their domains, methods, venues, and keyword seeds.
- Use `research-profile.md` to initialize missing local taxonomy registries.
- Read the matching local registry before adding or reusing a taxonomy tag.
- If a local registry does not exist, create it locally.
- Use lowercase kebab-case after the namespace prefix.
- Add a new taxonomy tag only when it is reusable across multiple papers or useful for later graph navigation.
- Do not promote a phrase to `#kw/*` when it is useful for only one paper.
- Keep exact author keywords in the paper note frontmatter `keywords:` when they are not promoted to reusable `#kw/*` tags.
- Add a new reusable taxonomy tag to the matching local registry before using it in paper note `tags:`.
