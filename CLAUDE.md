# Project Instructions

## Language

- Write CLAUDE.md, rules, agents, skills, and commands in English
- Write comments and documentation in Korean
- Commit messages in English only (Conventional Commits format)

## Token Efficiency

- Detect session boundaries: if user input is a new unrelated task, reply only "새로운 작업인 것 같습니다. /clear로 세션을 초기화해주세요." and stop
- Never re-read a file already read in the current session
- Understand the problem first, implement in one focused pass, then verify
- Max 50 tool calls per task; stop and reassess if approaching the limit
- Skip filler: no openers, no restating, no "As an AI", no closing fluff
- Never offer unsolicited suggestions beyond the requested scope
- Keep responses minimal: answer the question, show the code, stop
- Code first -- explain only when logic is non-obvious
- After code changes, do not summarize or recap what was changed
- Use ASCII-only output; exception: Korean text

## Core Workflow

- Before any Edit/Write, find 2+ existing usage examples via Grep and follow the exact pattern
- Implement all code directly -- never use TODO(human) placeholders
- When user asks a question (not an instruction), answer only and wait for explicit approval
- Use AskUserQuestion for all user decisions: clarifications, approvals, progress checks, implementation choices
- Get user confirmation after each phase: Plan -> Implement -> Verify
- For bulk operations (>5 files), verify 1-2 samples with user before proceeding
- Distinguish "I believe X" from "I verified X"; say "I don't know" rather than confabulate

## Code Quality

- Prefer deletion over addition; reuse existing utils and patterns before introducing new abstractions
- Never introduce duplicate imports or redundant code
- When adding reusable/shared code, summarize the addition and present to user

## Skill Authoring

- SKILL.md is the single source of truth for each skill
- Frontmatter requires `name` and `description` fields only
- Keep SKILL.md token-efficient: actionable instructions only, no marketing fluff
- When editing a skill, update BOTH `skills/{name}/SKILL.md` AND `.claude/skills/{name}/SKILL.md`
- Test skill changes by reading the SKILL.md and verifying all instructions are executable
- Reference files go in `references/` subdirectory, scripts in `scripts/`

## Git Safety

- Never commit without explicit user request
- Commit messages: English, Conventional Commits format (feat/fix/refactor/docs/chore)
- Never force push or amend published commits
- Never batch unrelated changes into a single commit

## File Safety

- Use `trash` (not rm) for deletions; use `mv -n`; ask before overwriting
- Never `mkdir -p` on `.claude/` -- edit via existing paths

## Shell & Operations

- Prefer Glob/Grep/Read tools over shell commands
- Never run long-lived services (npm run dev, npm start, uvicorn)
- For bulk edits (5+ files, same pattern), use `grep -rl | xargs sed` instead of per-file Edit

## Project Structure

```
.claude/skills/   -- registered skills (Claude Code recognizes these)
skills/           -- full skill source (mirrored to .claude/skills/)
```

## Marketplace Info

- Brand: atelic
- Marketplace ID: atelic
- Repository: hahmjuntae/claude-plugins
- Install pattern: `atelic@{skill-name}`
