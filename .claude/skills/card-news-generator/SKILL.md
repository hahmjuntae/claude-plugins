---
name: card-news-generator
description: Create 600x600 Instagram-style card news series with optional background images. User provides topic, colors, and optional images.
---

# Card News Generator (V2)

600x600 카드 뉴스 시리즈 자동 생성 (배경 이미지 지원).

## 트리거

"카드 뉴스 만들어줘", "카드 시리즈", "인스타용 카드" 등 시각 카드 콘텐츠 요청 시.

## 워크플로우

### 1단계: 사용자 입력 수집

필수: **주제**, 선택: **배경색** (RGB, 기본 245,243,238), **배경 이미지 폴더**, **오버레이 불투명도** (0.0-1.0, 기본 0.5)

추천 색상: 베이지 `245,243,238` | 핑크 `255,229,229` | 민트 `224,244,241` | 라벤더 `232,224,245` | 피치 `255,232,214` | 스카이블루 `227,242,253`

RGB→Hex 변환: `'#{:02x}{:02x}{:02x}'.format(r, g, b)`

### 2단계: 콘텐츠 생성 (5-7장)

**글자 수 제한 필수:**
- 제목: 최대 20자 (공백 포함)
- 내용: 최대 60자 (공백 포함)
- 카드당 핵심 메시지 1개

```
1. 디지털 네이티브
태어날 때부터
디지털 환경에 익숙

2. 개인화 중시
나만의 개성과
취향을 중요시
```

### 3단계: 카드 생성

**단색 배경:**
```bash
python auto_generator.py \
  --topic "주제" \
  --bg-color "#f5f3ee" \
  --text-color "#1a1a1a" \
  --output-dir /mnt/user-data/outputs \
  --base-filename "name" << 'EOF'
1. 제목
내용 줄1
내용 줄2
EOF
```

**배경 이미지 (V2):**
```bash
python auto_generator.py \
  --topic "주제" \
  --output-dir /mnt/user-data/outputs \
  --base-filename "name" \
  --image-folder /path/to/images \
  --overlay-opacity 0.6 << 'EOF'
1. 제목
내용 줄1
내용 줄2
EOF
```

이미지 폴더 규칙: 알파벳/숫자순 정렬 (`01.jpg`, `02.jpg`), 카드 수와 일치, 부족 시 단색 대체. 지원 형식: JPG, JPEG, PNG, WebP, BMP. 이미지 사용 시 텍스트 자동 흰색 전환.

### 단일 카드 모드

```bash
python generate_card.py \
  --title "제목" --content "내용" \
  --bg-color "#f5f3ee" --text-color "#1a1a1a" \
  --number 1 --output /mnt/user-data/outputs/single.png
```

배경 이미지: `--bg-image /path/to/img.jpg --overlay-opacity 0.6` 추가.

### 4단계: 결과 제공

```
✅ 카드 뉴스 N장 생성 완료!
[View card 1](computer:///mnt/user-data/outputs/name_01.png)
```

## 기술 사양

- 캔버스: 600x600px, 패딩 40px, 텍스트 최대 폭 520px
- 폰트: 번호 60px, 제목 48px bold, 내용 28px
- 이미지 처리: 600x600 리사이즈+센터크롭 (LANCZOS), 다크 오버레이 적용
- 텍스트: 자동 줄바꿈, 수동 줄바꿈 유지, 수평 중앙 정렬
- 파일명: `{base}_{number:02d}.png`

## 오류 대응

텍스트 오버플로 시: 제목 축소, 내용 단축, 줄바꿈 활용 후 재생성.
