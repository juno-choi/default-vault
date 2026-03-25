# 1_daily

매일의 할일 관리 및 AI 대화 기록을 저장하는 폴더.

## 구조

```
1_daily/{yyyy-MM}/{yyyy-MM-dd}/
  ├── todo.md      # 할일 목록
  └── prompt.md    # AI 대화 기록
```

## 규칙

- 월 폴더(`yyyy-MM`) 아래에 일 폴더(`yyyy-MM-dd`)를 생성한다.
- `/daily` skill로 자동 생성한다.
- 생성 시 이전 날짜의 미완료 항목(`- [ ]`)과 공지사항을 자동 이월한다.
- prompt.md는 대화 기록이므로 절대 덮어쓰지 않는다.
