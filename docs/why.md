# Why pure Go

go-hocon is one of a family of pure-Go config/data-format engines (alongside
[go-eyaml](https://github.com/go-eyaml) and [go-augeas](https://github.com/go-augeas),
which do belong to the Puppet ecosystem) that provide a well-known format as
an ordinary Go library, with **`CGO_ENABLED=0`** and no runtime dependency on
a JVM or a C toolchain. HOCON itself is Lightbend/Typesafe Config's format,
unrelated to Puppet — go-hocon is validated against the reference
[`puppetlabs/ruby-hocon`](https://github.com/puppetlabs/ruby-hocon) gem
(itself a faithful Ruby port of Typesafe Config), not against anything in the
Puppet language/runtime stack.

## Static, portable, embeddable

Because it is pure Go and imports the Go standard library only, go-hocon compiles with cgo disabled,
cross-compiles to every 64-bit Go target (amd64, arm64, riscv64, loong64, ppc64le, s390x) and to WebAssembly, and links
into a single static binary. There is nothing to install alongside it — no shared
library, no interpreter, no external process it must shell out to.

## Testability by construction

Every interaction with the outside world — file access, the environment, the
network — flows through an **injectable seam**. That means both the happy path and
*every error branch* are exercised deterministically against in-memory fixtures,
which is how the project holds **100% coverage** across operating systems and
architectures from a single test suite, without special privileges.

## An engine, not a framework

go-hocon exposes a small, stable Go API and does one thing well —
syntax & config model — as a dependency-light library you embed, not a
service or CLI you must stand up.
