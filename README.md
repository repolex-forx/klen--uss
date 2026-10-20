# Repolex Knowledge Graph of klen/uss

RDF knowledge graph data for [klen/uss](https://github.com/klen/uss), parsed by [repolex](https://repolex.ai).

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
rlex download klen/uss
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── ca79487ea9b3cfb4a667fb793896a852ce7bd7cf
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── ca79487ea9b3cfb4a667fb793896a852ce7bd7cf
│           └── chunk-001.nq.gz
├── blob
│   ├── 060549673ba4216eaaa2cf0b18b565892014a20d.nq.gz
│   ├── 11edb75c6e211676436cd02bfc62ca0b1046c8e7.nq.gz
│   ├── 24445e10875e825a900d8001fcb969a9eb681675.nq.gz
│   ├── 260174cdf29f3dd9af467455dec0b129392242a2.nq.gz
│   ├── 32786aa437b1ac88d17aa6f54dfa6679c26a5725.nq.gz
│   ├── 58544be8c65649202b6ab6ac89a74a85b6e58139.nq.gz
│   ├── 649c778b48f9f886d3a834dbe6604c118e4e7a26.nq.gz
│   ├── 6b83bea86142e0a10af1f95df9eaed335eadc467.nq.gz
│   ├── 7847eab965e29245a661f368c7db7dfcb0744dc9.nq.gz
│   ├── 7b0b5e27124e0072ba920dd5844b22099c41c579.nq.gz
│   ├── 8aeba116e2c904764a06b3359b344481dac374b5.nq.gz
│   ├── d2018755901b431788cb0d27316d7a432ce1bcbd.nq.gz
│   ├── d8cd54c2ab7b55b8052ca146eaa587b2a96794c1.nq.gz
│   ├── dada99b34c253f5fe43fefdcb39578df275a5558.nq.gz
│   └── e6d7ebdbe01b77f196628dfdd73671b6c071a9a0.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── ca79487ea9b3cfb4a667fb793896a852ce7bd7cf.nq.gz
└── tag
    └── tag.nq.gz

11 directories, 21 files
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

[klen/uss](https://github.com/klen/uss)

---
*Parsed on 2026-10-20 by [repolex](https://repolex.ai)*
