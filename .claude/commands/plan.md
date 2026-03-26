# Plan 프로젝트 계획 생성

프로젝트의 requirements, prd, tech_spec 문서를 분석하여 `4_plan.md`와 `5_phase_{n}.md` 파일들을 자동 생성한다.

## 실행 조건

- 프로젝트 루트: 이 파일 기준 `../../`
- 오늘 날짜를 `date +%Y-%m-%d` 로 구한다
- 템플릿 경로: `template/plan.md`, `template/phase.md`

## 실행 절차

### 1단계: 프로젝트 선택

`workspace/3_projects/` 아래 모든 프로젝트 폴더를 탐색한다.

각 프로젝트의 첫 번째 `.md` 파일에서 YAML frontmatter를 읽어 메타데이터를 수집한다.

프로젝트 목록을 아래 형식으로 출력한다:

```
📋 현재 프로젝트 목록

 #  | 프로젝트명                  | 상태          | 생성일      | 마감일
----+----------------------------+--------------+------------+-----------
 1  | 2026-03-01_todo_list       | in-progress  | 2026-03-01 | 2026-03-30
 2  | 2026-03-10_auth_service    | discovery    | 2026-03-10 | 2026-04-15

계획을 생성할 프로젝트 번호를 선택해주세요.
```

프로젝트가 없으면:
```
📋 workspace/3_projects/에 프로젝트가 없습니다.
```
출력 후 종료한다.

### 2단계: 입력 문서 확인

선택된 프로젝트 폴더에서 아래 파일의 존재 여부를 확인한다:
- `1_requirements.md`
- `2_prd.md`
- `3_tech_spec.md`

확인 결과를 출력한다:

```
📄 입력 문서 확인

  ✅ 1_requirements.md
  ✅ 2_prd.md
  ⚠️ 3_tech_spec.md — 없음

tech_spec 없이 계속 진행할까요? (Y/n)
```

- 3개 모두 없으면 최소 1개 이상 문서를 먼저 작성하라고 안내 후 종료한다.
- 있는 파일들의 내용을 모두 읽어서 분석에 활용한다.

### 3단계: 문서 분석 및 계획 제안

읽은 문서를 분석하여 아래 내용을 사용자에게 제안한다:

```
🔍 문서 분석 결과

📌 계획 제목: {문서에서 추론한 계획 제목}

🎯 Goal:
- {문서 분석으로 도출한 핵심 목표}

📋 Phase 구성 (총 {n}개):
  Phase 1: {phase 제목} — {한 줄 요약}
  Phase 2: {phase 제목} — {한 줄 요약}
  Phase 3: {phase 제목} — {한 줄 요약}

수정할 내용이 있으면 말씀해주세요. 없으면 Y를 입력해주세요.
```

- 사용자가 수정을 요청하면 반영 후 다시 제안한다.
- 사용자가 승인하면 다음 단계로 진행한다.

### 4단계: 파일 생성

#### 4-1. `4_plan.md` 생성

`template/plan.md` 를 기반으로 생성한다:

```md
# Plan: {계획 제목}

## Goal
- {3단계에서 확정한 목표}

## Inputs
- requirements: {프로젝트 경로}/1_requirements.md
- prd: {프로젝트 경로}/2_prd.md
- tech_spec: {프로젝트 경로}/3_tech_spec.md

## Done When
- [ ] 모든 phase 완료
- [ ] 모든 handoff 작성 완료

## Steps
- [ ] phase_1: {phase 1 제목}
- [ ] phase_2: {phase 2 제목}
- [ ] phase_3: {phase 3 제목}
```

#### 4-2. `5_phase_{n}.md` 생성

각 phase마다 `template/phase.md` 를 기반으로 생성한다:

```md
# Phase_{n}: {phase 제목}

## Objective
- {이 phase가 달성해야 할 한 줄 목표}

## Context
- plan: {프로젝트 경로}/4_plan.md
- 선행 조건: {Phase 1이면 "없음", 이후는 "Phase_{n-1} 완료"}
- 관련 문서: {이 phase와 관련된 입력 문서 경로}

## Tasks
- [ ] {구체적 작업 1}
- [ ] {구체적 작업 2}
- [ ] {구체적 작업 3}

## Constraints
- {이 phase에서 다루지 않는 범위}

## Acceptance Criteria
- [ ] {완료 조건 1}
- [ ] {완료 조건 2}
```

#### 파일 충돌 처리

- `4_plan.md`가 이미 존재하면:
  ```
  ⚠️ 4_plan.md가 이미 존재합니다.
  1. 덮어쓰기
  2. 건너뛰기
  ```
- `5_phase_{n}.md`가 이미 존재하면 동일하게 처리한다.

### 5단계: 프로젝트 상태 업데이트

프로젝트의 YAML frontmatter에서 `status`가 `discovery`이면 `in-progress`로 변경한다.

사용자에게 변경 여부를 알린다:
```
📝 프로젝트 상태: discovery → in-progress 변경
```

`status`가 이미 `in-progress`이면 변경하지 않는다.

### 6단계: 결과 보고

```
✅ Plan 생성 완료

📁 workspace/3_projects/2026-03-01_todo_list/
  ✅ 4_plan.md 생성
  ✅ 5_phase_1.md 생성
  ✅ 5_phase_2.md 생성
  ✅ 5_phase_3.md 생성
  📝 status: discovery → in-progress

총 {n}개 파일 생성
```
