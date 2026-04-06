---
name: "Prompt Coach"
description: "Analyze Claude Code session logs to improve prompt quality, optimize tool usage, and become a better AI-native engineer."
---

# Prompt Coach

AI-native 엔지니어링 전문가. Claude Code 세션 로그(`~/.claude/projects/*.jsonl`) 분석으로 프롬프트 품질, 도구 사용, 효율성 개선을 지원.

**이 머신의 로컬 로그만 분석 가능.** 다른 기기/클라우드/삭제된 로그/웹·모바일 Claude 세션은 불가.

## 사용법

### 종합 분석 (추천)
"Give me a general analysis of my Claude Code usage" → 8개 분석 항목 종합 보고서 생성.

### 프로젝트 탐색
"List all projects with Claude Code logs" → `~/.claude/projects/` 하위 프로젝트별 세션 수/기간/크기 표시.

### 특정 분석
"Analyze my prompt quality for ~/code/my-app" — 프로젝트 경로 지정 가능. 기본 분석 기간: 최근 30일. "last week", "from Nov 1 to Nov 9" 등 기간 지정 가능.

### 보고서 저장
"... and save as docs/analysis.md"

### 프로젝트 경로 매핑
실제 경로 `/Users/name/code/my-app` → 로그 디렉토리 `~/.claude/projects/-Users-name-code-my-app/`

## 로그 형식

각 `.jsonl` 파일 = 한 세션. 각 줄 = JSON 이벤트.

**User entry:** `type: "user"`, `message.content`, `timestamp`, `sessionId`, `cwd`, `gitBranch`
**Assistant entry:** `type: "assistant"`, `message.model`, `message.content[]` (text/tool_use), `message.usage` (input_tokens, output_tokens, cache_creation_input_tokens, cache_read_input_tokens)

**주요 도구:** Read, Write, Edit, Bash, Grep, Glob, Task, TodoWrite, WebFetch, WebSearch, NotebookEdit, `mcp__*`

## 프롬프트 품질 평가 기준

### 핵심 원칙
"동료에게 최소 컨텍스트로 보여줬을 때 혼란스러우면 Claude도 혼란."

### 평가 차원 (각 0-10)
1. **Clarity**: 명확성/비모호성
2. **Specificity**: 필요 정보 포함 (명시적 OR 암시적 컨텍스트)
3. **Actionability**: 즉시 실행 가능 여부
4. **Scope**: 적절한 크기/집중도

**점수 기준:** 8-10 Excellent | 5-7 Good | 3-4 Needs work | 0-2 Poor

### 컨텍스트 인식 분석 (핵심)

**간결함 ≠ 문제.** 프롬프트 품질 = 명시적 정보 + 암시적 컨텍스트.

**높은 점수 (8-10) — 컨텍스트 풍부한 간결 프롬프트:**
- Git 명령 ("git commit", "push") → git diff 컨텍스트 있음
- 빌드/테스트 ("run tests", "build", "npm test") → 프로젝트 구조 컨텍스트
- 개발 명령 ("install dependencies", "lint", "format")
- 후속 요청 ("try again", "edit this function") → 최근 작업 컨텍스트
- 응답 ("yes", "1", "continue") → Claude 질문에 대한 답변
- 연속 작업 ("continue", "do the same for X")

**낮은 점수 (0-4) — 컨텍스트 부족 독립 프롬프트:**
- 파일 미지정: "fix the bug", "update the component"
- 모호한 동사: "improve", "optimize", "make better"
- 에러 정보 없음: "fix the error", "it's not working"
- 범위 모호: "refactor the code", "add tests"
- 방법 미지정: "add authentication", "implement caching"

**분석 시 필수 확인:**
1. 이전 assistant 메시지 확인 — Claude가 질문/옵션 제시했으면 단답("1", "yes")은 완벽한 응답
2. 환경 컨텍스트 (최근 도구 사용, 파일 수정) 확인
3. 대화 컨텍스트 (이전 논의, 진행 중인 작업) 확인

## 분석 항목

### 0. 종합 분석 (General Analysis)

8개 항목 전체 분석 → 단일 종합 보고서. Task 도구(general-purpose 서브에이전트) 활용 권장.

보고서 구조: Executive Summary → 8개 섹션 → Top 5 추천 → Next Steps 체크리스트

### 1. Token Usage & Cost Analysis

**필수: 중복 제거** — `message.id + requestId` 해시로 Set 관리, 중복 스킵 (스트리밍 응답 다중 로깅).

**필수: 모델별 요금 적용** — `message.model` 필드에서 모델 추출:

| Model | Input | Output | Cache Write | Cache Read |
|-------|-------|--------|-------------|------------|
| Opus 4.1 (`claude-opus-4-1-*`) | $15/1M | $75/1M | $18.75/1M | $1.50/1M |
| Sonnet 4.5 (`claude-sonnet-4-5-*`) ≤200K | $3/1M | $15/1M | $3.75/1M | $0.30/1M |
| Sonnet 4.5 >200K | $6/1M | $22.50/1M | $7.50/1M | $0.60/1M |
| Haiku 4.5 (`claude-haiku-4-5-*`) | $1/1M | $5/1M | $1.25/1M | $0.10/1M |
| Haiku 3.5 (`claude-haiku-3-5-*`) | $0.80/1M | $4/1M | $1/1M | $0.08/1M |
| Opus 3 (`claude-3-opus-*`) | $15/1M | $75/1M | $18.75/1M | $1.50/1M |

**과금 모델별 추천 차별화:**
- Pay-per-use: 비용 최적화 직접 관련, 모델 선택 영향 큼
- Subscription: 비용보다 캐시(속도/UX) + 세션 효율성 + 프롬프트 품질 집중

출력: 모델별 토큰 분류, 비용, 캐시 효율, 중복 제거 통계, 월간 프로젝션.

### 2. Prompt Quality Analysis

Task 도구(general-purpose) 권장 — 다수 세션 파일의 맥락 기반 주관적 분석.

단계:
1. 최근 세션 읽기 → user 프롬프트 식별
2. 후속 assistant 응답의 AskUserQuestion/명확화 질문 확인
3. **컨텍스트 인식 분석** 적용 (위 기준)
4. 0-4점 프롬프트 **전수 목록** + 각각: 원문, 점수, 문제점, 가용 컨텍스트, Claude 반응, 개선 버전, 절약 시간
5. 통계: 전체 프롬프트 수, 카테고리별 분포, clarification rate, 평균 점수
6. Top 3 개선 추천 (최대 임팩트 순)

### 3. Tool Usage Patterns

1. tool_use 블록 추출 → 도구명별 카운트
2. 분류: Built-in (Read, Write, Edit, Bash, Grep, Glob, Task 등) | MCP (`mcp__*` → 서버명 파싱)
3. Built-in = 요약 한 줄, MCP = 서버별 상세 분류
4. 워크플로우 패턴, 성공/실패율, MCP 채택 수준 분석

### 4. Session Efficiency Analysis

sessionId별: 메시지 수, user 메시지(iterations), 기간, 완료 신호(git commit, build, test).
지표: 세션당 평균 iterations, 평균 기간, 완료율, Quick wins(<5min) / Standard(5-30) / Deep work(>30).

### 5. Productivity Time Patterns

타임스탬프 기반: 시간대(0-23), 요일별 세션 수/iterations/기간/효율 분석. 최고/최저 효율 시간대 추천.

### 6. File Modification Heatmap

Edit/Write 도구의 file_path 추출 → 파일별/디렉토리별 수정 횟수. 핫스팟 = 리팩토링 필요 신호.

### 7. Error & Recovery Analysis

Bash 도구 결과의 에러 패턴 (non-zero exit, npm ERR!, error:, failed 등). 에러 유형별 복구 시간/시도 횟수 분석.

### 8. Project Switching Analysis

cwd 변화 추적 → 일일 프로젝트 전환 횟수, 프로젝트별 시간 분배, 전환 오버헤드. 시간 블로킹/배치 처리 추천.

## 분석 가이드라인

1. **샘플링**: 최근 5-10 파일, 대형 파일은 앞뒤 N줄, 날짜별 균등 샘플
2. **JSON 파싱**: 줄 단위, 잘못된 줄 건너뛰기
3. **프라이버시**: 패턴 중심, 코드/프롬프트 그대로 반복 금지 (예시용 제외)
4. **실행 가능한 인사이트**: 항상 추천/팁 포함, 벤치마크 비교
5. **시각화**: ASCII 차트, 이모지 지표, 테이블

## Bash 참고 명령

```bash
ls -la ~/.claude/projects/-Users-username-code-projectname/  # 프로젝트 세션
find ~/.claude/projects -name "*.jsonl" -newermt "2025-01-01" -ls  # 날짜 필터
du -sh ~/.claude/projects  # 전체 크기
find ~/.claude/projects -name "*.jsonl" | wc -l  # 세션 수
```
