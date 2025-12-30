# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a documentation repository for managing deep research on Sui and related Web3 projects (Walrus, Scallop, Cetus, etc.). Research is conducted in English using LLMs (ChatGPT, Grok, Gemini, etc.), stored with metadata, and translated into multiple languages.

**Key principle**: All research files are stored flat in `deep-research/` to avoid decision fatigue about directory placement. Classification is handled entirely through `tags:` in YAML front matter.

## Architecture

### Directory Structure

```
deep-research-sui/
├── deep-research/           # English master files (flat structure)
│   └── *.md                # Research outputs with YAML front matter
├── translations/           # Multi-language translations
│   ├── ja/                # Japanese translations
│   ├── zh/                # Chinese translations
│   ├── ko/                # Korean translations
│   ├── de/                # German translations
│   ├── fr/                # French translations
│   ├── es/                # Spanish translations
│   ├── ar/                # Arabic translations
│   └── ru/                # Russian translations
├── docs/                  # English documentation
├── doc-ja/                # Japanese documentation
└── _templates/            # Shared templates (planned)
```

### File Format Standards

#### Research Files (`deep-research/*.md`)

Research files combine YAML front matter with markdown content in a single file:

```markdown
---
title: Sui DeFi Overview
platform: ChatGPT DeepResearch (GPT-4o)
date: 2025-12-30
url: https://chat.openai.com/share/xxx123
tags: [defi, user, ecosystem]
---

[PROMPT]

```markdown
Please investigate...
```

---

# [OUTPUT]

```markdown
[Full output content]
```
```

#### Translation Files (`translations/{lang}/*.md`)

Translation files use simplified metadata:

```markdown
---
title: Sui DeFi概要
translation_tool: ChatGPT (GPT-5.2)
translation_prompt: ja/prompts/translation-v1.md
---

## 概要

...
```

### Tag System

All classification is done through `tags:` in YAML front matter, using multiple axes:

| Axis | Examples |
|------|----------|
| Content type | `project`, `ecosystem`, `dev-guide` |
| Technology | `sui`, `oracle`, `move` |
| Use case | `oracle`, `nft`, `defi`, `wallet`, `ai` |
| Audience | `builder`, `investor`, `user` |

### Metadata Management

The following metadata is **NOT included** in files because it's managed by Git:

- `language:` (determined by directory structure)
- `translator:` (available in Git log)
- `date_translated:` (available in Git log)
- `source_file:` (translation files match original filenames)

## Research Prompt Guidelines

When creating new research prompts, follow the guidelines in `docs/research-prompt-guide.md`:

1. **Write prompts in English** - LLMs are optimized for English
2. **Specify output format** - Always request Markdown with clear headings
3. **Define scope and restrictions** - Set date ranges, language filters, and content boundaries
4. **Keep prompts concise** - Short, clear sentences work best
5. **Design clear focus areas** - Use specific questions, not vague topics
6. **Specify trusted sources** - List official docs, GitHub repos, blogs, Twitter accounts
7. **Define target audience** - Specify perspective (e.g., "Web3 developers")
8. **Split tasks** - Separate research, writing, and translation into different prompts

## Scaling Strategy

The flat structure in `deep-research/` is intentional for the initial phase. Directory organization will be introduced when:

- File count exceeds 100
- Specific categories develop into series (e.g., multiple Walrus-related files)

When this happens, create subdirectories like `deep-research/walrus/` based on tags.

## Future Automation

The following are planned but not yet implemented:

- Tag-based indexing tools (Node.js/Python)
- Automated translation pipeline using Claude Code Hooks
- Integration of static processing and LLM processing for translations
