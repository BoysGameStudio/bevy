# Agent instructions

Read README.md for project context and CONTRIBUTING.md and docs/fork-contracts.md for the affected task.

- Preserve one ECS/reflection source identity across the resolved graph. Do not
  change package versions to conceal source incompatibility.
- Keep queue handoff ordering, glTF registration timing and unsafe access proofs.
  Consumer-specific material/game policy does not belong in generic engine code.
- Do not invoke the no-argument local `ci` task: it includes broad checks and a
  Cargo clean operation. Select explicit tasks and preserve comparison artifacts.
- Generated pages, embedded README/error docs and platform examples have consumers;
  change their owning inputs and references before removing or moving content.
- Use local validation only; do not create, enable, dispatch or require remote CI.
- Choose checks for the affected behavior. Documentation-only edits use link,
  API/command-reference and packaging-input checks, without Cargo/GPU runs.
- Serialize Cargo/GPU work and set `CARGO_INCREMENTAL=0`. Report missing inputs
  and unexecuted platform checks; do not weaken tests or replace golden images.
- Preserve unrelated work and authoring inputs. Commit or publish only when asked.
