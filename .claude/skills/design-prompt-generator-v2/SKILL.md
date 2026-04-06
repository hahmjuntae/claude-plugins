---
name: design-prompt-generator-v2
description: 7-step hierarchical design prompt generator for AI web dev tools (Lovable, Cursor, Bolt). Triggers on "디자인 프롬프트", "웹 디자인", "Lovable 프롬프트", "랜딩페이지 만들어줘", or AI web builder prompt requests.
---

# Design Prompt Generator v2

AI 웹 개발 도구(Lovable, Cursor, Bolt)를 위한 7단계 계층적 디자인 프롬프트 생성기.

## 7-Step Framework

| Step | 내용 | 핵심 |
|------|------|------|
| 1. Domain Research | 업종 UX 패턴, 경쟁사 | Top 3 앱, 기대 UX, 신뢰 신호, 페인포인트 |
| 2. User Journey | 사용자 흐름, 전환 포인트 | [진입]→[발견]→[평가]→[결정]→[행동]→[유지] |
| 3. Emotional Design | 감성 키워드, 무드 컨셉 | 감정별 시각/컬러/타이포/이미지 매핑 |
| 4. Identity & Goal | 브랜드 정체성, 목표 | Name, One-liner, Positioning, Goals, Personality |
| 5. Design System | 컬러, 타이포, 컴포넌트 | 10색 시스템, 폰트 스케일, 스페이싱, 컴포넌트 스타일 |
| 6. Component Specs | 핵심 컴포넌트 상세 | Purpose, Contents, States, Variants, Responsive |
| 7. Micro-interactions | 애니메이션, 인터랙션 | Entrance/Feedback/StateChange/Navigation/Delight |

## Step 1: Domain Research

도메인별 패턴 참고:

| 도메인 | 패턴 | 신뢰 신호 | 핵심 흐름 |
|--------|------|-----------|-----------|
| Pet Services | 프로필카드, 예약캘린더 | 인증뱃지, 리뷰, 보험 | 검색→조회→예약→결제 |
| SaaS | 기능비교, 요금제, 데모CTA | 로고, 후기, 보안뱃지 | 학습→체험→구독 |
| E-commerce | 그리드, 필터, 장바구니 | 리뷰, 반품정책 | 탐색→담기→결제 |
| Education | 강의카드, 진도추적 | 인증서, 수강생수, 평점 | 탐색→등록→학습 |
| Healthcare | 의료진검색, 예약슬롯 | 면허, 병원소속 | 찾기→예약→상담 |
| Fintech | 대시보드, 거래내역 | 암호화뱃지, 규제준수 | 연결→모니터링→실행 |
| Food Delivery | 레스토랑카드, 실시간추적 | 평점, 배달시간예측 | 탐색→주문→추적 |
| Marketplace | 판매자프로필, 리스팅 | 인증, 거래내역 | 검색→연락→거래 |

## Step 2: User Journey

각 단계별 정의:
```
Journey Stage → User Goal / Key Info / Friction / Solution
```

## Step 3: Emotional Design

| 감정 | 시각 | 컬러 | 타이포 |
|------|------|------|--------|
| Trust | 깔끔, 정돈 | 블루, 그린 | 안정적 세리프/산스 |
| Warmth | 부드러운 모서리 | 웜 옐로우, 오렌지 | 둥글고 친근 |
| Energy | 강한 대비 | 비비드 레드 | 강렬 임팩트 |
| Calm | 여백, 미니멀 | 소프트 블루/뉴트럴 | 가벼운 웨이트 |
| Luxury | 다크, 골드 | 블랙, 골드, 딥퍼플 | 우아한 세리프 |
| Playful | 비대칭, 애니메이션 | 밝고 다양 | 퀴키 커스텀 |
| Professional | 그리드, 구조적 | 네이비, 그레이 | 클래식 산스 |

감정 비율 정의: 예) 60% Trust, 30% Warmth, 10% Energy

## Step 4: Identity & Goal

```
Service Name / One-liner / Category / Positioning / Primary Goal / Secondary Goal / Brand Personality (형용사 3개)
```

## Step 5: Design System

```
Colors: Primary, Secondary, Accent, Background, Surface, Text Primary/Muted, Success/Warning/Error
Typography: Headings [폰트/웨이트], Body [폰트/행간], Scale [base px, ratio]
Spacing: Base unit, Border radius, Shadow, Grid, Container max-width
Components: Buttons [shape/padding/hover], Cards [radius/shadow], Inputs [border/focus]
```

## Step 6: Component Specs

```
[Component] → Purpose / Contents / States (Default,Hover,Active,Disabled,Loading) / Variants / Responsive
```

공통: Profile/Card, Search/Filter, Booking/Action, Review/Trust, Status/Progress

## Step 7: Micro-interactions

| 타입 | 목적 | Duration | Easing |
|------|------|----------|--------|
| Entrance | 새 콘텐츠 주목 | 400-600ms | ease-out + stagger |
| Feedback | 액션 확인 | 150-200ms | ease-out |
| State Change | 전환 표시 | 250-350ms | ease-in-out |
| Navigation | 뷰 간 가이드 | 250-350ms | ease-in-out |
| Delight | 기억에 남는 순간 | 400-600ms | ease-out |

## Output Format

```markdown
# [Service Name] Design Prompt
## Domain Context → User Journey → Emotional Direction
## Design Specifications
### Identity / Design System / Key Components / Interactions
## Implementation Prompt (AI 도구용 복사-붙여넣기)
## Iterative Refinement Prompts (단계별 개선)
```

## User Input

**필수**: 서비스 주제/업종, 서비스 이름 (없으면 제안)
**선택**: 타겟 사용자, 경쟁사, 분위기/감성, 필수 기능, 페이지 종류

*최소 입력 시 도메인 기본값 사용, 가정 명시.*

## Quality Checklist

- [ ] 도메인 특화 UX 패턴 반영
- [ ] 사용자 여정이 구조에 반영
- [ ] 감정 키워드 → 시각 스펙 변환
- [ ] 컬러 시스템 완성 (용도 포함)
- [ ] 핵심 컴포넌트 상태 정의
- [ ] 마이크로 인터랙션 명시
- [ ] 모바일 반응형 고려
- [ ] 구현 프롬프트 복사-붙여넣기 가능
