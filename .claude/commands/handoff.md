# Handoff Phase 수행 결과 기록

Phase의 실행 결과를 체크하고 `5_hand_off_{n}.md` 파일을 생성한다.

## 실행 조건

- 프로젝트 루트: 이 파일 기준 `../../`
- 오늘 날짜를 `date +%Y-%m-%d` 로 구한다
- 템플릿 경로: `template/handoff.md`

## 실행 절차

### 1단계: 프로젝트 선택

`workspace/3_projects/` 아래 모든 프로젝트 폴더를 탐색한다.

`4_plan.md`가 존재하는 프로젝트만 목록에 포함한다. plan이 없는 프로젝트는 handoff 대상이 아니므로 제외한다.

```
📋 Handoff 가능한 프로젝트 목록

 #  | 프로젝트명                  | 상태          | Phase 현황
----+----------------------------+--------------+--------------
 1  | 2026-03-01_todo_list       | in-progress  | 3개 중 1개 완료
 2  | 2026-03-10_auth_service    | in-progress  | 2개 중 0개 완료

프로젝트 번호를 선택해주세요.
```

프로젝트가 없으면:
```
📋 workspace/3_projects/에 plan이 있는 프로젝트가 없습니다.
먼저 /plan 으로 계획을 생성해주세요.
```
출력 후 종료한다.

### 2단계: Phase 선택

선택된 프로젝트에서 `5_phase_{n}.md` 파일들을 찾고, 각 phase의 상태를 확인한다.

상태 판별 기준:
- 대응하는 `5_hand_off_{n}.md`가 이미 존재하면 → **완료**
- 존재하지 않으면 → **미완료**

```
📋 Phase 목록

 #  | Phase                | 상태     | 제목
----+---------------------+---------+------------------
 1  | 5_phase_1.md        | ✅ 완료  | 기본 구조 설계
 2  | 5_phase_2.md        | 🔲 미완료 | API 개발
 3  | 5_phase_3.md        | 🔲 미완료 | 테스트 및 배포

Handoff를 작성할 Phase 번호를 선택해주세요.
```

이미 완료된 phase를 선택하면:
```
⚠️ Phase 1의 handoff가 이미 존재합니다 (5_hand_off_1.md).
1. 덮어쓰기
2. 다른 Phase 선택
```

### 3단계: Phase 실행 결과 분석

선택된 `5_phase_{n}.md`를 읽고 아래 항목을 분석한다:

**Tasks 체크리스트 확인:**
- `- [x]` 완료된 항목 → Finished 후보
- `- [ ]` 미완료 항목 → Blocked 후보

**Acceptance Criteria 확인:**
- `- [x]` 충족된 조건 → Finished 근거
- `- [ ]` 미충족 조건 → Blocked 근거

분석 결과를 사용자에게 제안한다:

```
🔍 Phase {n} 분석 결과

✅ Finished (완료된 작업):
- 작업 1 (Task + Acceptance Criteria 충족)
- 작업 2

🚫 Blocked (미완료 작업):
- 작업 3 — 사유를 입력해주세요

수정하거나 추가할 내용이 있으면 말씀해주세요.
특히 Blocked 항목의 사유와 Changed 내용이 있으면 알려주세요.
```

사용자에게 아래를 추가로 확인한다:
- Blocked 항목의 구체적 사유
- 기존 계획 대비 Changed 내용이 있는지

### 4단계: Handoff 파일 생성

`template/handoff.md` 를 기반으로 `5_hand_off_{n}.md`를 생성한다:

```md
# Handoff_{n}

## Finished
- {완료한 작업 1}
- {완료한 작업 2}

## Blocked
- {미완료 작업} — {사유}

## Changed
- {기존 계획 대비 변경 사항, 없으면 "없음"}

## Next
- Phase_{n+1}
```

- 마지막 phase의 handoff인 경우, Next 섹션:
  ```
  ## Next
  - 모든 Phase 완료. /done 으로 프로젝트 완료 처리 가능.
  ```

### 5단계: Plan 업데이트

`4_plan.md`의 Steps에서 해당 phase를 완료 처리한다:

**변경 전:**
```md
## Steps
- [ ] phase_1: 기본 구조 설계
- [ ] phase_2: API 개발
```

**변경 후:**
```md
## Steps
- [x] phase_1: 기본 구조 설계
- [ ] phase_2: API 개발
```

모든 phase가 완료되면 Done When도 업데이트한다.

### 6단계: 결과 보고

```
✅ Handoff 생성 완료

📁 workspace/3_projects/2026-03-01_todo_list/
  ✅ 5_hand_off_1.md 생성
  📝 4_plan.md 업데이트 (phase_1 완료 체크)

  Finished: 3건
  Blocked: 1건
  Changed: 없음
  Next: Phase_2
```
