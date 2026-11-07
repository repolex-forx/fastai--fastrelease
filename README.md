# Repolex Knowledge Graph of fastai/fastrelease

RDF knowledge graph data for [fastai/fastrelease](https://github.com/fastai/fastrelease), parsed by [repolex](https://repolex.ai).

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
rlex download fastai/fastrelease
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 21425882c172bc1b9094b4ce4636a75ac8897def
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 21425882c172bc1b9094b4ce4636a75ac8897def
│           └── chunk-001.nq.gz
├── blob
│   ├── 0066c5469f55b2c5c9e37eb4261bd5babdec5bec.nq.gz
│   ├── 09d2cf64113a7cb6551f066c739c2817d6046f31.nq.gz
│   ├── 142cef44d9e429648e4679fd3294a0589a9039ab.nq.gz
│   ├── 222093603c5f1dbd4fee115efbf8a0c09436696b.nq.gz
│   ├── 261eeb9e9f8b2b4b0d119366dda99c6fd7d35c64.nq.gz
│   ├── 2fa08a3f9a41d871b19a62a8c653565c9b8dfce1.nq.gz
│   ├── 361aa8ddd2a198483516b283da4a1e1ac34971f9.nq.gz
│   ├── 37081e589f2d34c8eadcfca535a6bb92f977f9f2.nq.gz
│   ├── 38fbde548847377b547aeb7e695dedc2e928f5a2.nq.gz
│   ├── 396763121083b97dc7343b3ee3d61efb23ddee41.nq.gz
│   ├── 3a334acdc5532044c1984882ea03147af65da9a5.nq.gz
│   ├── 417bd2c9aca7879b0aa190328049fe8a845643f4.nq.gz
│   ├── 43786af05574d256d04dbdb6666540f4c199c5bb.nq.gz
│   ├── 455ac564581625166a83a95815810f0f03968f92.nq.gz
│   ├── 4c0096a7c485b568ecec521985287842baa64427.nq.gz
│   ├── 5341ac919b3842edf6654f1a4eb0f54caaf2f6ea.nq.gz
│   ├── 5bb92fe0a35123a46400a88807265694030a68c3.nq.gz
│   ├── 5c0e7ced193cb35aee60cbadc3e022a1da0fd8cc.nq.gz
│   ├── 70c40e9c08ed830172449a9556e26b82f42e7b2d.nq.gz
│   ├── 7fae8e7ef3db30cef5311ea283ffd4ccb50f10c3.nq.gz
│   ├── 80f77f2895a39fb51ac73b0d3b61853410cc6e8c.nq.gz
│   ├── 8bea6b0320c7fd5923ba8eb8dd2d988ef61dd013.nq.gz
│   ├── 98a964d8eef60f651ad7608de551d165069709f4.nq.gz
│   ├── a58a767ddaabf69002f725030e7bbda8099c4044.nq.gz
│   ├── aedcd3de872b0dc0a1d37147dcd34cc4caac6b1a.nq.gz
│   ├── b0084ad1038f7e596dbe6906cd247e63bbe3b29d.nq.gz
│   ├── b3e972294794e71c4df4839912e21ee755409158.nq.gz
│   ├── baa55fe130619da3f39966e8cf00474c4e72471d.nq.gz
│   ├── bd97c177d2cedceff7e4f53ff5074dcb8d432fd2.nq.gz
│   ├── c00c560c7050f72c1d9f402e0efad3a983240fa8.nq.gz
│   ├── c957d822fbea58c028cee5cb8e732fe3087732aa.nq.gz
│   ├── d001a7ebfe83f325524cfcbcc8e800b048c3cc2a.nq.gz
│   ├── d343ecdb2d25b7eb1583401204bf16bc87c207f9.nq.gz
│   ├── d8352783a9fb15f2a9342c91a56be1ef5e5a6051.nq.gz
│   ├── df2cb7d717133507806b9744a86680cc3bf4eedd.nq.gz
│   ├── dfabb1454a9773e8fec1e729ca0be9d71ee12bd1.nq.gz
│   ├── e1beb8591ddd2770ead4b8935a04c43349a244ea.nq.gz
│   ├── e306e0b19fbf4eab9f41ad3f3fa22c9141c9c427.nq.gz
│   └── f013ceba0a46f67ada9704cdf74ae1ddd62250b4.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 21425882c172bc1b9094b4ce4636a75ac8897def.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 47 files
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

[fastai/fastrelease](https://github.com/fastai/fastrelease)

---
*Parsed on 2026-11-07 by [repolex](https://repolex.ai)*
