# Project 새 프로젝트 생성

`workspace/3_projects/`에 새 프로젝트 폴더를 생성한다.

## 실행 조건

- 프로젝트 루트: 이 파일 기준 `../../` (bdacs 폴더)
- 오늘 날짜를 `date +%Y-%m-%d` 로 구한다

## 실행 절차

### 1단계: 프로젝트 정보 인터뷰

사용자에게 순서대로 질문한다:

```
📝 새 프로젝트를 생성합니다.

1. 프로젝트명을 입력해주세요. (영문 snake_case 권장, 예: todo_list, auth_service)
```

사용자가 입력하면:

```
2. 마감일을 입력해주세요. (yyyy-MM-dd 형식, 예: 2026-04-15)
   미정이면 "미정"을 입력해주세요.
```

### 2단계: 입력 확인

```
🔍 프로젝트 정보를 확인합니다.

  프로젝트명: todo_list
  폴더명: 2026-03-25_todo_list
  마감일: 2026-04-15
  경로: workspace/3_projects/2026-03-25_todo_list/

생성할까요? (Y/n)
```

- 마감일이 "미정"이면 deadline 값을 `TBD`로 설정한다.
- 동일한 폴더명이 이미 존재하면 알린다:
  ```
  ⚠️ workspace/3_projects/2026-03-25_todo_list/ 가 이미 존재합니다.
  다른 프로젝트명을 입력해주세요.
  ```
  이후 1단계로 돌아간다.

### 3단계: 폴더 및 초기 파일 생성

1. `workspace/3_projects/{yyyy-MM-dd}_{프로젝트명}/` 폴더를 생성한다.
2. 폴더 안에 `1_prd.md` 파일 하나만 생성한다:

```md
---
created: {yyyy-MM-dd}
deadline: {마감일 또는 TBD}
status: discovery
---

# {프로젝트명}

```

나머지 파일(tech_spec, plan 등)은 사용자가 직접 추가한다.

### 4단계: 결과 보고

```
✅ 프로젝트 생성 완료

📁 workspace/3_projects/2026-03-25_todo_list/
  ✅ 1_prd.md 생성 (status: discovery)
```
