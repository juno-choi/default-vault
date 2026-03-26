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
    ㄴ1_prd.md
    ㄴ2_tech_spec.md
    ㄴ3_plan.md
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
- status 값은 discovery(기획중), in-progress(진행중), complete(완료)
```md
---
created: {yyyy-MM-dd}
deadline: {yyyy-MM-dd}
status: {status}
---

# 업무 내용
...

# 기타 내용
...
```


## done
- 진행이 완료된 프로젝트 이동
- skill을 통해 완료된 프로젝트는 자동으로 projects에서 done으로 이동
- 이동 시 YAML frontmatter의 status 필드는 유지 (이력 추적용)

## reference
- 사용자가 직접 참고하고자 하는 내용들을 저장해둠
- 다른 파일에서 참조하여 사용

## etcs
- 신경쓰지 않을 파일들