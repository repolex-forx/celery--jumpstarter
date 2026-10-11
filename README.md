# Repolex Knowledge Graph of celery/jumpstarter

RDF knowledge graph data for [celery/jumpstarter](https://github.com/celery/jumpstarter), parsed by [repolex](https://repolex.ai).

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
rlex download celery/jumpstarter
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 43dbf34e5e90ac53aff3acb524b0a47d115bb7c2
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 43dbf34e5e90ac53aff3acb524b0a47d115bb7c2
│           └── chunk-001.nq.gz
├── blob
│   ├── 02a73cd45bf6020007eb3e430d7a41609788a76e.nq.gz
│   ├── 05d04db3105f609b83dcdd7b64cde48204c0f611.nq.gz
│   ├── 0c3936975f600ecd2c6aee56ca16c4498cac5b9d.nq.gz
│   ├── 2f8653dcc6552b8034a0366033cdb509c69028b5.nq.gz
│   ├── 58c96087c45001a1e236d814e803ff8d2dfb0c93.nq.gz
│   ├── 5d51e869cfb64b59343692959611612e65ad8f9f.nq.gz
│   ├── 5ecbd2a78822457136d7bcb1df86983af324511f.nq.gz
│   ├── 8694ef02ec822a6a27f1a2d03f94a036bd4bd349.nq.gz
│   ├── 8ba8c3f39211d1d8d4492917834f1def1a2eea06.nq.gz
│   ├── a2ad3ab64a747639bce03c88178514a092f6b426.nq.gz
│   ├── a6dd8b5d7c12c74fa30165154ef40210752a7dc7.nq.gz
│   ├── a7a647c2439d8acd60a8f2dd241b5ef7ab14d27d.nq.gz
│   ├── bbc8813848ed9207469e2073fca4cc377a778d9b.nq.gz
│   ├── e26277c4fd6d10aa6d9839c632cda29fa0b37733.nq.gz
│   └── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 43dbf34e5e90ac53aff3acb524b0a47d115bb7c2.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 23 files
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

[celery/jumpstarter](https://github.com/celery/jumpstarter)

---
*Parsed on 2026-10-11 by [repolex](https://repolex.ai)*
