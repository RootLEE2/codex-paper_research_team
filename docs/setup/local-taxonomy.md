# Local Taxonomy Setup

Use this file to initialize research-specific tags before a real paper-research run.

## Research Profile

Treat `research-profile.md` as part of setup, not as a post-setup task. It is the local input for reusable domain, method, venue, and keyword tags.

Ensure `papers/obsidian/_indexes/research-profile.example.md` exists. If `research-profile.md` is missing, copy the example file:

```bash
cp papers/obsidian/_indexes/research-profile.example.md papers/obsidian/_indexes/research-profile.md
```

Then fill in:

- domain seeds for `#domain/*`
- method seeds for `#method/*`
- venue seeds for `#venue/*`
- keyword seeds for `#kw/*`

## Registry Files

After `research-profile.md` is filled, create or update these local-only registry files from that profile:

- `papers/obsidian/_indexes/domain-registry.md`
- `papers/obsidian/_indexes/method-registry.md`
- `papers/obsidian/_indexes/venue-registry.md`
- `papers/obsidian/_indexes/keyword-registry.md`

These registry files should contain reusable tags, aliases, and brief usage notes. Do not create one-off tags just because a single paper uses a phrase.

Keep `papers/obsidian/_indexes/tag-registry.md` public and workflow-oriented. Keep research-specific taxonomy in the local registries.

## Git Policy

`research-profile.md` and local registry files can contain personal research interests and should stay out of Git.
