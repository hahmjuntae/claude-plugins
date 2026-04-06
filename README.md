# Claude Code Skills

Claude Code 커스텀 스킬 모음. 개발 생산성을 높이기 위한 21개 자동화 스킬을 제공합니다.

## 설치

```bash
# 마켓플레이스 등록
/plugin marketplace add hahmjuntae/claude-plugins

# 개별 스킬 설치
/plugin marketplace install atelic@{스킬명}

# 설치된 스킬 확인
/plugin list

# 스킬 업데이트
/plugin update atelic@{스킬명}

# 마켓플레이스 제거
/plugin marketplace remove atelic
```

## 스킬 목록

### 프로젝트 생성

| 스킬 | 설명 | 설치 |
|------|------|------|
| [flutter-init](./skills/flutter-init/) | Flutter Clean Architecture 프로젝트 스캐폴딩 | `atelic@flutter-init` |
| [nextjs15-init](./skills/nextjs15-init/) | Next.js 15 App Router 프로젝트 스캐폴딩 | `atelic@nextjs15-init` |

### 디자인 & 랜딩페이지

| 스킬 | 설명 | 설치 |
|------|------|------|
| [landing-page-guide-v2](./skills/landing-page-guide-v2/) | 고전환율 랜딩페이지 제작 가이드 | `atelic@landing-page-guide-v2` |
| [landing-page-guide](./skills/landing-page-guide/) | 랜딩페이지 11가지 필수 요소 가이드 | `atelic@landing-page-guide` |
| [frontend-design](./skills/frontend-design/) | 프로덕션급 프론트엔드 UI 생성 | `atelic@frontend-design` |
| [design-prompt-generator-v2](./skills/design-prompt-generator-v2/) | AI 웹빌더용 디자인 프롬프트 생성 | `atelic@design-prompt-generator-v2` |

### 카드뉴스 & 이미지

| 스킬 | 설명 | 설치 |
|------|------|------|
| [card-news-generator-v2](./skills/card-news-generator-v2/) | 배경 이미지 지원 카드뉴스 생성 | `atelic@card-news-generator-v2` |
| [card-news-generator](./skills/card-news-generator/) | 600x600 인스타 카드뉴스 자동 생성 | `atelic@card-news-generator` |
| [midjourney-cardnews-bg](./skills/midjourney-cardnews-bg/) | Midjourney 배경 프롬프트 생성 | `atelic@midjourney-cardnews-bg` |
| [gemini-logo-remover](./skills/gemini-logo-remover/) | OpenCV 워터마크/로고 제거 | `atelic@gemini-logo-remover` |

### 프롬프트 & 자동화

| 스킬 | 설명 | 설치 |
|------|------|------|
| [prompt-enhancer](./skills/prompt-enhancer/) | 프로젝트 컨텍스트 기반 프롬프트 강화 | `atelic@prompt-enhancer` |
| [meta-prompt-generator](./skills/meta-prompt-generator/) | 구조화된 슬래시 커맨드 자동 생성 | `atelic@meta-prompt-generator` |
| [code-prompt-coach](./skills/code-prompt-coach/) | Claude Code 세션 로그 기반 프롬프트 코칭 | `atelic@code-prompt-coach` |

### AI 엔지니어링 루프

| 스킬 | 설명 | 설치 |
|------|------|------|
| [codex-claude-cursor-loop](./skills/codex-claude-cursor-loop/) | Claude + Codex + Cursor 3중 AI 루프 | `atelic@codex-claude-cursor-loop` |
| [codex-claude-loop](./skills/codex-claude-loop/) | Claude + Codex 듀얼 AI 루프 | `atelic@codex-claude-loop` |
| [codex](./skills/codex/) | OpenAI Codex CLI 래퍼 | `atelic@codex` |

### 문서화 & 유틸리티

| 스킬 | 설명 | 설치 |
|------|------|------|
| [workthrough-v2](./skills/workthrough-v2/) | 개발 작업 문서화 + VitePress 서빙 | `atelic@workthrough-v2` |
| [workthrough](./skills/workthrough/) | 개발 작업 자동 문서화 | `atelic@workthrough` |
| [code-changelog](./skills/code-changelog/) | 코드 변경사항 자동 기록 + HTML 뷰어 | `atelic@code-changelog` |
| [web-to-markdown](./skills/web-to-markdown/) | 웹페이지 → 마크다운 변환 | `atelic@web-to-markdown` |
| [web-search](./skills/web-search/) | DuckDuckGo 기반 웹/뉴스/이미지 검색 | `atelic@web-search` |

## 라이선스

MIT
