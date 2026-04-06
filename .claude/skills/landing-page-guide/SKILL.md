---
name: landing-page-guide
description: Guide for creating effective landing pages using Next.js 15+ with App Router and ShadCN UI, following the 11 essential elements framework for high-converting pages.
---

# Landing Page Guide

11 essential elements framework (DESIGNNAS) 기반 고전환 랜딩페이지 생성 가이드.

## When to Use

User requests: landing pages, marketing pages, product pages needing conversion optimization with Next.js/React.

## 11 Essential Elements (All Required)

1. **URL** - SEO keyword 포함
2. **Logo** - Header top-left 브랜드 아이덴티티
3. **Title/Subtitle** - 명확한 가치 제안 + SEO 키워드
4. **Primary CTA** - Hero 섹션 메인 액션 버튼
5. **Social Proof** - 리뷰, 평점, 사용자 통계
6. **Media** - 제품/서비스 시각 자료
7. **Benefits** - 3-6개 핵심 장점 + 아이콘
8. **Testimonials** - 4-6개 고객 후기 + 사진
9. **FAQ** - 5-10개 질문 아코디언 UI
10. **Final CTA** - 하단 2차 전환 버튼
11. **Footer** - 연락처, 법적 고지, 소셜 링크

## Tech Stack

- **Next.js 15+** App Router + TypeScript + Tailwind CSS
- **ShadCN UI**: `button card accordion badge avatar separator input`

## Implementation Flow

### 1. SEO Metadata
```typescript
export const metadata: Metadata = {
  title: 'SEO Title | Brand',
  description: 'Compelling description',
  keywords: ['keyword1', 'keyword2'],
  openGraph: { title: '...', description: '...', images: ['/og.jpg'] },
}
```

### 2. Component Structure
Header → Hero(Title+CTA+SocialProof) → Media → Benefits(Card) → Testimonials(Avatar+Card) → FAQ(Accordion) → FinalCTA(Button+Card) → Footer(Separator)

### 3. Project Structure
```
app/          layout.tsx, page.tsx, globals.css
components/   Header, Hero, MediaSection, Benefits, Testimonials, FAQ, FinalCTA, Footer
public/       images/
```

### 4. Responsive + Performance + Accessibility
- Mobile-first: `sm:` `md:` `lg:` `xl:`, min touch 44px, base font 16px+
- Next.js Image (`priority` for hero), lazy load below-fold
- Semantic HTML5, ARIA labels, keyboard nav, WCAG AA contrast, alt text

## Validation Checklist

- [ ] 11 elements 전부 포함
- [ ] Next.js 15+ App Router + TypeScript
- [ ] ShadCN UI 컴포넌트 사용
- [ ] SEO metadata 설정
- [ ] 반응형, 접근성, 성능 최적화

## Best Practices

- **Content**: 혜택 중심 카피, 액션 지향 CTA, 구체적 수치/통계
- **Design**: 시각적 위계, 일관된 컬러, 충분한 여백, 모바일 우선
- **SEO**: H1→H2→H3 구조, alt text, 빠른 로딩, 키워드 자연 배치
- **Conversion**: CTA는 hero+하단 최소 2곳, 대비색, 신뢰 신호 강조

## References

- `references/11-essential-elements.md` - 11 요소 상세 설명
- `references/component-examples.md` - ShadCN 컴포넌트 코드 예제
