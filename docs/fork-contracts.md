# Fork contracts


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


The owning engine surfaces are `crates/bevy_render/src/renderer/`,
`crates/bevy_gltf/src/`, and `crates/bevy_ecs/src/world/unsafe_world_cell.rs`.
Consumer-specific acceptance belongs to the corresponding library: queue receipts
in Damage Numbers, glTF registration in Stylized, and disjoint permission tests
in Inspector. Engine checks and actual consumer acceptance are separate scopes.
See [local validation](../CONTRIBUTING.md) for source preparation and task selection.
