# Repolex Knowledge Graph of xarray-contrib/xproj

RDF knowledge graph data for [xarray-contrib/xproj](https://github.com/xarray-contrib/xproj), parsed by [repolex](https://repolex.ai).

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
rlex download xarray-contrib/xproj
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 033e141509ff55cc1040dbba84907877a560a124
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 033e141509ff55cc1040dbba84907877a560a124
│           └── chunk-001.nq.gz
├── blob
│   ├── 0612b5224eb567ee6cef89e23cb87fd6fde90b39.nq.gz
│   ├── 075ee507c2e1ae6f84ef437e156df561a85d3982.nq.gz
│   ├── 0a75e0b9420cfbb4c3de47a20e146e13fc54c9d6.nq.gz
│   ├── 0aef05b683017f771ed2babd3e6b4578e94e22e5.nq.gz
│   ├── 13bb96043493b2fbadfc628f97dc303119a13c67.nq.gz
│   ├── 175defcadb3eb38d9a05bd51953a678108dbab0e.nq.gz
│   ├── 1fa483cb1a7a260e664be9829f832e5abd21e7da.nq.gz
│   ├── 261eeb9e9f8b2b4b0d119366dda99c6fd7d35c64.nq.gz
│   ├── 281545cbf675035d877a8236fd7cbaa66b9d8028.nq.gz
│   ├── 2b564edb5bbc9bc8b0a9df12ef3bd03e22a28008.nq.gz
│   ├── 337a3e3a4bfa878045973dd9d052c5d3cd0721a2.nq.gz
│   ├── 3744b49afebd55097c4e088cd04fc7ab758d8ee5.nq.gz
│   ├── 3b2fd04e51ad82a54ca7f30fc421e3118cf97357.nq.gz
│   ├── 4c6ca9180486a3bea06604489e054e8ede821147.nq.gz
│   ├── 6db32ad06fb60f890658c1303cfa3a2252414886.nq.gz
│   ├── 7480b0386280255934c455ff3c352606208a29bd.nq.gz
│   ├── 7d17e1d02bdac479104f1b1c83d97f6a78e7c543.nq.gz
│   ├── 859632c744c7ada62c69362eb3ff513af56e0288.nq.gz
│   ├── 8ac6b8c4984dcd382e54c7923325af6d226ca3df.nq.gz
│   ├── 920d39224fe345b9d7054688ad4014cf0c5afbf6.nq.gz
│   ├── 95fb569ea0fdfb7868d8d925a8e4863d58801c86.nq.gz
│   ├── 9d1e0987bfc323000b570d680343f00c53ddbc3d.nq.gz
│   ├── 9d3511a4de181b910400803422e41d4254316055.nq.gz
│   ├── a4cf38615e73b2a119b43179d0969046e924658d.nq.gz
│   ├── a6fcf4d091cf9b0dfd54ca08419834e88a752ddd.nq.gz
│   ├── b79293627da446841c9a8e526a9c79a2d3618fd1.nq.gz
│   ├── ba128426a9b1b2631a70012be7f0581658920ed1.nq.gz
│   ├── be46ac13903b5bd245b8dae84dbf84379e42cff5.nq.gz
│   ├── c27e0ac566cc45d6a5e080ef6dc3dfa0320e8fcc.nq.gz
│   ├── c5e875ae83b9b3f2ff37aa85e75c66c36dcb3a3b.nq.gz
│   ├── ceb6a56db1028fcab0ae1e953f16094ac9a60d9c.nq.gz
│   ├── d8e0ddf3da82de17d08fd35ce7ad404f4b0843bc.nq.gz
│   ├── dd47d55999f98da0a788d39641c1ffcef1d1143e.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── f6c127a43aca0863fc89766feff1e51019f855ef.nq.gz
│   ├── fb1f61a01aabd87acae7f3c5625be644aa5a0201.nq.gz
│   └── fedf383c8c065895a1b0eee196d453fd12bc0327.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 033e141509ff55cc1040dbba84907877a560a124.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 45 files
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

[xarray-contrib/xproj](https://github.com/xarray-contrib/xproj)

---
*Parsed on 2026-10-28 by [repolex](https://repolex.ai)*
