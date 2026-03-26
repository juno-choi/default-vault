# bdacs

Claude Code 기반 업무 자동화 Obsidian Vault

## 폴더 구조

```text
bdacs/
├── .claude/            # Claude 설정 및 skill
│   └── commands/vault/  # vault: namespace skill 모음
├── template/           # 자동 생성용 파일 템플릿
├── workspace/
│   ├── 1_daily/        # 일일 할일 + AI 대화 기록
│   ├── 2_weekly/       # 주간 회고
│   ├── 3_projects/     # 진행 중 프로젝트
│   ├── 4_done/         # 완료된 프로젝트 보관
│   ├── 5_reference/    # 참고 자료
│   └── 6_etcs/         # 기타 파일
├── CLAUDE.md           # Claude 프로젝트 지시사항
├── STRUCTURE.md        # 상세 폴더 구조 및 규칙 정의
└── README.md
```

## 폴더별 설명

| 폴더            | 설명                                                     |
| ------------- | ------------------------------------------------------ |
| `1_daily`     | 매일 `{yyyy-MM}/{yyyy-MM-dd}/` 하위에 todo.md, prompt.md 생성 |
| `2_weekly`    | `{yyyy}/W{nn}_review.md` 형식으로 주간 회고 저장. 월요일 시작, 7일 단위  |
| `3_projects`  | `{yyyy-MM-dd}_{프로젝트명}/` 형식. YAML frontmatter로 상태 관리    |
| `4_done`      | 완료된 프로젝트 보관. status, completed 메타데이터 유지                |
| `5_reference` | 사용자가 직접 관리하는 참고 자료                                     |
| `6_etcs`      | 기타 파일 (로그인 정보 등)                                       |

## Skills

| 명령어               | 기능                                                  |
| ----------------- | --------------------------------------------------- |
| `/vault:daily`    | 오늘 날짜 daily 폴더 생성. 이전 미완료 항목, 공지사항 자동 이월            |
| `/vault:weekly`   | 해당 주차 daily 데이터를 수집하여 주제별 분류/요약 회고 생성               |
| `/vault:project`  | 인터뷰를 통해 새 프로젝트 폴더 + requirements, PRD 파일 생성          |
| `/vault:tech-spec`| requirements + prd 분석하여 기술 명세(tech_spec) 생성           |
| `/vault:plan`     | requirements + prd + tech_spec 분석하여 plan + phase 파일 생성 |
| `/vault:handoff`  | phase 실행 결과를 분석하여 handoff 파일 생성 + plan 업데이트           |
| `/vault:done`     | 프로젝트 목록에서 선택 → complete 처리 + done으로 이동               |

## 프로젝트 상태 흐름

```
discovery(기획중) → in-progress(진행중) → complete(완료) → done 이동
```
