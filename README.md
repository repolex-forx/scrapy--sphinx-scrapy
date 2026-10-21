# Repolex Knowledge Graph of scrapy/sphinx-scrapy

RDF knowledge graph data for [scrapy/sphinx-scrapy](https://github.com/scrapy/sphinx-scrapy), parsed by [repolex](https://repolex.ai).

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
rlex download scrapy/sphinx-scrapy
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 9231605ac5f164edf053998ed9ba4b61b385f691
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 9231605ac5f164edf053998ed9ba4b61b385f691
│           └── chunk-001.nq.gz
├── blob
│   ├── 061fff04d8a041af19c757dcc6c534c20f797859.nq.gz
│   ├── 0c6dbf812b08fbb4f1beabec53e9ae9fe587dede.nq.gz
│   ├── 0dacdbd6c539bd7ea2ace49482d1d8ea77f979e1.nq.gz
│   ├── 1465c0e3e2c479651badf216b9f0da2546daeee8.nq.gz
│   ├── 4587a83c44dca3e62c17bfece481ccbecf91d0dd.nq.gz
│   ├── 4d0a0863ad6724fd6fdd10407169fe288a3cc95e.nq.gz
│   ├── 623d48cfa6b6f2ba551dde2435254ed5a1b63862.nq.gz
│   ├── 71f625575f0ae5b97977e2f6ba8b00acba3c2c91.nq.gz
│   ├── 7e53d42a3f9c25d12601e7f210ba3ef6cfe9e5f1.nq.gz
│   ├── 9e99910eb413b60d9227cfe49d770695aa0e1d4c.nq.gz
│   ├── b32a7e5173a697db5394e2bd9742426a1217b248.nq.gz
│   ├── dfc5dcb913733486b59e60141e1c7694d1cf79e4.nq.gz
│   ├── e653aea35e6b0f58088ed8b8ad91d2114a850a76.nq.gz
│   └── eb981b685fd76a0a7e42dc48bf64836587f71b79.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 9231605ac5f164edf053998ed9ba4b61b385f691.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 22 files
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

[scrapy/sphinx-scrapy](https://github.com/scrapy/sphinx-scrapy)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*
