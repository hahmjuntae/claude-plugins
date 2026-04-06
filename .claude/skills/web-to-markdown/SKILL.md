---
name: web-to-markdown
description: 웹페이지 URL을 마크다운으로 변환하여 저장. 일반/AI최적화/듀얼 모드 지원. 동적 콘텐츠는 Playwright 폴백.
---

# Web to Markdown Converter

웹페이지 URL을 마크다운으로 변환하여 저장하는 스킬.

## 변환 모드

| 모드 | 트리거 키워드 | 출력 |
|------|--------------|------|
| **일반** (기본) | - | `article.md` |
| **AI 최적화** | "AI가 읽기 좋게", "컨텍스트로 사용" | `article.context.md` |
| **듀얼** | "원본이랑", "둘 다", "both" | 원본 `.md` + AI `.context.md` 2개 파일 |

## Core Workflow

### 1. URL 입력
- `http://` 또는 `https://`로 시작 필수 (HTTP는 자동 HTTPS 업그레이드)

### 2. 모드 자동 감지
사용자 요청에서 키워드로 모드 판별.

### 3. 저장 위치/파일명 확인
기본: 현재 디렉토리, `webpage.md`

### 4. WebFetch로 변환

**일반 모드 프롬프트:**
```
웹페이지 전체 내용을 마크다운으로 변환. 제목/본문/링크/이미지 포함, 네비게이션/광고 제외.
```

**AI 최적화 모드 프롬프트:**
```
AI 컨텍스트 최적화 형태로 변환:

필수 구조:
1. YAML 프론트매터: title, url, author, date, word_count, topics, summary, main_points, content_type, difficulty
2. 본문: 핵심 요약 -> 주요 내용 (H2/H3 계층) -> 핵심 인사이트 -> 실용적 적용 -> 관련 리소스 -> 결론

변환 규칙: 광고/네비/푸터 제거, 코드블록 언어 명시, 간결하게, 중요 개념 볼드
```

**듀얼 모드**: WebFetch를 2회 호출 (일반 프롬프트 + AI 최적화 프롬프트), 각각 저장.

### 5. 저장 및 결과 보고
파일 경로, 크기, 용도 안내.

## 동적 콘텐츠 처리 (JS 렌더링 페이지)

WebFetch 결과가 빈약할 때 (< 500자):

1. `AskUserQuestion`으로 Playwright 사용 여부 확인
2. **MCP Playwright** (권장): `browser_navigate` -> `browser_wait_for` (networkidle) -> `browser_snapshot` -> 마크다운 변환
3. **Node Playwright** (대안): `node` 스크립트로 `page.goto` + `page.content()` 실행

## 고급 기능

- **일괄 변환**: 여러 URL 순차 처리
- **섹션 추출**: 프롬프트에 특정 섹션명 명시
- **포맷 커스텀**: 프롬프트에 스타일 요구사항 추가

## Error Handling

- **잘못된 URL**: http/https 확인 요청
- **접근 불가**: 삭제/권한/네트워크 오류 안내
- **저장 실패**: 경로/권한/디렉토리 확인 안내

## 참고

- WebFetch 캐시: 15분
- 이미지: 원본 URL 링크 (다운로드 안 됨)
- 인코딩: UTF-8
