# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 프로젝트 개요

Obsidian Vault 기반 업무 자동화 시스템. 일일 할일 관리, 주간 회고, 프로젝트 생명주기를 Claude Code skill로 자동화한다.

## 핵심 규칙

### 날짜 규칙
- daily 경로: `workspace/1_daily/{yyyy-MM}/{yyyy-MM-dd}/`
- weekly 경로: `workspace/2_weekly/{yyyy}/W{nn}_review.md`
- 주차 계산: 월요일 시작, 단순 7일 단위. W01 = 1/1~1/7, W02 = 1/8~1/14, ...
- 프로젝트 폴더: `workspace/3_projects/{yyyy-MM-dd}_{프로젝트명}/`

### 프로젝트 상태 관리
- YAML frontmatter 사용: `created`, `deadline`, `status` 필드
- status 값: `discovery`(기획중) → `in-progress`(진행중) → `complete`(완료)
- hand-off 이동 시 `completed` 필드 추가, 기존 status 유지

### 파일 처리 원칙
- 템플릿은 `template/` 폴더의 파일을 기반으로 생성
- 이미 존재하는 파일은 덮어쓰지 않고 내용 보강 (prompt.md는 절대 덮어쓰지 않음)
- daily 생성 시 이전 날짜의 미완료 항목(`- [ ]`)과 공지사항을 자동 이월

## 응답 언어

모든 응답은 한국어로 작성. 코드와 식별자는 영어 유지.

---
## 회사 정보

### 도메인

### project 구조

### project 설명

### project 위치

