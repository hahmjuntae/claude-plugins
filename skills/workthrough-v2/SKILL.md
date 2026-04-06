---
name: workthrough
description: "개발 작업 완료 후 자동 실행. 작업 요약, 변경/개선 내용, 향후 제안을 간결한 한국어로 작성."
license: MIT
---

# Workthrough v2

개발 완료 시 자동으로 간결한 작업 요약 문서 생성.

## 규칙

- 개발 완료 시 자동 실행, 한국어 작성
- 위치: `<project-root>/workthrough/YYYY-MM-DD_HH_MM_description.md`
- 핵심만 간결하게, 긴 설명 금지

## 문서 템플릿

```markdown
# [작업 제목]

## 개요
2-3문장 요약

## 주요 변경사항
- 개발: XXX 기능 추가
- 수정: YYY 버그 수정
- 개선: ZZZ 성능 향상

## 핵심 코드 (필요시만)
` ``typescript
const key = value
` ``

## 결과
- 빌드/테스트 성공 여부

## 다음 단계
- 다음 구현/수정 사항
```

## VitePress

- **첫 실행** (workthrough 폴더 없음): 초기 설정 + `pnpm install && pnpm dev`
- **이후**: 새 문서만 생성 + `pnpm build` 확인
