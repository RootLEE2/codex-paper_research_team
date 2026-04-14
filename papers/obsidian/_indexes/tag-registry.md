# Tag Registry

Use this registry before adding non-keyword tags to paper notes. Prefer existing tags.

Keyword tags are managed separately in `papers/obsidian/_indexes/keyword-registry.md`. That file is local-only and should be ignored by Git because it can reveal active research interests.

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

## Domain

- #domain/hci
- #domain/haptics
- #domain/tactile-interface
- #domain/wearable-haptics
- #domain/vibrotactile
- #domain/vr
- #domain/ar
- #domain/assistive-technology
- #domain/robotics
- #domain/multimodal-interaction
- #domain/multimedia
- #domain/human-factors

## Method

- #method/user-study
- #method/controlled-experiment
- #method/psychophysics
- #method/system-review
- #method/literature-review
- #method/prototype
- #method/computational-model
- #method/dataset-analysis
- #method/field-study
- #method/interview
- #method/survey

## Venue

- #venue/chi
- #venue/uist
- #venue/ieee-toh
- #venue/ieee-haptics-symposium
- #venue/ieee-whc
- #venue/eurohaptics
- #venue/ieee-vr
- #venue/ismar
- #venue/vrst
- #venue/dis
- #venue/imwut
- #venue/icra
- #venue/iros
- #venue/acm-multimedia
- #venue/ieee-tmm
- #venue/siggraph

## Keyword Tags

- Read `keyword-registry.md` before adding or reusing `#kw/*` tags.
- If `keyword-registry.md` does not exist, create it locally.
- Use lowercase kebab-case after `#kw/`.
- Prefer singular concepts unless the field convention is plural.
- Promote a keyword to `#kw/*` only when it is reusable across multiple papers or likely to support later graph navigation.
- Keep exact author keywords in the note frontmatter `keywords:` even when they are not promoted to tags.
- When adding a new reusable keyword tag, add it to `keyword-registry.md` before using it in paper notes.
