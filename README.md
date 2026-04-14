# Researches Workspace

이 workspace는 연구 프로젝트, 논문 PDF, Obsidian 논문 노트, literature review 결과물을 함께 관리하기 위한 공간입니다.

Codex 자동화 설정과 복구 절차는 [SETUP.md](SETUP.md)에 분리되어 있습니다.

## 목적

- 프로젝트별 연구 자료를 한 workspace에서 관리합니다.
- 논문 조사는 screening, Zotero 저장, PDF 확인, Obsidian note 작성, synthesis, professor review 순서로 진행합니다.
- 장기 재사용 가능한 논문 노트는 `papers/obsidian/notes/`에 유지합니다.
- 요청별 literature review 결과는 `literature-reviews/YYYY-MM-DD-<topic-slug>/`에 저장합니다.

## 주요 폴더

- `papers/zotero/`: Zotero 또는 ZotMoov가 관리하는 PDF, 사용자가 직접 제공한 PDF
- `papers/obsidian/notes/`: 재사용 가능한 논문 요약 노트
- `papers/obsidian/pending-notes/`: 사용자가 PDF를 추가해야 하는 pending 논문 목록
- `papers/state/`: 후보, screening, pending queue 등 기계가 읽는 상태 파일
- `literature-reviews/`: 주제별 조사 결과, synthesis, professor review
- `.agents/skills/paper-research-team/`: Codex가 논문 조사에 사용하는 project-local skill
- `AGENTS.md`: Codex가 이 workspace에서 따라야 하는 project instruction

## 기본 사용법

1. Zotero Desktop을 열어 둡니다.
2. Codex를 이 workspace root에서 실행합니다.
3. 논문 조사를 요청할 때는 `$paper-research-team`을 사용합니다.
4. Codex는 broad search 후 screening을 하고, selected `core` 및 approved `supporting` 논문만 Zotero에 저장합니다.
5. PDF 또는 full text가 없는 selected paper는 최종 synthesis/review 전에 멈추고 `papers/obsidian/pending-notes/`에 사용자 업로드 필요 목록만 남깁니다.
6. PDF가 모두 준비되면 Codex가 pending 논문 note를 작성하고, note validation, synthesis, professor review를 다시 진행합니다.

## 요청 예시

처음 실행할 때는 주제, 목적, 원하는 결과 위치를 같이 적는 것이 좋습니다.

```text
$paper-research-team으로 haptic feedback for collision avoidance in VR 관련 논문 조사를 진행해줘.
목표는 내 연구의 related work 정리야.
결과는 literature-reviews/YYYY-MM-DD-topic-slug/에 저장해줘.
Zotero에는 selected core/supporting paper만 저장하고, PDF가 없으면 pending 목록만 남겨줘.
```

screening 결과를 먼저 보고 싶다면 이렇게 요청합니다.

```text
$paper-research-team으로 위 주제를 조사하되, Zotero 저장 전에 screening 결과를 먼저 보여줘.
```

PDF를 추가한 뒤 이어서 처리할 때는 이렇게 요청합니다.

```text
pending PDF를 Zotero에 모두 추가했어.
$paper-research-team으로 pending 논문 note 작성, note validation, synthesis, professor review까지 이어서 진행해줘.
```

진행 과정을 별도 로그로 보고 싶을 때만 `process-log.md`를 요청합니다.

```text
이번 실행은 process-log.md도 남겨줘. 각 단계와 담당 agent를 같이 기록해줘.
```

## 결과 확인 순서

새 literature review folder가 만들어지면 보통 아래 순서로 확인하면 됩니다.

1. `research-brief.md`: 이번 조사 목표와 범위
2. `screening-results.md`: 검색 후보를 왜 선택/제외했는지
3. `selected-papers.md`: Zotero 저장 및 분석 대상 논문
4. `pending-pdfs.md`: 아직 PDF/full text가 없어 막힌 논문
5. `note-validation.md`: 작성된 Obsidian note가 원문과 맞는지 검증한 결과
6. `synthesis.md`: 논문들을 종합한 literature review
7. `professor-review.md`: synthesis에 대한 최종 품질 검토

`pending-pdfs.md`나 `papers/obsidian/pending-notes/`에 논문이 남아 있으면 최종 synthesis/review가 아직 완료되지 않은 상태일 수 있습니다.

## 필요한 프로그램

Codex가 파일과 설정은 도울 수 있지만, 아래 프로그램은 사용자가 직접 설치하고 로그인해야 합니다.

- **Zotero Desktop**: 논문 library, PDF 첨부, local API 연동에 필요합니다.
- **Obsidian**: 선택 사항으로, `papers/obsidian/` 아래의 노트와 인덱스를 사람이 읽고 편집할 때, 그리고 키워드 기반 논문 간 연결점을 파악할 때 사용합니다.
- **Codex CLI**: project-local skill과 MCP 서버를 사용해 자동화를 실행합니다.
- **브라우저 Zotero Connector**: 선택 사항이지만 논문 웹페이지에서 Zotero 저장을 보조할 수 있습니다.
- **ZotMoov 또는 ZotFile 계열 PDF 관리 도구**: 선택 사항입니다. Zotero PDF를 `papers/zotero/`에 정리하려면 사용합니다.

## 논문 처리 원칙

- 검색 후보를 전부 Zotero에 저장하지 않습니다. 먼저 screening하고 selected paper만 저장합니다.
- 이미 Zotero나 Obsidian note가 있는 핵심 논문은 중복 생성하지 않고 재사용합니다.
- PDF, preprint, confirmed full text가 없는 논문은 `papers/obsidian/notes/`에 일반 note를 만들지 않습니다.
- 개별 논문 note는 해당 논문 자체만 요약합니다. 현재 프로젝트에 대한 해석이나 종합은 synthesis에서 다룹니다.
- note 본문 설명은 한국어로 작성하고, title, authors, venue, DOI, tag, 기술 용어와 concept는 원문을 유지합니다.
- `#kw/*` keyword tag는 `papers/obsidian/_indexes/keyword-registry.md`에서 관리하고, 이 파일은 공개하지 않습니다.
- `process-log.md`는 기본 산출물이 아닙니다. 실행 추적이나 진행 과정 기록을 명시적으로 요청한 경우에만 만듭니다.

## 추천 운영 방식

- Zotero는 항상 먼저 열고 논문 조사를 시작하는 것이 좋습니다.
- pending list에는 "사용자가 어떤 PDF를 올려야 하는지"만 남겨 두는 것이 좋습니다.
- Literature review 결과를 읽을 때는 `research-brief.md`, `selected-papers.md`, `synthesis.md`, `professor-review.md` 순서로 보면 맥락을 덜 소모합니다.
- API key, Zotero key, OAuth token은 문서에 직접 쓰지 말고 Codex/MCP 설정의 secret/env 형태로 관리합니다.
- 새 환경으로 옮길 때는 [SETUP.md](SETUP.md)를 Codex에게 읽히고 설치/검증을 맡기는 것이 좋습니다.
