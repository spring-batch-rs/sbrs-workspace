# CLAUDE.md — sbrs-workspace

This workspace is the root of the **Spring Batch RS** ecosystem. It groups four sibling repositories, each with a distinct responsibility.

## Repository Map

```
spring-batch-rs/
├── sbrs-workspace/     ← you are here (workspace meta, no code)
├── sbrs-lib/           ← Rust library (crates.io package)
├── sbrs-docsite/       ← Documentation website (Astro + Starlight)
└── sbrs-java-bench/    ← Java/Spring Batch reference benchmark
```

## Project Roles

| Repo | Language | Purpose |
|---|---|---|
| `sbrs-lib` | Rust | Core library: readers, writers, tasklets, chunk processing |
| `sbrs-docsite` | TypeScript / MDX | Public documentation site at https://spring-batch-rs.boussekeyt.dev/ |
| `sbrs-java-bench` | Java 25 / Spring Batch | 10M-row ETL benchmark (CSV → PostgreSQL → XML) used as reference |
| `sbrs-workspace` | — | Workspace meta: links, cross-repo conventions, shared docs |

## Cross-Repo Rules

### Sync Obligation

Any change that adds or modifies a public feature in `sbrs-lib` **must** be reflected in `sbrs-docsite` in the same logical change set. This includes:

- New readers / writers → update `item-readers-writers/overview.mdx` and `reference/features.mdx`
- New tasklets → update `tasklets/` and `reference/features.mdx`
- New examples → add or update the matching page under `examples/`
- New feature flags → update `reference/features.mdx` and `sbrs-lib/README.md`

### Versioning

All repos follow the version of the library (`sbrs-lib/Cargo.toml` is the source of truth). When cutting a release, update the version in:
1. `sbrs-lib/Cargo.toml`
2. `sbrs-docsite` — hero tagline or version badge if present
3. Tag all three repos with the same `vX.Y.Z` tag

## Working Across Repos

When a task spans multiple repos, work in each repo directory separately. Each repo has its own `.git` and its own CLAUDE.md with repo-specific rules — read the target repo's CLAUDE.md before touching its code.

Quick navigation:
```bash
cd ../sbrs-lib        # Rust library
cd ../sbrs-docsite    # Documentation website
cd ../sbrs-java-bench # Java benchmark
```

## Key Links

- **Website**: https://spring-batch-rs.boussekeyt.dev/
- **Crates.io**: https://crates.io/crates/spring-batch-rs
- **docs.rs**: https://docs.rs/spring-batch-rs
- **GitHub** (sbrs-lib): referenced in sbrs-lib CI workflows
