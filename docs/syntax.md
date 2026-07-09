# Syntax & config model

This page walks the engine's capabilities. Each is complete unless explicitly marked as a documented deferral.

## Lexer & parser

Unquoted keys and strings, `=` / `:`, optional commas and root braces, `#` and `//` comments, dotted-path keys, triple-quoted strings and unicode escapes — the full HOCON surface over JSON.

## Merging & concatenation

Deep object merge of duplicate keys, array and value concatenation, and `+=` self-append, applied as the tree is built.

## Substitutions

`${path}` and optional `${?path}` substitutions with environment fallback and self-reference, resolved after the whole tree is assembled.

## Includes & environment seams

`include` directives and environment lookups run through injectable `WithIncludeResolver` / `WithEnv` seams — no filesystem or process environment needed, in production or in tests.

## Typed access & rendering

`GetString` / `GetInt` / `GetFloat` / `GetBool` / `GetDuration` / `GetBytes` / `GetList` / `GetObject` / `GetOrElse` / `HasPath` over dotted paths, `WithFallback`, and `Render` back to HOCON or JSON.
