# Local validation

Remote CI workflows and Actions-only components were removed on 2026-09-19
at the user’s request. Do not recreate, dispatch or require remote jobs.
The removed definitions remain available in Git history, not as active runners.

Run relevant commands from this project directory; these are selectable checks,
not a mandatory full batch for every change. Keep Cargo and GPU runs serialized.
Frozen resolution requires already prepared dependencies and a matching lockfile.

```sh
cargo run --frozen -p ci -- --help
```

Use the existing README and domain runbooks for affected runtime, GPU, asset and
platform checks. A check on Linux does not qualify Windows, macOS or mobile.
Record the source revision, command, configuration, device where relevant, exit
status and evidence directory. Missing inputs are not passing results.

Deleting local workflow files does not change a remote branch until publication.
Actions were disabled and read back as disabled on all ten workbench repositories
on 2026-09-19. No queued or active runs were found. Recheck settings before any
authorized publication. Exact published revisions are recorded by the workbench.

## Explicit inspection and preparation

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

The root lockfile is locally prepared and not tracked in this fork. On a fresh
machine, explicitly run `cargo generate-lockfile` and `cargo fetch --locked` after
selecting the toolchain, retain their lock/toolchain identity, then run frozen
checks. This preparation can resolve new dependencies and is not evidence of
matching another machine's accepted binaries.

## Consumer contracts to preserve

- RenderGraph command buffers must reach the stock CorePipeline Submit stage in
  order. Damage Numbers uses the encoded prefix, actual queue handoff and receipt
  identity before acknowledging journal work or recycling slots. Submission is
  distinct from GPU completion; neither may be inferred merely from Finish running.
- glTF custom attribute registration belongs before loader creation. Keep the
  generic engine mechanism; material-specific registration remains in consumers.
- UnsafeWorldCell callers must prove disjoint access. The Inspector permission
  partition fix belongs at that boundary, not in a new global World lock.
- A single ECS/reflection type identity must be preserved across the resolved
  graph. Workbench source inspection verifies exact reviewed engine paths and
  duplicates; it does not qualify every engine platform/backend.

Keep upstream examples, compile-fail fixtures and platform crates. Absence from one
application's dependency closure does not establish that upstream code is dead.
