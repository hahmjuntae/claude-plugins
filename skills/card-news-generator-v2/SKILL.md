---
name: card-news-generator-v2
description: Create 600x600 Instagram-style card news series with optional background images. User provides topic, colors, optional images - generates content and creates multiple cards automatically.
---

# Card News Generator v2

600x600 카드 뉴스 시리즈 자동 생성 (배경 이미지 지원).

## When to Use

"카드 뉴스 만들어줘", "인스타용 카드 생성", 시각 카드 콘텐츠 요청 시.

## Core Workflow

### Step 1: 사용자 입력

- **주제**: 카드 시리즈 내용
- **배경색** (RGB, 기본: `245,243,238` 베이지) 또는 **배경 이미지 폴더 경로**
- 이미지 사용 시: **오버레이 불투명도** (0.0-1.0, 기본 0.5)

추천 색상: 베이지 `245,243,238` / 핑크 `255,229,229` / 민트 `224,244,241` / 라벤더 `232,224,245` / 피치 `255,232,214` / 스카이블루 `227,242,253`

### Step 2: 콘텐츠 생성 (5-7장)

```
1. [제목]
[설명 2-3줄]
```

**CRITICAL 글자 제한**: 제목 max 20자, 내용 max 60자 (600x600 캔버스 적합)

### Step 3: 카드 생성

**Option A: 단색 배경**
```bash
python auto_generator.py \
  --topic "[주제]" --bg-color "#hex" --text-color "#1a1a1a" \
  --output-dir /mnt/user-data/outputs --base-filename "[name]" << 'EOF'
1. 제목
내용 첫째 줄
내용 둘째 줄
EOF
```

**Option B: 배경 이미지**
```bash
python auto_generator.py \
  --topic "[주제]" --output-dir /mnt/user-data/outputs --base-filename "[name]" \
  --image-folder /path/to/images --overlay-opacity 0.6 << 'EOF'
1. 제목
내용
EOF
```

이미지 규칙: 알파벳/숫자순 정렬(`01.jpg`, `02.jpg`), 카드 수와 일치 권장 (부족 시 단색 대체). 지원 포맷: jpg, jpeg, png, webp, bmp. 이미지 사용 시 텍스트 자동 흰색.

### Step 4: 결과 제공

```
[View card 1](computer:///path/name_01.png)
```

## Single Card Mode

```bash
python generate_card.py \
  --title "제목" --content "내용" --bg-color "#hex" --text-color "#1a1a1a" \
  --number 1 --output /path/single.png
# 배경 이미지: --bg-image /path/image.jpg --overlay-opacity 0.6
```

## Technical Specs

- **Canvas**: 600x600px, padding 40px, max text 520px
- **Font**: Number 60px, Title 48px bold, Content 28px regular
- **Image processing**: 600x600 center crop, LANCZOS resampling, dark overlay
- **Text**: 자동 줄바꿈, 수동 줄바꿈 유지, 수평 중앙 정렬
- **파일명**: `{base}_{number:02d}.png`
- RGB→Hex: `'#{:02x}{:02x}{:02x}'.format(r, g, b)`

텍스트 오버플로우 시: 제목/내용 축소, 줄바꿈 활용 후 재생성.
