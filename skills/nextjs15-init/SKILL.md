---
name: nextjs15-init
description: Use when user wants to create a new Next.js 15 project (Todo/Blog/Dashboard/E-commerce/Custom domain) with App Router, ShadCN, Zustand, Tanstack Query, and modern Next.js stack
---

# NextJS 15 Init Skill

도메인 기반 Next.js 15 프로젝트를 App Router로 자동 생성합니다.

## Task Instructions

**대화형 스킬** - 아래 순서대로 진행합니다.

### Step 1: 사용자 입력 수집

다음을 질문하세요:

**1. 도메인 선택 (A-E)**

| 도메인 | 필드 | 핵심 기능 | API |
|--------|------|-----------|-----|
| A) Todo | title, description, completed, createdAt, updatedAt | CRUD, 필터, 토글 | /api/todos |
| B) Blog | title, content, excerpt, slug, published, createdAt | CRUD, 검색, 목록/상세 | /api/posts |
| C) Dashboard | 통계, 차트, 사용자 관리 | 시각화, 테이블, 페이지네이션 | /api/analytics, /api/users |
| D) E-commerce | name, price, description, images, stock, category | 상품목록, 장바구니, 주문 | /api/products, /api/cart |
| E) Custom | 사용자 정의 (엔티티명, 필드명:타입) | 기본 CRUD | /api/[entity] |

- 지원 타입(Custom): string, number, boolean, Date (createdAt/updatedAt 자동추가)

**2. 프로젝트 정보**
- 폴더명 (기본: [도메인]-app)
- 프로젝트명 (기본: 폴더명, package.json name)

**3. 스택 프리셋 (A-D)**

| 프리셋 | ShadCN | Zustand | Tanstack Query | RHF+Zod | Drizzle | Better Auth | Framer Motion | Lucide |
|--------|--------|---------|----------------|---------|---------|-------------|---------------|--------|
| A) Essential (권장) | O | O | X | O | X | X | X | O |
| B) Minimal | X | X | X | X | X | X | X | X |
| C) Full Stack | O | O | O | O | O | O | O | O |
| D) Custom | 개별 선택 | | | | | | | |

기본 포함: Next.js 15 App Router, TypeScript, Tailwind CSS, ESLint

### Step 2: 프로젝트 생성

1. `npx create-next-app@latest [폴더명] --typescript --tailwind --app --use-npm`
2. 패키지 설치
3. App Router 구조 생성: `app/`, `components/`, `lib/` (stores, api, validations)
4. 도메인별 보일러플레이트: API Routes(CRUD), Pages, Components, Zustand Store, Zod Schema
5. ShadCN 설치 (Essential 이상): `npx shadcn@latest init && npx shadcn@latest add button card input form table`

### Step 3: 검증 (CRITICAL - 필수)

lint + build 모두 성공해야 완료:

1. `npm run lint` → 0 errors
2. `npm run build` → 빌드 성공

주요 점검:
- `@/` alias import, TypeScript 타입 명시
- `'use client'` 지시어 (React Hooks 사용 파일)
- Server/Client Component 분리
- ESLint: 미사용 변수/import 제거

오류 발견 시 수정 후 재검증 반복.

### Step 4: 완료 안내

검증 통과 후:
- 프로젝트 정보 요약 (폴더명, 도메인, 스택, 생성 파일 수)
- 실행: `cd [폴더명] && npm run dev` → http://localhost:3000
- 도메인별 다음 단계 제안, Vercel 배포 안내

## Core Principles

- App Router 기반, TypeScript Strict Mode
- ShadCN/ui 컴포넌트, Zustand(클라이언트) + Tanstack Query(서버) 상태관리
- React Hook Form + Zod 폼 검증

## Reference Files

[references/setup-guide.md](references/setup-guide.md) - 상세 가이드 (도메인별 CRUD, 선택 옵션 등)
