---
name: web-search
description: DuckDuckGo 웹 검색. 텍스트/뉴스/이미지 검색, 지역/기간 필터 지원. 빌트인 WebSearch가 제한적이거나 뉴스/이미지/필터가 필요할 때 사용.
---

# DuckDuckGo Web Search

## 사용 시점

- 빌트인 WebSearch 사용 불가 시 (US 외 지역)
- 뉴스/이미지 전용 검색
- 시간 범위/지역 필터 필요
- 결과를 JSON으로 저장/처리

빌트인 WebSearch 우선: US 지역 단순 텍스트 검색, 빠른 사실 확인.

## 사용법

```bash
python3 ~/.claude/skills/web-search/scripts/search.py -q "검색어" -t text -n 5
```

## 파라미터

| Flag | 필수 | 기본값 | 설명 |
|------|------|--------|------|
| `-q` | Yes | - | 검색 키워드 |
| `-t` | No | text | `text`, `news`, `images` |
| `-n` | No | 5 | 최대 결과 수 |
| `-r` | No | wt-wt | 지역: `kr-kr`, `us-en`, `jp-jp`, `uk-en` |
| `-s` | No | moderate | SafeSearch: `on`, `moderate`, `off` |
| `-p` | No | None | 기간: `d`(일), `w`(주), `m`(월), `y`(년) |

## 예시

```bash
# 한국 뉴스 (최근 1주)
python3 ~/.claude/skills/web-search/scripts/search.py -q "AI 인공지능" -t news -n 10 -r kr-kr -p w

# 이미지 검색
python3 ~/.claude/skills/web-search/scripts/search.py -q "modern web design" -t images -n 5

# 파일 저장
python3 ~/.claude/skills/web-search/scripts/search.py -q "React 19" -n 20 > results.json
```

## 검색 연산자

`site:example.com` | `filetype:pdf` | `"exact phrase"` | `-exclude`

## Error Handling

- **Rate Limit**: 재시도 또는 결과 수 줄임
- **Timeout**: 네트워크 확인 후 재시도
- **패키지 미설치**: 자동 설치 시도, 실패 시 `pip install -U ddgs`
