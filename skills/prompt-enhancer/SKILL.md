---
name: prompt-enhancer
description: Enhance user prompts by analyzing project context (code structure, dependencies, conventions). Use when brief development requests need project-specific context for accurate implementation.
---

# Prompt Enhancer

간략한 개발 요청을 프로젝트 컨텍스트 기반으로 구조화된 요구사항으로 변환. 확인 후 구현 진행.

## 트리거

"로그인 기능 만들어줘", "API 추가해줘" 등 구체적 구현 세부사항이 부족한 개발 요청 시.

## 워크플로우

### 1. 프로젝트 컨텍스트 분석

업로드 파일 확인 (`/mnt/user-data/uploads`), 다음 정보 수집:
- 프로젝트 구조, 기술 스택 (package.json, pubspec.yaml, requirements.txt 등)
- 기존 패턴 (상태관리, API, 라우팅), 코드 컨벤션, 유사 기능

### 2. 요청 의도 추출

Feature type (신규/버그픽스/리팩토링/API연동), Scope (단일화면/전체플로우/풀스택), Dependencies

### 3. 구조화된 요구사항 생성

```markdown
# [기능명] 구현 요구사항

## 프로젝트 컨텍스트
- Framework: [감지된 프레임워크]
- Architecture: [감지된 패턴]
- State Management: [감지된 라이브러리]
- Key Libraries: [관련 의존성]

## 구현 범위

### 주요 기능
1. [기능 1]
2. [기능 2]

### 파일 구조
[프로젝트 기반 예상 파일 구조]

## 상세 요구사항

### 1. [레이어/컴포넌트]
- **위치**: [파일 경로]
- **목적**: [역할]
- **구현 내용**: [세부사항]
- **기존 패턴 따르기**: [참조]

## 성공 기준
- [ ] [수용 기준]
- [ ] 기존 코드 스타일/아키텍처 일관성 유지
- [ ] 테스트 작성

## 확인 사항
- [질문/가정]

---
이 요구사항으로 진행할까요? 수정 필요 시 말씀해주세요.
```

### 4. 사용자 확인

**구현하지 않고** 요구사항만 제시. 사용자 확인 후 진행.

## 스택별 분석 포인트

### Flutter
감지: pubspec.yaml, lib/
수집: 상태관리 (Riverpod/Bloc/Provider/GetX), 아키텍처, Navigation (go_router/auto_route), Network (Dio/http), Storage
요구사항 포함: Presentation/Domain/Data Layer 구조, Navigation 설정, Widget test

### Next.js/React
감지: package.json with "next"/"react"
수집: App Router vs Pages Router, 상태관리 (Zustand/Redux/Context), 스타일링 (Tailwind/CSS Modules), TypeScript
요구사항 포함: UI Components, State, API Layer, Routing, 반응형, SEO

### Python (Django/FastAPI)
감지: requirements.txt, manage.py, main.py
수집: Framework, ORM, Auth, API docs
요구사항 포함: Models/Schema, Views/Endpoints, Business Logic, DB Migration, API docs

## 팁

- 프로젝트 컨텍스트 부족 시 파일 업로드 또는 프레임워크/상태관리/구조 정보 요청
- 기존 화면/컴포넌트 참조로 시각적 일관성 안내
- 연관 기능 (UserRepository, TokenStorage, ErrorHandler 등) 명시
