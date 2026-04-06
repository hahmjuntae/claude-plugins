---
name: landing-page-guide-v2
description: Create distinctive, high-converting landing pages combining proven 11-element conversion framework with exceptional design. Next.js 15+, ShadCN UI, avoiding generic AI aesthetics.
---

# Landing Page Guide V2

Distinctive, high-converting landing pages = proven conversion elements + exceptional design quality.

## When to Use

User requests: landing pages, marketing pages, product pages, promotional websites needing both conversion optimization AND memorable visual design.

## Design Thinking (Before Coding)

### 1. Understand Context
- Purpose, target audience, brand personality, industry norms
- Differentiation: What ONE thing will visitors remember?

### 2. Choose Aesthetic Direction (commit fully to ONE)

| Direction | Characteristics | Best For |
|-----------|----------------|----------|
| Minimalist & Refined | Clean, whitespace, monochromatic, subtle interactions | Luxury, premium SaaS |
| Bold & Maximalist | Rich layers, animations, gradients, vibrant colors | Creative, entertainment |
| Retro-Futuristic | Geometric, neon, glitch effects, monospace fonts | Gaming, tech startups |
| Organic & Natural | Soft shapes, earth tones, smooth motion, rounded | Wellness, food |
| Editorial & Magazine | Strong typography, asymmetric, large imagery | Content, media |
| Brutalist & Raw | Unconventional, system fonts, high contrast, minimal animation | Art, fashion |

### 3. Define Design System

**Typography**: Distinctive display font (NEVER Inter/Roboto/Arial) + refined body font. Scale: H1 4rem+ with dramatic hierarchy. Line height: Display 1.1-1.2, Body 1.6-1.8.

**Color**: Dominant (60%) + Accent for CTAs (10%) + Neutral (30%). Define as CSS variables. Background: gradient/texture/pattern (not plain white).

**Motion**: Staggered hero reveals (animation-delay), scroll-triggered section fades, hover states that surprise. Prefer CSS `transform`/`opacity` (GPU-accelerated). Always support `prefers-reduced-motion`.

**Layout**: Break grids. Asymmetry, overlapping, diagonal flow, Z-axis depth with shadows/blur.

## 11 Essential Elements (All Required)

| # | Element | Functional | Design Excellence |
|---|---------|-----------|-------------------|
| 1 | URL | SEO keywords | N/A |
| 2 | Logo/Header | Brand identity top-left | Animated load, sticky with backdrop blur transition |
| 3 | Hero Title | Value proposition + keywords | MASSIVE (4-6rem+), display font, gradient/outlined text, staggered fade-in |
| 4 | Primary CTA | Hero call-to-action | Impossible to miss: pill/geometric shape, micro-interactions, entrance animation |
| 5 | Social Proof | Reviews, stats | Animated count-up, overlapping avatars, custom star styling |
| 6 | Media | Product visuals | Device mockups, parallax, 3D tilt, reveal animations (NO placeholders) |
| 7 | Benefits | 3-6 features + icons | Custom icons, glassmorphism/gradient cards, staggered scroll animation, asymmetric layout |
| 8 | Testimonials | 4-6 reviews + photos | Gradient-border avatars, masonry/carousel, hover lift, branded quote marks |
| 9 | FAQ | 5-10 questions accordion | Smooth expand/collapse, custom chevrons, generous padding |
| 10 | Final CTA | Bottom conversion | Full-width dramatic section, bigger than hero CTA, urgency elements |
| 11 | Footer | Contact + legal | Multi-column, social hover effects, newsletter input, distinct background |

## Tech Stack

- **Next.js 15+** App Router + TypeScript + Tailwind CSS
- **ShadCN UI**: Install `button card accordion badge avatar separator input`. Customize heavily (modify styles, add variants, create wrapper components).
- **Framer Motion** (optional) for advanced animations

## Implementation Flow

1. **Design first**: Define fonts, colors, motion, layout in comments before coding
2. **CSS variables**: Set up design system in `globals.css` + `tailwind.config.ts`
3. **SEO metadata**: `layout.tsx` with title, description, keywords, OpenGraph
4. **Build sections**: Header → Hero → Media → Benefits → Testimonials → FAQ → FinalCTA → Footer
5. **Animations**: Staggered entrance + scroll reveals + hover states
6. **Responsive**: Mobile-first, all breakpoints (sm/md/lg/xl), 44px min touch target
7. **Performance**: Next.js Image with `priority` for hero, lazy load below-fold, `font-display: swap`
8. **Accessibility**: Semantic HTML5, ARIA labels, keyboard nav, WCAG AA contrast, alt text

## AVOID Generic AI Aesthetics

**DON'T**: Inter/Roboto fonts, purple gradients on white, perfectly symmetric layouts, generic line icons, default yellow stars, plain white backgrounds, cookie-cutter 3-column grids.

**DO**: Distinctive fonts per project, unique color palettes, asymmetric layouts, characterful icons, textured/gradient backgrounds, varied section layouts.

## Validation Checklist

- [ ] Aesthetic direction chosen and consistent throughout
- [ ] Distinctive typography (NOT generic fonts), dramatic scale hierarchy
- [ ] CSS variable color system, non-plain backgrounds
- [ ] All 11 elements present with design excellence
- [ ] ShadCN components heavily customized
- [ ] Responsive, accessible (WCAG AA), performant
- [ ] Staggered animations + reduced motion support
- [ ] No placeholder content, no generic AI look

## References

- `references/11-essential-elements.md` - Detailed element explanations
- `references/component-examples.md` - Production-ready ShadCN component code
