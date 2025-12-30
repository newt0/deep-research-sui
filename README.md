# deep-research-sui

## ✅ Overview

| Item         | Details                                                                          |
| ------------ | -------------------------------------------------------------------------------- |
| Repository   | `deep-research-sui`                                                             |
| Scope        | Deep Research on Sui and related projects (Walrus, Scallop, Cetus, etc.)        |
| Purpose      | Execute and accumulate research in English using ChatGPT, Grok, Gemini, etc., then translate and manage in multiple languages |
| Structure    | All classifications consolidated in `tags:`, files stored flat in `deep-research/` |

## 📁 Directory Structure (Initial)

```plaintext
deep-research-sui/
├── README.md
├── deep-research/                         # English master files (all flat)
│   ├── sui-defi-overview.md
│   ├── sui-nft-overview.md
│   ├── walrus-development.md
│   └── ...
├── translations/                          # Multilingual translations
│   ├── ja/
│   │   ├── sui-defi-overview.md
│   │   └── prompts/
│   │       └── translate.md
│   ├── zh/
│   │   ├── ...
│   │   └── prompts/
│   │       └── translate.md
│   ├── ko/
│   │   └── prompts/
│   │       └── translate.md
│   ├── de/
│   │   └── prompts/
│   │       └── translate.md
│   ├── fr/
│   │   └── prompts/
│   │       └── translate.md
│   └── es/
│       └── prompts/
│           └── translate.md
├── _templates/                             # Common templates for translations and research
│   └── translation-template.md
└── tools/                                  # Auxiliary scripts (optional)
    ├── generate-tag-index.ts
    └── check-missing-translations.ts
```

## 📝 File Structure in deep-research/ (English Original)

Original research content.
Research prompts, results, and other metadata are managed in a single file using `YAML Front Matter + Markdown Body`.
English is used as the primary language since LLMs are optimized for English and Web3 information is predominantly published in English.
Research results are intentionally stored flat in `deep-research/` to avoid the decision-making cost of determining which directory to place files in.

````markdown
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
[Full output text]
```
````

## 📝 File Structure in translations/ (Translations)

```markdown
---
title: Sui DeFi Overview
translation_tool: ChatGPT (GPT-5.2)
translation_prompt: ja/prompts/translation-v1.md
---

## Overview

...

## Translation Body

...
```

## ✅ Tag Management

* All classifications are consolidated in `tags:`, with the following classification axes that can be used in combination:

| Axis         | Examples                                 |
| ------------ | ---------------------------------------- |
| Content Type | `project`, `ecosystem`, `dev-guide`      |
| Technology   | `sui`, `oracle`, `move`                  |
| Use Case     | `oracle`, `nft`, `defi`, `wallet`, `ai`  |
| Audience     | `builder`, `investor`, `user`            |

## ✅ Directory Split Criteria (Future)

| Trigger Condition                        | Action                                                          |
| ---------------------------------------- | --------------------------------------------------------------- |
| File count exceeds 100                   | Split into tag-based directories (e.g., `deep-research/walrus/`) |
| Multiple series appear in specific category | Extract that category only into a directory (e.g., `deep-research/walrus/`) |

## ❌ Metadata Not Included (Managed by Git)

| Field              | Reason                                    |
| ------------------ | ----------------------------------------- |
| `language:`        | Determinable from directory structure     |
| `translator:`      | Determinable from Git log                 |
| `date_translated:` | Available from Git log                    |
| `source_file:`     | Unnecessary due to matching file names    |

## ✅ Additional Notes

* Tools (Node.js/Python, etc.) to generate listings and classifications based on `tags:` are planned for future implementation
* Translation automation is also planned. Currently developing an integrated translation tool using Claude Code Hooks that combines static processing with LLM processing
