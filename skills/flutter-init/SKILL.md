---
name: flutter-init
description: Use when user wants to create a new Flutter project (Todo/Habit/Note/Expense/Custom domain) with Clean Architecture, Riverpod 3.0, Drift, and modern Flutter stack
---

# Flutter Init Skill

도메인 기반 Flutter 프로젝트를 Clean Architecture로 자동 생성합니다.

## Task Instructions

**대화형 스킬** - 아래 순서대로 진행합니다.

### Step 1: 사용자 입력 수집

다음을 질문하세요:

**1. 도메인 선택 (A-E)**

| 도메인 | 필드 | 핵심 기능 |
|--------|------|-----------|
| A) Todo | title, description, isCompleted, createdAt, completedAt | CRUD, 필터(전체/진행중/완료), 토글 |
| B) Habit | name, description, frequency, streak, lastCompletedAt, goal, isActive | CRUD, 연속기록, 달성률 |
| C) Note | title, content, tags, isPinned, createdAt, updatedAt | CRUD, 태그필터, 고정, 검색 |
| D) Expense | amount, category, description, date, paymentMethod | CRUD, 카테고리 집계, 월별 통계 |
| E) Custom | 사용자 정의 (엔티티명, 필드명:타입) | 기본 CRUD |

- 지원 타입(Custom): String, int, double, bool, DateTime (createdAt/updatedAt 자동추가)

**2. 프로젝트 정보**
- 폴더명 (기본: [도메인]_app)
- 패키지명 (기본: 폴더명과 동일, pubspec.yaml name 및 import에 사용)
- 조직명 (기본: com.example)

**3. 스택 프리셋 (A-D)**

| 프리셋 | GoRouter | SharedPref | FPDart | Google Fonts | FluentUI Icons | Responsive | Auth |
|--------|----------|------------|--------|-------------|----------------|------------|------|
| A) Essential (권장) | O | O | O | O | O | X | X |
| B) Minimal | X | O | X | X | O | X | X |
| C) Full Stack | O | O | O | O | O | O | O |
| D) Custom | 개별 선택 | | | | | | |

### Step 2: 프로젝트 생성

1. `flutter create --platforms android,ios --android-language kotlin --org [조직명] [폴더명]`
2. pubspec.yaml 업데이트 후 `flutter pub get`
3. Clean Architecture 폴더 구조 생성 (core, data, domain, presentation)
4. 도메인별 보일러플레이트: Entity(Freezed), Drift DB, Repository, Providers(Riverpod 3.0), Screens(List/Detail/Form)
5. Android 설정: `build.gradle.kts`에 core library desugaring 추가
6. `dart run build_runner build --delete-conflicting-outputs`

### Step 3: 검증 (CRITICAL - 필수)

`flutter analyze` 실행 후 모든 error 수정 반복. 주요 점검:

- **Freezed 3.0**: `sealed class` 사용 (NOT `class ... with _$`)
- **Riverpod 3.0**: `Notifier`/`NotifierProvider` 사용 (NOT StateNotifier)
- **import**: 모든 경로를 `package:` 형식으로
- **CardTheme** → `CardThemeData` (deprecated)
- FluentUI 아이콘명 존재 확인, null safety, switch expression

목표: `flutter analyze` 결과 error 0건 (info만 허용)

### Step 4: 완료 안내

검증 통과 후:
- 프로젝트 정보 요약 (폴더명, 패키지명, 도메인, 스택, 생성 파일 수)
- 실행: `cd [폴더명] && flutter run`
- 도메인별 다음 단계 제안

## Core Principles

- Repository 패턴으로 data/domain 분리
- Riverpod 3.x DI, Freezed 불변 모델, Easy Localization i18n
- FluentUI Icons, 영어/한국어 다국어

## Reference Files

[references/setup-guide.md](references/setup-guide.md) - 상세 가이드 (도메인별 CRUD, 선택 옵션 등)
