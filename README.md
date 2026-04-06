# Claude Code Skills

A collection of 21 custom skills for Claude Code to boost developer productivity.

## Installation

```bash
# Add marketplace
/plugin marketplace add hahmjuntae/claude-plugins

# Install a skill
/plugin marketplace install atelic@{skill-name}

# List installed skills
/plugin list

# Update a skill
/plugin update atelic@{skill-name}

# Remove marketplace
/plugin marketplace remove atelic
```

## Skills

### Project Scaffolding

| Skill | Description | Install |
|-------|-------------|---------|
| [flutter-init](./skills/flutter-init/) | Flutter Clean Architecture project scaffolding | `atelic@flutter-init` |
| [nextjs15-init](./skills/nextjs15-init/) | Next.js 15 App Router project scaffolding | `atelic@nextjs15-init` |

### Design & Landing Pages

| Skill | Description | Install |
|-------|-------------|---------|
| [landing-page-guide-v2](./skills/landing-page-guide-v2/) | High-conversion landing page guide | `atelic@landing-page-guide-v2` |
| [landing-page-guide](./skills/landing-page-guide/) | Landing page 11 essential elements guide | `atelic@landing-page-guide` |
| [frontend-design](./skills/frontend-design/) | Production-grade frontend UI generation | `atelic@frontend-design` |
| [design-prompt-generator-v2](./skills/design-prompt-generator-v2/) | 7-step design prompt generator for AI web builders | `atelic@design-prompt-generator-v2` |

### Card News & Images

| Skill | Description | Install |
|-------|-------------|---------|
| [card-news-generator-v2](./skills/card-news-generator-v2/) | Card news with background image support | `atelic@card-news-generator-v2` |
| [card-news-generator](./skills/card-news-generator/) | 600x600 Instagram-style card news generator | `atelic@card-news-generator` |
| [midjourney-cardnews-bg](./skills/midjourney-cardnews-bg/) | Midjourney background prompt generator | `atelic@midjourney-cardnews-bg` |
| [gemini-logo-remover](./skills/gemini-logo-remover/) | OpenCV watermark/logo removal | `atelic@gemini-logo-remover` |

### Prompt & Automation

| Skill | Description | Install |
|-------|-------------|---------|
| [prompt-enhancer](./skills/prompt-enhancer/) | Context-aware prompt enhancement | `atelic@prompt-enhancer` |
| [meta-prompt-generator](./skills/meta-prompt-generator/) | Structured slash command generator | `atelic@meta-prompt-generator` |
| [code-prompt-coach](./skills/code-prompt-coach/) | Session log analysis for prompt coaching | `atelic@code-prompt-coach` |

### AI Engineering Loops

| Skill | Description | Install |
|-------|-------------|---------|
| [codex-claude-cursor-loop](./skills/codex-claude-cursor-loop/) | Claude + Codex + Cursor triple AI loop | `atelic@codex-claude-cursor-loop` |
| [codex-claude-loop](./skills/codex-claude-loop/) | Claude + Codex dual AI loop | `atelic@codex-claude-loop` |
| [codex](./skills/codex/) | OpenAI Codex CLI wrapper | `atelic@codex` |

### Documentation & Utilities

| Skill | Description | Install |
|-------|-------------|---------|
| [workthrough-v2](./skills/workthrough-v2/) | Dev work documentation + VitePress serving | `atelic@workthrough-v2` |
| [workthrough](./skills/workthrough/) | Automatic dev work documentation | `atelic@workthrough` |
| [code-changelog](./skills/code-changelog/) | Code change logging + HTML viewer | `atelic@code-changelog` |
| [web-to-markdown](./skills/web-to-markdown/) | Web page to markdown conversion | `atelic@web-to-markdown` |
| [web-search](./skills/web-search/) | DuckDuckGo web/news/image search | `atelic@web-search` |

## License

MIT
