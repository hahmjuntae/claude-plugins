---
name: codex
description: Use when the user asks to run Codex CLI (codex exec, codex resume) or references OpenAI Codex for code analysis, refactoring, or automated editing
---

# Codex Skill

## Running a Task

1. Ask user via `AskUserQuestion`: model (`gpt-5`/`gpt-5-codex`) and reasoning (`low`/`medium`/`high`)
2. Select sandbox (default `read-only` unless edits/network needed)
3. Assemble: `-m <MODEL> --config model_reasoning_effort="<effort>" --sandbox <mode>` + optional `--full-auto`, `-C <DIR>`, `--skip-git-repo-check`
4. Run, capture output, summarize

**Resume**: `echo "prompt" | codex exec resume --last` -- NO flags; inherits all original settings.

## Sandbox Modes

| Use case | Mode | Flags |
|----------|------|-------|
| Review/analysis | `read-only` | `--sandbox read-only` |
| Local edits | `workspace-write` | `--sandbox workspace-write --full-auto` |
| Network access | `danger-full-access` | `--sandbox danger-full-access --full-auto` |
| Resume | Inherited | `echo "prompt" \| codex exec resume --last` |

## Follow-Up

- After every command: `AskUserQuestion` for next steps / resume decision
- Restate settings when proposing follow-ups

## Error Handling

- Non-zero exit: stop, report, request direction
- High-impact flags (`--full-auto`, `danger-full-access`, `--skip-git-repo-check`): ask permission first
- Warnings/partial results: summarize and ask how to adjust
