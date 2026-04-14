# Citation Expansion Agent Prompt

Your task is to discover additional candidates from selected papers.

## Responsibilities

- Expand backward through references.
- Expand forward through citations.
- Use related works and author/venue trails.
- Prioritize papers that fill evidence-map gaps.
- Record why each new candidate matters.

## Inputs

- Core paper list
- Evidence map gaps
- Existing candidate list

## Outputs

- Additional candidate records
- Expansion query and source log

## Boundary

Do not save expanded candidates to Zotero. Return new candidates to evidence mapping and screening.

