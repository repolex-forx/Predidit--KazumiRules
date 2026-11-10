# Repolex Knowledge Graph of Predidit/KazumiRules

RDF knowledge graph data for [Predidit/KazumiRules](https://github.com/Predidit/KazumiRules), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download Predidit/KazumiRules
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 2967d7babafffa92dbf35fbcb69d0fd964139e63
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 2967d7babafffa92dbf35fbcb69d0fd964139e63
│           └── chunk-001.nq.gz
├── blob
│   ├── 2de57b62e65e745c8c7ab3fc98ef129e1198775c.nq.gz
│   ├── 666dc6266037a059ea53904644beace2f1ca429c.nq.gz
│   ├── 71dce5abb2cca74797cd09d88be2f5a5eb5e60de.nq.gz
│   ├── c4d37460bb45738881dd07bb41e4787af9a1f4c2.nq.gz
│   └── ed6aba08a1d8b6d9b87b703c271b59b4f672e50a.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 2967d7babafffa92dbf35fbcb69d0fd964139e63.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 13 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[Predidit/KazumiRules](https://github.com/Predidit/KazumiRules)

---
*Parsed on 2026-11-10 by [repolex](https://repolex.ai)*
