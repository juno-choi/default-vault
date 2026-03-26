# Done 프로젝트 완료 이동

완료된 프로젝트를 `workspace/3_projects/`에서 `workspace/4_done/`으로 이동한다.

## 실행 조건

- 프로젝트 루트: 이 파일 기준 `../../` (bdacs 폴더)
- 오늘 날짜를 `date +%Y-%m-%d` 로 구한다

## 실행 절차

### 1단계: 프로젝트 목록 조회

`workspace/3_projects/` 아래 모든 프로젝트 폴더를 탐색한다.

각 프로젝트의 첫 번째 `.md` 파일(보통 `1_prd.md`)에서 YAML frontmatter를 읽어 메타데이터를 수집한다.

프로젝트 목록을 아래 형식으로 출력한다:

```
📋 현재 프로젝트 목록

 #  | 프로젝트명                  | 상태          | 생성일      | 마감일
----+----------------------------+--------------+------------+-----------
 1  | 2026-03-01_todo_list       | in-progress  | 2026-03-01 | 2026-03-30
 2  | 2026-03-10_auth_service    | discovery    | 2026-03-10 | 2026-04-15
 3  | 2026-02-15_batch_job       | in-progress  | 2026-02-15 | 2026-03-20

완료 처리할 프로젝트 번호를 선택해주세요. (복수 선택 가능, 예: 1, 3)
```

프로젝트가 없으면:
```
📋 workspace/3_projects/에 프로젝트가 없습니다.
```
출력 후 종료한다.

### 2단계: 사용자 선택 확인

사용자가 번호를 선택하면, 선택된 프로젝트를 다시 확인한다:

```
🔍 선택한 프로젝트를 확인합니다.

1. 2026-03-01_todo_list (현재: in-progress)
3. 2026-02-15_batch_job (현재: in-progress)

위 프로젝트를 완료 처리하고 done으로 이동할까요? (Y/n)
```

사용자가 거부하면 1단계로 돌아간다.

### 3단계: 메타데이터 업데이트

선택된 각 프로젝트의 YAML frontmatter를 수정한다:

**변경 전:**
```yaml
---
created: 2026-03-01
deadline: 2026-03-30
status: in-progress
---
```

**변경 후:**
```yaml
---
created: 2026-03-01
deadline: 2026-03-30
status: complete
tags: Tag1, Tag2
completed: 2026-03-25
---
```

- `status`를 `complete`로 변경한다.
- `completed` 필드를 추가하고 오늘 날짜를 넣는다.
- 기존 `tags` 등 나머지 frontmatter 필드와 본문 내용은 그대로 유지한다.

YAML frontmatter가 있는 모든 `.md` 파일에 동일하게 적용한다.

### 4단계: 폴더 이동

`workspace/3_projects/{프로젝트 폴더}` → `workspace/4_done/{프로젝트 폴더}`

- 폴더명은 변경하지 않는다.
- `4_done/`에 동일한 이름의 폴더가 이미 있으면 사용자에게 알린다:
  ```
  ⚠️ 4_done/2026-03-01_todo_list 가 이미 존재합니다.
  1. 덮어쓰기
  2. 건너뛰기
  ```

### 5단계: 결과 보고

```
✅ Done 완료

📁 2026-03-01_todo_list
  → workspace/4_done/2026-03-01_todo_list
  status: in-progress → complete
  completed: 2026-03-25

📁 2026-02-15_batch_job
  → workspace/4_done/2026-02-15_batch_job
  status: in-progress → complete
  completed: 2026-03-25

이동된 프로젝트: 2건
```
