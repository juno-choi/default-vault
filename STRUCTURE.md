# Structure

```text
.claude
CANVAS.canvas
README.md
CLAUDE.md
template
workspace
ㄴ1_daily
  ㄴ{yyyy-MM}
    ㄴ{yyyy-MM-dd}
        ㄴtodo.md
        ㄴprompt.md
ㄴ2_weekly
    ㄴ{yyyy}
        ㄴW01_review.md
        ㄴW02_review.md
ㄴ3_projects
  ㄴ{yyyy-MM-dd}_todo_list
    ㄴ1_requirements.md
    ㄴ2_prd.md
    ㄴ3_tech_spec.md
    ㄴ4_plan.md
    ㄴ5_phase_1.md
    ㄴ5_hand_off_1.md
    ㄴ5_phase_2.md
    ㄴ5_hand_off_2.md
    ㄴ5_phase_3.md
    ㄴ5_hand_off_3.md
  ㄴ{yyyy-MM-dd}_project_2
  	ㄴ1_prd.md
  	ㄴ2_plan.md
  	ㄴ3_phase.md
    ...
ㄴ4_done
  ㄴ{yyyy-MM-dd}_complete_project
  	ㄴ1_prd.md
ㄴ5_reference
  ㄴ1_crypto
    ㄴ1_crypto란.md
    ㄴ2_crypto.pdf
ㄴ6_etcs
  ㄴlogin
    ㄴaws.md
    ㄴgpt.md
```


## CANVAS.canvas
- 정리되는 내용을 canvas에 자동으로 처리하여 연관 마인드맵을 그려줌
- skill을 통해 command or trigger로 처리

## README.md
- canvas를 통해 자동으로 mind map을 그려줌
- 폴더 구조와 폴더별 설명
- 스킬이 있다면 스킬 이름과 스킬 설명
- subagent가 있다면 agent 이름과 설명

## .claude
- claude 관련 설정 및 저장소

## template
- 자동화하는 파일들의 템플릿을 미리 정의해두는 곳

## workspace
- 작업 폴더

### daily
- 사용자가 가장 많이 작업할 공간
- 매일 새롭게 생성
- todo.md 와 prompt.md 파일이 존재
- 할일의 체크리스트로 관리하며 사용자가 체크하면 해당 부분을 todo 외의 폴더에서 찾아서 체크
- skill을 통해 command or trigger로 처리

### weekly
- 사용자의 매일 업무에 대해 주마다 정리하여 회고
- skill을 통해 command or trigger로 처리
- 주차 기준: 월요일 시작, 단순 7일 단위 (1/1~1/7 = W01, 1/8~1/14 = W02, ...)

### projects
- 사용자 프로젝트 정리
- 폴더명은 {yyyy-MM-dd} 이고 생성일을 표시함.

# file 예시

## daily
- 매일 작업할 부분 정리

### todo.md
- 오늘 할일

```md
# 🔴 공지사항
- 3월 30일까지 xxx 업무 완료
- 4월 20일까지 연차 사용 제한

# 👊 이어서 할일
- [ ] 어제 못끝낸 일
- [ ] project에서 오늘부터 시작하는 일
- [ ] 

# ✅ 오늘 할일
- [ ] project 1 끝내기
- [x] 사용자가 끝낸 업무
```

### prompt.md
- ai와 대화한 내용 정리
- hook을 만들어서 해당 workspace에서 대화한 내용은 자동으로 해당 날짜 prompt.md에 내용을 저장

```md

🔴
사용자의 질문 내용을 적음

🟢
ai의 답변 내용을 적음

---

🔴
사용자의 질문 내용을 적음

🟢
ai의 답변 내용을 적음

---

🔴
사용자의 질문 내용을 적음

🟢
ai의 답변 내용을 적음

```

## weekly
주간 회고 폴더

### review.md

```md
# 🔴 한주동안 진행한 일
- 1번 업무
- 2번 업무

# 🔴 한주동안 ai와 대화한 내용 정리
## crypto
- crypto에 대해 ai에게 답변 받은 내용 정리

## project
- prd 내용 어느정도까지 진행
```

## projects
- 진행하고 있는 프로젝트 내용 정리

### requirements.md
- 요구 사항 및 개발 진행시 알고 있어야 할 사항들을 정리
- 회의록, 요구사항, 개발에 진행시 필요한 지식, 개발에 필요한 내부 정보 등
- project를 스킬로 생성시 자동으로 빈 파일로 생성
```
# 요구사항

# 개발 진행시 필요한 지식

# 개발에 필요한 내부 정보 (ai는 모르는 내부 정보 기입)

```

### prd.md
- 기획에서 작성된 prd 문서
- 링크를 알려주면 자동으로 confluence mcp를 통해 정보를 가져와서 md으로 작성

### tech_spec.md
- requirements.md 와 prd.md 기반의 개발 공유 문서 작성
- 아래 template을 참고하여 진행
```
## 과제 명
- 관련 링크 달기  
- JIRA, PRD 등 참고 할만한 문서
- GIT PR 링크 등..
    

## 요약
- 간단한 요약 2줄 정도
    
## 배경
- 어떤 문제를 해결하기 위해 ?
- 왜 만드는지
- 이전에 비슷한 시도가 있었는지
    
## 목표
- 예상 결과
    
### 목표가 아닌것
- 이번에 포함되지 말아야 할 것들
- 이 기능 저 기능 붙이는 것 방지
    

### 계획
- 어떻게 접근할 것인지
- 결정못한 사항이 있다면 어떤 것들을 고려하고 있는지
- 시퀀스 다이어그램, ERD 등을 포함하면 좋음
- 로우 레벨 까지 다뤄야 한다면 HTTP 응답, JSON 요청/응답 포맷 등 모두 작성하기

### 고려사항
- 최초 고려 되었으나 제외하기로 결정된 사항들 작성
    

### 마일스톤
- …
    
### 참고
```
- template과 skill을 만들어서 자동화 필요
### plan.md
- requirements.md, prd.md, tech_spec.md 문서를 분석하여 세부 계획을 세우고 phase 별로 진행할 계획을 세움
- plan 이라는 skill을 통해 자동화 필요 + phase 파일들도 함께 생성
```
# Plan: 계획 제목

## Goal
- 어떤 일을 해내야하 하는지
  
## Inputs
- requirements 경로
- prd 경로
- tech_spec 경로
  
## Done When
- phase 체크
- handoff 체크
  
## Steps
- [ ] phase_1
- [ ] phase_2
- [ ] phase_3
  ...
```

### phase_{number}.md
- plan에서 만들어진 phase의 단계별 상세 실행 계획

### handoff_{number}.md
- phase에서 수행한 내역을 확인
- handoff 라는 스킬을 통해 phase의 실행 내용을 체크하고 handoff에 진행한 내용을 기록
```
# Handoff_{number}

## Finished
- 끝낸일1
- 끝낸일2

## Blocked
- 해당 업무는 xx 이유로 아직 못함

## Changed
- 기존 계획에서 변경된 내용
  
## Next
- Phase_{number}
```

- status 값은 discovery(기획중), in-progress(진행중), complete(완료)
```md
---
created: {yyyy-MM-dd}
deadline: {yyyy-MM-dd}
status: {status}
tags: Tag1, Tag2
---

# 업무 내용
...

# 기타 내용
...
```


## done
- 진행이 완료된 프로젝트 이동
- skill을 통해 완료된 프로젝트는 자동으로 projects에서 done으로 이동
- 이동 시 status를 `complete`로 변경, `completed: {yyyy-MM-dd}` 필드 추가

## reference
- 사용자가 직접 참고하고자 하는 내용들을 저장해둠
- 다른 파일에서 참조하여 사용

## etcs
- 신경쓰지 않을 파일들