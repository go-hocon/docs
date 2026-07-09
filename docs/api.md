# Usage & API

```go
import "github.com/go-hocon/hocon"
```

```go
cfg, err := hocon.Parse(`
  app {
    name = checkout
    workers = 4
    timeout = 30s
    max-size = 8MB
    listen = ${?PORT}
  }
`)
if err != nil { /* typed parse / resolve error */ }

name, _ := cfg.GetString("app.name")     // "checkout"
n,   _  := cfg.GetInt("app.workers")     // 4
d,   _  := cfg.GetDuration("app.timeout")// 30 * time.Second
b,   _  := cfg.GetBytes("app.max-size")  // 8388608
fmt.Print(cfg.Render(hocon.RenderOptions{}))
```

`Parse` lexes, parses, merges and resolves an input string into a `*Config`. Includes and environment lookups run through the `WithIncludeResolver` and `WithEnv` options. Typed accessors read dotted paths and report typed errors: `GetString`, `GetInt`, `GetFloat`, `GetBool`, `GetDuration`, `GetBytes`, `GetList`, `GetObject`, `GetOrElse`, `HasPath`. `Render` serialises a config back to HOCON or JSON, and `WithFallback` layers a second config underneath.

## Command line & builds

The library is `CGO_ENABLED=0` pure Go. Cross-compile it anywhere:

```sh
GOOS=linux   GOARCH=arm64    go build ./...
GOOS=js      GOARCH=wasm     go build ./...
```

It builds and tests on all six 64-bit Go targets (amd64, arm64, riscv64, loong64, ppc64le, s390x).
