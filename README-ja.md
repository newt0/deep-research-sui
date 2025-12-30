# deep-research-sui

## ✅ 概要

| 項目         | 内容                                                                          |
| ------------ | ----------------------------------------------------------------------------- |
| リポジトリ名 | `deep-research-sui`                                                       |
| 管理対象     | sui および関連プロジェクト（Walrus, Scallop, Cetus など）の Deep Research  |
| 目的         | 英語で ChatGPT や Grok, Gemini 等によるリサーチを実行・蓄積し、多言語に翻訳して管理   |
| 構成方針     | すべての分類は `tags:` に集約し、ファイルは `deep-research/` にフラットに配置 |

## 📁 ディレクトリ構成（初期）

```plaintext
deep-research-sui/
├── README.md
├── deep-research/                         # 英語マスターファイル（全てフラット）
│   ├── sui-defi-overview.md
│   ├── sui-nft-overview.md
│   ├── walrus-development.md
│   └── ...
├── translations/                          # 多言語翻訳
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
├── _templates/                             # 翻訳ファイルやリサーチの共通テンプレート
│   └── translation-template.md
└── tools/                                  # 補助スクリプト（任意）
    ├── generate-tag-index.ts
    └── check-missing-translations.ts

```

## 📝 deep-research/ 配下のファイル構成（英語原文）

リサーチのオリジナルコンテンツ。
使用したリサーチプロンプトとリサーチ結果、その他メタ情報を `YAML Front Matters + Markdown Body` でワンファイルにまとめて管理する。
また、LLM は英語に最適化されており、Web3 の情報発信も英語が支配的であるため、基本的に英語を使用する。
`deep-research/` 配下でリサーチ結果は意図的にフラットに配置する。ディレクトリを分割すると、どのディレクトリにファイルを置くべきか？という意思決定コストが生じるため。

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
[出力全文]
```
````

## 📝 translations/ 配下のファイル構成（翻訳）

```markdown
---
title: Sui DeFi概要
translation_tool: ChatGPT (GPT-5.2)
translation_prompt: ja/prompts/translation-v1.md
---

## 概要

...

## 翻訳本文

...
```

## ✅ タグ管理

* 分類はすべて `tags:` に集約し、以下の分類軸を併用可能

| 軸           | 例                                       |
| ------------ | ---------------------------------------- |
| 内容分類     | `project`, `ecosystem`, `dev-guide`      |
| 技術名       | `sui`, `oracle`, `move`   |
| ユースケース | `oracle`, `nft`, `defi`, `wallet` , `ai` |
| 読者層       | `builder`, `investor`,`user`             |

## ✅ ディレクトリ分割の基準（将来的に）

| トリガー条件                     | 対応アクション                                                  |
| -------------------------------- | --------------------------------------------------------------- |
| ファイル数が 100 本以上          | タグベースにディレクトリ分割（例：`deep-research/walrus/`）         |
| 特定カテゴリにシリーズが複数登場 | 該当カテゴリのみディレクトリ切り出し（例：`deep-research/walrus/`） |

## ❌ 含めないメタ情報（Git で管理）

| フィールド         | 理由                           |
| ------------------ | ------------------------------ |
| `language:`        | ディレクトリで判別可能         |
| `translator:`      | Git ログで判別可能             |
| `date_translated:` | Git ログで取得可能             |
| `source_file:`     | ファイル名を一致させるため不要 |

## ✅ その他の補足

* `tags:` に基づいて一覧生成や分類を行うツール（Node.js/Python など）も今後導入予定
* 翻訳も自動化予定。Claude Code Hooks を活用した、静的処理 + LLM 処理の統合翻訳ツールを開発中
