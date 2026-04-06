---
name: workthrough
description: Automatically document all development work in a structured workthrough format after completing any development task.
license: MIT
---

# Workthrough

Auto-generate structured documentation after any development work (features, bug fixes, refactoring, config changes, dependency updates).

## Document Structure

Save to: `workthrough/YYYY-MM-DD-brief-description.md` (create directory if needed)

```markdown
# [Clear Descriptive Title]

## Overview
2-3 sentence summary of what was accomplished and why.

## Context
- Problem/requirement being addressed
- Relevant background

## Changes Made

### 1. [Major Change]
- Specific modifications
- File: `path/to/file.tsx`

### 2. [Additional Changes]
- Dependencies: `package@version`
- Config updates: `config-file.json`

## Code Examples
` ``typescript
// src/path/to/file.tsx
const example = () => { /* key changes */ }
` ``

## Verification Results
` ``bash
> build output
Exit code: 0
` ``

## Next Steps
- Follow-up tasks
- Known limitations
```

## Guidelines

1. **Capture context**: problem, approach, decisions made
2. **Document all changes**: file paths, before/after for significant changes, dependencies
3. **Include verification**: build output, test results, exit codes
4. **Be concise**: clear formatting, no verbose descriptions, concrete examples
5. **Auto-trigger**: run at end of every development session
