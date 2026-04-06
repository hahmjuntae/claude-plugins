---
name: midjourney-card-news-backgrounds
description: Generate Midjourney prompts for 600x600 card news background images based on topic, mood, and style preferences.
---

# Midjourney Card News Background Generator

카드 뉴스/인스타 배경용 Midjourney 프롬프트 생성 (600x600, 텍스트 오버레이 최적화).

## 트리거

카드 뉴스 배경, 인스타 포스트 배경, 1:1 소셜미디어 배경 요청 시.

## 프롬프트 구조

```
[subject/scene], [style keywords], [color palette], [texture/atmosphere], [technical] --ar 1:1 --v 7
```

| 요소 | 가이드 |
|------|--------|
| Subject | 5-10단어, 구체적 시각 요소, 추상 개념 회피 |
| Style | 3-5 키워드 (minimal, gradient, geometric, organic 등) |
| Color | 정확한 색상명 + 강도 (pastel blue, vibrant coral), 3-4색 이내 |
| Texture | 2-3 키워드 (smooth, flowing, textured, light and airy 등) |
| Specs | `--ar 1:1 --v 7` 필수. 선택: `--s 50-250`, `--chaos 0-100` |

## 주제별 스타일 가이드

| 카테고리 | 색상 | 스타일 |
|----------|------|--------|
| Business/Tech | blue, purple, teal | clean gradients, geometric |
| Health/Wellness | green, peach, soft pink | soft pastels, organic shapes |
| Finance | navy, gold, green | bold gradients, sharp lines |
| Education | yellow, orange, light blue | friendly, simple shapes |
| Food/Lifestyle | earth tones, warm orange | warm, natural textures |
| Creative/Art | vibrant multi-color | bold abstract patterns |

## 텍스트 오버레이 최적화

- 중앙 60% 균일한 밝기 유지
- 복잡한 요소는 코너에 배치
- 중앙 가로선, 고대비 패턴, 세밀한 텍스처 회피

## 예시 프롬프트

**Tech/AI:**
```
abstract neural network patterns, modern tech aesthetic, gradient blue and cyan tones, smooth digital waves, clean negative space for text --ar 1:1 --v 7
```

**Finance:**
```
elegant geometric patterns, premium professional style, navy and gold gradient, subtle texture with depth, sophisticated minimal design --ar 1:1 --v 7
```

**Mental Health:**
```
calming abstract clouds, serene peaceful atmosphere, soft lavender and mint gradients, dreamy gentle textures, meditative minimal space --ar 1:1 --v 7
```

## 응답 형식

주제당 3가지 스타일 제안:
```
주제: [topic]

1. 메인 추천:
[prompt]
→ [한국어 설명]

2. 대안 1:
[prompt]
→ [한국어 설명]

3. 대안 2:
[prompt]
→ [한국어 설명]
```

## 한국어 지원

한국어 주제 이해 → 영어 프롬프트 생성 → 한국어 설명 제공. Midjourney 프롬프트는 반드시 영어.

## 고급 파라미터

- `--s 50`: realistic | `--s 150`: balanced (기본) | `--s 250`: artistic
- `--chaos 0-100`: 변형 제어 (0=일관)

60단어 이내, 구체적 색상명 사용, 브랜드/로고 요청 금지.
