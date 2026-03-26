# 3_projects

진행 중인 프로젝트를 관리하는 폴더.

## 구조

```
3_projects/{yyyy-MM-dd}_{프로젝트명}/
  └── 1_prd.md     # PRD (Product Requirements Document)
```

## 규칙

- `/project` skill로 인터뷰를 통해 생성한다.
- YAML frontmatter로 상태를 관리한다: `created`, `deadline`, `status`
- status 흐름: `discovery`(기획중) → `in-progress`(진행중) → `complete`(완료)
- 완료된 프로젝트는 `/done` skill로 `4_done/`으로 이동한다.
