---
name: codex-claude-loop
description: Orchestrates a dual-AI engineering loop where Claude Code plans and implements, while Codex validates and reviews, with continuous feedback for optimal code quality
---

# Codex-Claude Engineering Loop

## Workflow

```
Plan (Claude) -> Validate (Codex) -> Feedback ->
Implement (Claude) -> Review (Codex) ->
Fix (Claude) -> Re-validate (Codex) -> Repeat until done
```

- **Claude Code**: Architecture, planning, execution, fixes
- **Codex**: Validation, code review, quality assurance

## Phase 1: Plan (Claude)

Create detailed implementation plan with steps, assumptions, potential issues.

## Phase 2: Validate Plan (Codex)

1. Ask user via `AskUserQuestion`: model (`gpt-5` or `gpt-5-codex`) and reasoning effort (`low`/`medium`/`high`)
2. Send plan to Codex:
```bash
echo "Review this plan for logic errors, edge cases, architecture flaws, security:
[plan]" | codex exec -m <model> --config model_reasoning_effort="<effort>" --sandbox read-only
```

## Phase 3: Feedback Loop

If issues found: summarize, refine plan, ask user whether to re-validate or proceed. Repeat Phase 2 as needed.

## Phase 4: Implement (Claude)

Execute validated plan using Edit/Write/Read tools. Break into steps with error handling.

## Phase 5: Cross-Review (Codex)

After every change, send to Codex for bug detection, performance, best practices, security review.
- Critical issues: fix immediately
- Architectural changes: discuss with user

## Phase 6: Iterate

1. Apply fixes, re-send to Codex for significant changes
2. Use `codex exec resume --last` to continue sessions (inherits all original settings):
```bash
echo "Review updated implementation" | codex exec resume --last
```

## Command Reference

| Phase | Command | Purpose |
|-------|---------|---------|
| Validate | `echo "plan" \| codex exec --sandbox read-only` | Check logic |
| Implement | Claude Edit/Write/Read tools | Code changes |
| Review | `echo "review" \| codex exec --sandbox read-only` | Validate implementation |
| Continue | `echo "next" \| codex exec resume --last` | Continue session |
| Re-validate | `echo "verify" \| codex exec resume --last` | Re-check fixes |

## Error Handling

- Stop on non-zero exit codes; summarize and ask user via `AskUserQuestion`
- Confirm with user before: significant architecture changes, multi-file changes, breaking changes
- Evaluate Codex warnings by severity before proceeding
