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

## 빠른 설치 표

| 스킬 | 설치 명령어 |
|------|------------|
| Flutter Init | `atelic@flutter-init` |
| Next.js 15 Init | `atelic@nextjs15-init` |
| Landing Page Guide V2 | `atelic@landing-page-guide-v2` |
| Landing Page Guide | `atelic@landing-page-guide` |
| Frontend Design | `atelic@frontend-design` |
| Design Prompt Generator V2 | `atelic@design-prompt-generator-v2` |
| Card News Generator V2 | `atelic@card-news-generator-v2` |
| Card News Generator | `atelic@card-news-generator` |
| Midjourney Card News BG | `atelic@midjourney-cardnews-bg` |
| Gemini Logo Remover | `atelic@gemini-logo-remover` |
| Prompt Enhancer | `atelic@prompt-enhancer` |
| Meta Prompt Generator | `atelic@meta-prompt-generator` |
| Code Prompt Coach | `atelic@code-prompt-coach` |
| Codex-Claude-Cursor Loop | `atelic@codex-claude-cursor-loop` |
| Codex-Claude Loop | `atelic@codex-claude-loop` |
| Codex | `atelic@codex` |
| Workthrough V2 | `atelic@workthrough-v2` |
| Workthrough | `atelic@workthrough` |
| Code Changelog | `atelic@code-changelog` |
| Web to Markdown | `atelic@web-to-markdown` |
| Web Search | `atelic@web-search` |

---

## 스킬 상세

### 프로젝트 생성

#### [Flutter Init](./skills/flutter-init/)
도메인 기반 Flutter 프로젝트를 Clean Architecture로 자동 생성합니다.

- 도메인 선택: Todo / Habit / Note / Expense / Custom
- 스택 프리셋: Minimal / Essential / Full Stack / Custom
- Riverpod 3.x, Drift, Freezed, Easy Localization, FluentUI Icons

#### [Next.js 15 Init](./skills/nextjs15-init/)
도메인 기반 Next.js 15 프로젝트를 App Router로 자동 생성합니다.

- 도메인 선택: Todo / Blog / Dashboard / E-commerce / Custom
- Next.js 15 App Router, ShadCN/ui, Zustand, Tanstack Query, Drizzle ORM, Better Auth
- TypeScript Strict Mode

---

### 디자인 & 랜딩페이지

#### [Landing Page Guide V2](./skills/landing-page-guide-v2/)
전환율과 브랜드 각인을 동시에 달성하는 랜딩페이지 제작 가이드.

- Design Thinking First — 코딩 전 미적 방향성 정의 (미니멀, 맥시멀리스트, 레트로, 유기적 등)
- 11가지 필수 전환 요소 + 디자인 우수성 기준
- Typography Excellence — Space Grotesk, Clash Display 등 (Inter/Roboto 금지)
- Advanced Animation — staggered reveals, parallax, scroll-triggered
- Spatial Composition — 비대칭, 오버랩, 대각선 흐름
- Next.js 15+ / TypeScript / Tailwind CSS / ShadCN UI / Framer Motion
- [참고자료: 11 Essential Elements](./skills/landing-page-guide-v2/references/11-essential-elements.md) · [Component Examples](./skills/landing-page-guide-v2/references/component-examples.md)

#### [Landing Page Guide](./skills/landing-page-guide/)
Next.js 14+ 기반 11가지 필수 요소 랜딩페이지 가이드. V2의 경량 버전.

#### [Frontend Design](./skills/frontend-design/)
프로덕션급 프론트엔드 UI 생성. 일반적인 AI 생성 미학을 탈피한 독특한 디자인 코드를 작성합니다.

#### [Design Prompt Generator V2](./skills/design-prompt-generator-v2/)
AI 웹 개발 도구(Lovable, Cursor, Bolt)를 위한 7단계 계층적 디자인 프롬프트 생성기.

```
Step 1: Domain Research      → 업종 UX 패턴, 경쟁사 인사이트
Step 2: User Journey         → 핵심 사용자 흐름, 전환 포인트
Step 3: Emotional Design     → 감성 키워드, 무드 컨셉
Step 4: Identity & Goal      → 브랜드 정체성, 목표
Step 5: Design System        → 컬러, 타이포, 컴포넌트
Step 6: Component Specs      → 핵심 컴포넌트 상세 정의
Step 7: Micro-interactions   → 애니메이션, 인터랙션 패턴
```

- 8개 도메인별 UX 패턴 매트릭스
- 7가지 감정 키워드 매트릭스
- [Sample: 펫시터 서비스 예제](./skills/design-prompt-generator-v2/sample/)

---

### 카드뉴스 & 이미지

#### [Card News Generator V2](./skills/card-news-generator-v2/)
배경 이미지를 지원하는 600x600 인스타그램 스타일 카드뉴스 생성기.

- 배경 이미지 자동 크롭/리사이징 (JPG, PNG, WebP, BMP)
- Cafe24Ssurround 폰트 번들 포함
- 반투명 박스 + 테두리, 오버레이 조절 (0.0-1.0)
- `python auto_generator.py --topic "주제" --image-folder ./imgs --overlay-opacity 0.6`

#### [Card News Generator](./skills/card-news-generator/)
600x600 인스타그램 스타일 카드뉴스 자동 생성. V2의 기본 버전.

- 주제와 색상만 입력하면 5-7장 카드 시리즈 생성
- 자동 텍스트 래핑 및 레이아웃
- 권장 색상: 베이지(`245,243,238`) 핑크(`255,229,229`) 민트(`224,244,241`) 라벤더(`232,224,245`)

#### [Midjourney Card News BG](./skills/midjourney-cardnews-bg/)
카드뉴스용 배경 이미지를 위한 Midjourney 프롬프트 생성.

- 주제/스타일/분위기 기반 프롬프트 자동 생성 (3-5가지 변형)
- 텍스트 오버레이에 최적화 — 중앙 60% 영역 균일 유지
- 스타일: 비즈니스/건강/금융/교육/음식/크리에이티브
- `--ar 1:1 --v 7`

#### [Gemini Logo Remover](./skills/gemini-logo-remover/)
OpenCV inpainting으로 AI 생성 이미지에서 로고/워터마크 제거.

- 좌표 기반 또는 코너 기반(bottom_right 등) 자동 제거
- TELEA 알고리즘, PNG/JPG/WebP/BMP 지원
- `pip install opencv-python numpy pillow`

---

### 프롬프트 & 자동화

#### [Prompt Enhancer](./skills/prompt-enhancer/)
프로젝트 컨텍스트를 분석해서 간단한 요청을 상세 요구사항으로 변환.

- 프로젝트 구조 자동 분석, 기존 패턴 인식
- "로그인 기능 만들어줘" → Clean Architecture 기반 상세 구현 요구사항
- Flutter (Riverpod), Next.js (App Router, Zustand), Python (Django, FastAPI) 지원

#### [Meta Prompt Generator](./skills/meta-prompt-generator/)
간단한 설명을 받아 구조화된 커스텀 슬래시 커맨드를 자동 생성.

- 지능형 지식 수집 (웹 검색)
- 단계 기반 워크플로우 설계 + 병렬 처리 최적화
- 포괄적인 테스트 생성

#### [Code Prompt Coach](./skills/code-prompt-coach/)
Claude Code 세션 로그를 분석하여 프롬프트 품질 향상.

- 8가지 통합 분석: 프롬프트 품질, 토큰/비용, 도구 사용 패턴, 세션 효율성, 생산성 시간대, 파일 수정 히트맵, 에러 복구, 프로젝트 전환 오버헤드
- 컨텍스트 인식 평가 (git commit, run tests 등)
- 모델별 요금 정확 계산 (Opus, Sonnet, Haiku)
- 로컬 로그만 분석 (`~/.claude/projects/`)

---

### AI 엔지니어링 루프

#### [Codex-Claude-Cursor Loop](./skills/codex-claude-cursor-loop/)
Claude + Codex + Cursor 3중 AI 루프.

1. **Claude** (계획) → 아키텍처 및 구현 계획 수립
2. **Codex** (검증) → 로직 에러, 보안 취약점 검토
3. **Cursor** (구현) → 검증된 계획으로 코드 작성
4. **Codex** (리뷰) → 버그, 성능, 보안 검증
5. **Claude** (최종) → 아키텍처 확인 및 승인
6. **반복** → 문제 시 수정 후 재검증

적합: 복잡한 기능 개발, 보안/성능 중요 작업, 대규모 리팩토링

#### [Codex-Claude Loop](./skills/codex-claude-loop/)
Claude + Codex 듀얼 AI 루프. Cursor 없이 Claude가 구현까지 담당하는 경량 버전.

- Claude: 계획 + 구현 + 수정 / Codex: 검증 + 리뷰
- `codex exec -m gpt-5-codex --sandbox read-only` (검증)
- `codex exec resume --last` (재검증)

#### [Codex](./skills/codex/)
OpenAI Codex CLI 래퍼.

- 모델 선택: gpt-5, gpt-5-codex
- 샌드박스: read-only / workspace-write / danger-full-access
- 세션 재개: `codex exec resume --last`

---

### 문서화 & 유틸리티

#### [Workthrough V2](./skills/workthrough-v2/)
개발 작업 자동 문서화 + VitePress 기반 문서 사이트.

- VitePress 자동 빌드, http://localhost:5173 서빙
- 실시간 업데이트 (HMR), 검색, 사이드바 자동 생성, 다크 모드
- `workthrough/YYYY-MM-DD-description.md` 형식

#### [Workthrough](./skills/workthrough/)
개발 작업 자동 문서화. V2의 경량 마크다운 전용 버전.

- 구조: Title → Context → Changes Made → Code Examples → Verification → Next Steps
- 버그 수정, 기능 구현, 리팩토링, 설정 변경 등 모든 작업 대상

#### [Code Changelog](./skills/code-changelog/)
AI가 만든 코드 변경사항을 자동 기록 + HTML 뷰어.

- 자동 문서 생성 (Markdown)
- 다크 모드 HTML 뷰어 (GitHub 스타일)
- Python 서버, http://localhost:4000

#### [Web to Markdown](./skills/web-to-markdown/)
웹페이지 URL을 마크다운으로 변환.

- 3가지 모드: 일반 / AI 최적화 (YAML 프론트매터, 토큰 30-50% 절감) / 듀얼 (두 버전 동시 생성)
- 동적 콘텐츠 자동 감지 → Playwright 폴백
- 여러 URL 일괄 변환, 특정 섹션 추출

#### [Web Search](./skills/web-search/)
DuckDuckGo 기반 웹/뉴스/이미지 검색.

- 3가지 검색: 텍스트, 뉴스, 이미지
- 지역별(한국, 미국, 일본) + 기간(일/주/월/년) 필터
- 검색 연산자: `site:`, `filetype:`, `"exact phrase"`, `-exclude`
- 빌트인 WebSearch 대비: US 외 지역, 뉴스/이미지 전용, 세밀한 필터

## 라이선스

MIT
