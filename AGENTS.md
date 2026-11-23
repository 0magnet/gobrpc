# AGENTS.md

Guidance for AI coding agents working in this repository.

## Communication style

Use simple direct language everywhere outside the code. That includes commit
messages, issues and review comments.

Lead with the change and the reason for it. Include a measurement, a table or
a log excerpt only where it is the evidence for a claim.

Avoid extra colons, semicolons and dashes. Write plain sentences instead.

## Comments

Omit redundant comments. Where a comment is needed, keep it short. Where a
comment records a specific requirement, cite the source.

## Naming

This package is a drop-in for the standard library's `net/rpc`, so its names
follow `net/rpc`: `NewClient`, `NewServer`, `Dial` and the rest. They are not
renamed to fit the general rules, and the guard here checks only for `func
init()` outside package main.

## No coding tool attributions

Never add `Co-Authored-By`, a "Generated with" footer, or any other coding tool
attribution to a commit, issue or comment.

## Verify before you submit

Run the change. Do not submit code that is only plausibly correct. Where
something was not verified, say so plainly rather than implying it was.

## Commits

The subject line is `package: lowercase summary` with no trailing period. Use
`all:` for a repository wide change. Any behavior change gets a body giving the
symptom, the cause and the fix.

Commits go to `main` directly.

## Working in this repository

`make check` runs the linters, `go vet`, the tests and the init guard. The
js/wasm-tagged half is linted and vetted again in its own build context, and
`make test-wasm` runs its tests under Node. `make docs` regenerates the dependency graph
and code counts in the README.

`make check-inits` fails on a `func init()` outside package main. Today's
violations are listed in `scripts/guard/`, and that allowlist only shrinks.
