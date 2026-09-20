# Bevy — maintained engine fork

Bevy is a modular Rust game engine with an entity component system, 2D/3D
rendering, assets, animation, audio and platform integration. This repository is
BoysGameStudio's maintained Bevy fork, based on the version in Cargo.toml.
The upstream project is [bevyengine/bevy](https://github.com/bevyengine/bevy).

Use this fork when developing against its reviewed engine contracts. The current
package version is 0.19.1; a registry package with the same version is not proof
of identical source. Consumer manifests and locks select their source graph.

## Start here

Use the Rust minimum declared in Cargo.toml and the target's system dependencies
([Linux setup](docs/linux_dependencies.md)). From this checkout, run an example:

```sh
CARGO_INCREMENTAL=0 cargo run --example breakout
```

This keeps the checked-out fork revision. A new checkout may need explicit
[dependency preparation](CONTRIBUTING.md#dependency-preparation) first.
The minimal app is:

```rust
use bevy::prelude::*;

fn main() {
    App::new().add_plugins(DefaultPlugins).run();
}
```

## Documentation

- [Examples](examples/README.md) and [Cargo features](docs/cargo_features.md).
- [Contributing and local validation](CONTRIBUTING.md).
- [Fork contracts](docs/fork-contracts.md) and [agent instructions](AGENTS.md).
- [Debugging](docs/debugging.md), [profiling](docs/profiling.md) and [linters](docs/linters.md).
- [Upstream learning guide](https://bevy.org/learn/quick-start/introduction) and
  [upstream API docs](https://docs.rs/bevy): verify examples against this checkout;
  upstream `latest` pages may describe a different revision.

## Community and attribution

See the [code of conduct](CODE_OF_CONDUCT.md), [security policy](SECURITY.md),
[asset credits](CREDITS.md) and [upstream contribution guide](https://bevy.org/learn/contribute/introduction).
Bevy is built by its contributors and the Rust game-development community;
[upstream sponsorship](https://bevy.org/donate/) supports their work.

<!-- This next line need to stay exactly as is. It is required for BrowserStack sponsorship. -->
This project is tested with BrowserStack.

## License

Bevy is free, open source and permissively licensed!
Except where noted (below and/or in individual files), all code in this repository is dual-licensed under either:

* MIT License ([LICENSE-MIT](LICENSE-MIT) or [http://opensource.org/licenses/MIT](http://opensource.org/licenses/MIT))
* Apache License, Version 2.0 ([LICENSE-APACHE](LICENSE-APACHE) or [http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0))

at your option.
This means you can select the license you prefer!
This dual-licensing approach is the de-facto standard in the Rust ecosystem and there are [very good reasons](https://github.com/bevyengine/bevy/issues/2373) to include both.

Some of the engine's code carries additional copyright notices and license terms due to their external origins.
These are generally BSD-like, but exact details vary by crate:
If the README of a crate contains a 'License' header (or similar), the additional copyright notices and license terms applicable to that crate will be listed.
The above licensing requirement still applies to contributions to those crates, and sections of those crates will carry those license terms.
The [license](https://doc.rust-lang.org/cargo/reference/manifest.html#the-license-and-license-file-fields) field of each crate will also reflect this.

The [assets](assets) included in this repository (for our [examples](./examples/README.md)) typically fall under different open licenses.
These will not be included in your game (unless copied in by you), and they are not distributed in the published bevy crates.
See [CREDITS.md](CREDITS.md) for the details of the licenses of those files.

### Your contributions

Unless you explicitly state otherwise,
any contribution intentionally submitted for inclusion in the work by you,
as defined in the Apache-2.0 license,
shall be dual licensed as above,
without any additional terms or conditions.
