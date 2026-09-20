# Contributing and local validation

The [upstream contribution guide](https://bevy.org/learn/contribute/introduction)
and [AI contribution policy](https://bevy.org/learn/contribute/policies/ai/) apply
when preparing upstream contributions. This fork uses local validation only.

## Choose an affected check

Run from the repository root, serialize Cargo work and set `CARGO_INCREMENTAL=0`.
Select the changed crate, feature and target rather than running every backend.
Record source/lock/toolchain identity, commands, results and missing coverage.
A successful Linux check does not qualify other operating systems or GPUs.

The no-argument local `ci` binary runs a broad suite including
`IntegrationTestCleanCommand`, which calls Cargo clean for its integration-test
manifest. Do not invoke it implicitly while reviewing sources or preserving
comparison binaries. The name is local tooling, not permission for remote CI or
cache deletion. Select an explicit task:

```sh
cargo run --frozen -p ci -- --help
cargo run --frozen -p ci -- format  # cargo fmt --all -- --check; does not format in place
CARGO_INCREMENTAL=0 cargo check --frozen -p bevy_ecs --lib
```

## Dependency preparation

The root lockfile is locally prepared and not tracked in this fork. On a fresh
machine, explicitly run `cargo generate-lockfile` and `cargo fetch --locked` after
selecting the toolchain, retain their lock/toolchain identity, then run frozen
checks. This preparation can resolve new dependencies and is not evidence of
matching another machine's accepted binaries.


## Contracts and documentation

Preserve [fork contracts](docs/fork-contracts.md). Retain upstream examples,
compile-fail fixtures and platform crates; one application's dependency closure
is not a deletion inventory for an engine.

`docs/cargo_features.md` and `examples/README.md` are produced by
`tools/build-templated-pages`; change their source/template and regenerate the
relevant page. Crate README and error Markdown can be rustdoc inputs. Check
`include_str!` and Cargo `readme` consumers before moving documentation.
Documentation-only edits use reference and command checks, without builds/GPU runs.
