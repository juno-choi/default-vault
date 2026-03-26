# 3_projects

진행 중인 프로젝트를 관리하는 폴더.

## 구조

```
3_projects/{yyyy-MM-dd}_{프로젝트명}/
  ├── 1_requirements.md  # 요구사항, 내부 정보
  ├── 2_prd.md           # PRD (Product Requirements Document)
  ├── 3_tech_spec.md     # 기술 명세 (/tech-spec)
  ├── 4_plan.md          # 프로젝트 계획 (/plan)
  ├── 5_phase_{n}.md     # Phase별 실행 계획 (/plan)
  └── 5_hand_off_{n}.md  # Phase 수행 결과 (/handoff)
```

## 규칙

- `/project` skill로 인터뷰를 통해 생성한다 (1_requirements.md + 2_prd.md 초기 생성).
- YAML frontmatter로 상태를 관리한다: `created`, `deadline`, `status`, `tags`
- status 흐름: `discovery`(기획중) → `in-progress`(진행중) → `complete`(완료)
- 완료된 프로젝트는 `/done` skill로 `4_done/`으로 이동한다.
