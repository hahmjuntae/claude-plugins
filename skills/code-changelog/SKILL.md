---
name: code-changelog
description: AI가 만든 모든 코드 변경사항을 reviews 폴더에 기록하고 간단한 HTML 뷰어로 웹 브라우저에서 실시간 확인. 매 수정마다 MD 문서 생성, Python 서버로 즉시 확인.
---

# Code Changelog with HTML Viewer

AI 코드 변경사항을 `reviews/` 폴더에 MD 파일로 기록하고, HTML 뷰어로 브라우저에서 확인.

## 핵심 기능

- 매 수정마다 `reviews/YYYYMMDD_HHMMSS.md` 자동 생성
- `save_and_build()` 호출 시 index.html 자동 업데이트 (파일 목록, 최신 문서 기본 표시)
- 다크 모드 GitHub 스타일 UI, Markdown 렌더링 (marked.js), 코드 하이라이팅

## 빠른 시작

### 1. 초기 설정
```bash
python3 create_changelog.py
```

### 2. 변경사항 기록
```python
from code_changelog_tracker import CodeChangeLogger

logger = CodeChangeLogger("프로젝트명", user_request="요구사항")
logger.log_file_creation("main.py", "코드", "이유")
logger.log_file_modification("auth.py", "old", "new", "암호화 추가")
logger.log_file_deletion("old_file.py", "이유")
logger.save_and_build()  # MD 저장 + SUMMARY + index.html 자동 갱신
```

### 3. 서버 실행
```bash
cd reviews && python3 -m http.server 4000
# http://localhost:4000 에서 확인
# 백그라운드: cd reviews && python3 -m http.server 4000 &
```

## 프로젝트 구조

```
project/
├── reviews/
│   ├── index.html          # HTML 뷰어 (자동 생성/갱신)
│   ├── README.md
│   ├── SUMMARY.md           # 네비게이션 (자동 생성)
│   └── 20260406_140000.md  # 변경 이력
├── code_changelog_tracker.py
└── create_changelog.py
```

## 명령어

| 작업 | 명령어 |
|------|--------|
| 서버 시작 | `cd reviews && python3 -m http.server 4000` |
| 백그라운드 | `cd reviews && python3 -m http.server 4000 &` |
| 포트 변경 | `python3 -m http.server 3000` |
| 서버 종료 | `lsof -ti:4000 \| xargs kill -9` |

## 배포

- **GitHub Pages**: `git subtree push --prefix reviews origin gh-pages`
- **Netlify**: Publish directory `reviews`
- **Vercel**: `vercel reviews`

## 문제 해결

- **포트 충돌**: 다른 포트 사용 또는 `lsof -ti:4000 | xargs kill -9`
- **파일 미표시**: `logger.save_and_build()` 재실행으로 index.html 재생성
- **렌더링 오류**: 브라우저 캐시 삭제 (Cmd+Shift+R)
