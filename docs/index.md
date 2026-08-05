# go-hocon

**HOCON (Typesafe Config) parser in pure Go — substitutions, includes, units, a JSON superset.**

go-hocon is a pure-Go (CGO_ENABLED=0) parser for HOCON, the Human-Optimized Config Object Notation used by Typesafe Config. HOCON is a superset of JSON that adds unquoted keys and strings, = as an alias for :, optional commas and root braces, # and // comments, dotted-path keys, deep merging of duplicate keys, array and value concatenation, ${path} / ${?path} substitutions with environment fallback, += self-append, include directives and duration / size unit suffixes. Includes and environment lookups run through injectable seams, so callers and tests never need touch the filesystem or process environment. Typed accessors read dotted paths and Render serialises back to HOCON or JSON. Standard library only, 100% coverage, six arches and WebAssembly.

- **[Why pure Go](why.md)** — a static, cgo-free, dependency-light engine.
- **[Syntax & config model](syntax.md)** — the capabilities in detail.
- **[Usage & API](api.md)** — the Go API and how to call it.
- **[Roadmap](roadmap.md)** — what is done and what is next.

## Guarantees

- **Pure Go, zero cgo.** Imports the Go standard library only; cross-compiles to the six 64-bit Go targets (amd64, arm64, riscv64, loong64, ppc64le, s390x) and WebAssembly, linking into a static binary.
- **Faithful to the HOCON / Typesafe Config specification.**
- **100% test coverage** including error branches, enforced as a CI gate.
