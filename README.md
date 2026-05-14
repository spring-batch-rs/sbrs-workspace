# Spring Batch RS — Workspace

This repository is the **meta root** of the Spring Batch RS ecosystem. It contains no code — it exists to document the project structure, cross-repo conventions, and shared links.

## Repository Map

```
spring-batch-rs/
├── sbrs-workspace/     ← you are here
├── sbrs-lib/           ← Rust library published on crates.io
├── sbrs-docsite/       ← Documentation website (Astro + Starlight)
└── sbrs-java-bench/    ← Java/Spring Batch reference benchmark
```

## Projects

| Repo | Purpose | Stack |
|---|---|---|
| [sbrs-lib](https://github.com/spring-batch-rs/sbrs-lib) | Core batch processing library | Rust, crates.io |
| [sbrs-docsite](https://github.com/spring-batch-rs/sbrs-docsite) | Public documentation | Astro, Starlight, Firebase |
| [sbrs-java-bench](https://github.com/spring-batch-rs/sbrs-java-bench) | Performance reference benchmark | Java 25, Spring Batch 6 |

## Quick Navigation

```bash
cd ../sbrs-lib        # Rust library
cd ../sbrs-docsite    # Documentation website
cd ../sbrs-java-bench # Java benchmark
```

## Links

- **Website**: https://spring-batch-rs.boussekeyt.dev/
- **Crates.io**: https://crates.io/crates/spring-batch-rs
- **API docs**: https://docs.rs/spring-batch-rs

## Cross-Repo Sync Rules

Any change that adds or modifies a public feature in `sbrs-lib` must be reflected in `sbrs-docsite` in the same logical change set.

| sbrs-lib change | Pages to update in sbrs-docsite |
|---|---|
| New reader / writer | `item-readers-writers/overview.mdx` + `reference/features.mdx` |
| New tasklet | `tasklets/` + `reference/features.mdx` |
| New example | `examples/<category>.mdx` |
| New feature flag | `reference/features.mdx` + `sbrs-lib/README.md` |
| Version bump | Version badge in `index.mdx` + tag all three repos `vX.Y.Z` |

## License

Licensed under [MIT](https://github.com/spring-batch-rs/sbrs-lib/blob/main/LICENSE-MIT) or [Apache-2.0](https://github.com/spring-batch-rs/sbrs-lib/blob/main/LICENSE-APACHE) at your option.
