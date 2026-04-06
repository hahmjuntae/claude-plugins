---
name: codex-claude-cursor-loop
description: Orchestrates a triple-AI engineering loop where Claude plans, Codex validates logic and reviews code, and Cursor implements, with continuous feedback for optimal code quality
---

# Codex-Claude-Cursor Engineering Loop

3-way sequential validation: Claude(계획/최종검토) → Codex(검증) → Cursor(구현) → 반복.

## Phase 1: Planning (Claude)

상세 계획 작성. 구현 단계 분리, 가정/잠재 이슈 문서화.

## Phase 2: Plan Validation (Codex)

사용자에게 모델(`gpt-5`/`gpt-5-codex`)과 reasoning effort(`low`/`medium`/`high`) 확인 후:

```bash
echo "Review this implementation plan and identify issues:
[plan]
Check for: logic errors, missing edge cases, architecture flaws, security concerns" | codex exec -m <model> --config model_reasoning_effort="<effort>" --sandbox read-only
```

## Phase 3: Plan Refinement

Codex 이슈 발견 시 → 사용자에게 요약 → 계획 수정 → 사용자 확인("재검증 or 구현 진행?") → 필요시 Phase 2 반복.

## Phase 4: Implementation (Cursor Agent)

사용자에게 확인: 새 세션 / 기존 세션 재개 (`cursor-agent ls`), 모델 선택.

**새 세션:**
```bash
cursor-agent --model "<model>" -p --force "Implement this plan: [validated plan]"
```

**세션 재개:**
```bash
cursor-agent --resume="<session-id>" -p --force "Continue: [plan]"
```

세션 ID 저장 필수 — 이후 모든 Cursor 호출에 재사용.

## Phase 5: Code Review (Codex)

```bash
echo "Review implementation for: bugs, performance, security, best practices, code quality
Files: [list] Summary: [what Cursor did]" | codex exec --sandbox read-only
```

## Phase 6: Final Review (Claude)

Read 도구로 구현 코드 확인. Codex 리뷰 + 실제 구현 분석. 원래 계획 대비 검증, 추가 우려사항 식별.

## Phase 7: Iterative Fix Loop

이슈 발견 시:
1. Claude가 Codex+자체 리뷰 기반 수정 계획 작성
2. Cursor에 **동일 세션**으로 수정 전달: `cursor-agent --resume="<id>" -p --force "Fix: [plan]"`
3. Phase 5부터 반복 (모든 검증 통과까지)

동일 Codex 모델, 동일 Cursor 세션 유지.

## Command Reference

| Phase | Who | Command |
|-------|-----|---------|
| Plan | Claude | 분석 도구 활용 |
| Validate | Codex | `echo "plan" \| codex exec -m <model> --config ... --sandbox read-only` |
| Implement | Cursor | `cursor-agent [--resume="<id>"] --model "<m>" -p --force "prompt"` |
| Review | Codex | `echo "review" \| codex exec --sandbox read-only` |
| Final | Claude | Read 도구로 코드 확인 |

## Error Handling

- Cursor 출력 오류 모니터링
- 중대 아키텍처 변경, 다수 파일 영향, 브레이킹 체인지 시 `AskUserQuestion`으로 사용자 확인
- Claude가 수정 계획 작성 후 Cursor에 전달

## The Loop

```
Plan(Claude) → Validate(Codex) → [이슈→수정→반복]
  → Implement(Cursor) → Review(Codex) → Final(Claude)
    → [이슈→Fix Plan(Claude)→Cursor→Phase 5 반복]
      → All passed → Done
```
