<div align="center">

  <h1><code>wasm-bindgen</code></h1>

  <p>
    <strong>Facilitating high-level interactions between Wasm modules and JavaScript.</strong>
  </p>

  <p>
    <a href="https://github.com/rustwasm/wasm-bindgen/actions/workflows/main.yml?query=branch%3Amain"><img src="https://github.com/rustwasm/wasm-bindgen/actions/workflows/main.yml/badge.svg?branch=main" alt="Build Status" /></a>
    <a href="https://crates.io/crates/wasm-bindgen"><img src="https://img.shields.io/crates/v/wasm-bindgen.svg?style=flat-square" alt="Crates.io version" /></a>
    <a href="https://crates.io/crates/wasm-bindgen"><img src="https://img.shields.io/crates/d/wasm-bindgen.svg?style=flat-square" alt="Download" /></a>
    <a href="https://docs.rs/wasm-bindgen"><img src="https://img.shields.io/badge/docs-latest-blue.svg?style=flat-square" alt="docs.rs docs" /></a>
  </p>

  <h3>
    <a href="https://rustwasm.github.io/wasm-bindgen/">Guide (main branch)</a>
    <span> | </span>
    <a href="https://docs.rs/wasm-bindgen">API Docs</a>
    <span> | </span>
    <a href="https://github.com/rustwasm/wasm-bindgen/blob/master/CONTRIBUTING.md">Contributing</a>
    <span> | </span>
    <a href="https://discord.gg/xMZ7CCY">Chat</a>
  </h3>

  <sub>Built with 🦀🕸 by <a href="https://rustwasm.github.io/">The Rust and WebAssembly Working Group</a></sub>
</div>

## Install `wasm-bindgen-cli`

You can install it using `cargo install`:

```
cargo install wasm-bindgen-cli
```

Or, you can download it from the
[release page](https://github.com/rustwasm/wasm-bindgen/releases).

If you have [`cargo-binstall`](https://crates.io/crates/cargo-binstall) installed,
then you can install the pre-built artifacts by running:

```
cargo binstall wasm-bindgen-cli
```

## Example

Import JavaScript things into Rust and export Rust things to JavaScript.

```rust
use wasm_bindgen::prelude::*;

// Import the `window.alert` function from the Web.
#[wasm_bindgen]
extern "C" {
    fn alert(s: &str);
}

// Export a `greet` function from Rust to JavaScript, that alerts a
// hello message.
#[wasm_bindgen]
pub fn greet(name: &str) {
    alert(&format!("Hello, {}!", name));
}
```

Use exported Rust things from JavaScript with ECMAScript modules!

```js
import { greet } from "./hello_world";

greet("World!");
```

## Features

* **Lightweight.** Only pay for what you use. `wasm-bindgen` only generates
  bindings and glue for the JavaScript imports you actually use and Rust
  functionality that you export. For example, importing and using the
  `document.querySelector` method doesn't cause `Node.prototype.appendChild` or
  `window.alert` to be included in the bindings as well.

* **ECMAScript modules.** Just import WebAssembly modules the same way you would
  import JavaScript modules. Future compatible with [WebAssembly modules and
  ECMAScript modules integration][wasm-es-modules].

* **Designed with the ["Web IDL bindings" proposal][webidl-bindings] in mind.**
  Eventually, there won't be any JavaScript shims between Rust-generated wasm
  functions and native DOM methods. Because the Wasm functions are statically
  type checked, some of those native methods' dynamic type checks should become
  unnecessary, promising to unlock even-faster-than-JavaScript DOM access.

[wasm-es-modules]: https://github.com/WebAssembly/esm-integration
[webidl-bindings]: https://github.com/WebAssembly/proposals/issues/8

## Guide

[**📚 Read the `wasm-bindgen` guide here! 📚**](https://rustwasm.github.io/docs/wasm-bindgen/)

You can find general documentation about using Rust and WebAssembly together
[here](https://rustwasm.github.io/docs).

## API Docs

- [wasm-bindgen](https://docs.rs/wasm-bindgen)
- [js-sys](https://docs.rs/js-sys)
- [web-sys](https://docs.rs/web-sys)
- [wasm-bindgen-futures](https://docs.rs/wasm-bindgen-futures)

## MSRV Policy

Libraries that are released on [crates.io](https://crates.io) have a MSRV of v1.57. Changes to the MSRV will be accompanied by a minor version bump.

CLI tools and their corresponding support libraries have a MSRV of v1.76. Changes to the MSRV will be accompanied by a patch version bump.

[Feature resolver version 2](https://doc.rust-lang.org/1.83.0/cargo/reference/resolver.html#feature-resolver-version-2) is required.

## License

This project is licensed under either of

 * Apache License, Version 2.0, ([LICENSE-APACHE](LICENSE-APACHE) or
   http://www.apache.org/licenses/LICENSE-2.0)
 * MIT license ([LICENSE-MIT](LICENSE-MIT) or
   http://opensource.org/licenses/MIT)

at your option.

## Contribution

**[See the "Contributing" section of the guide for information on
hacking on `wasm-bindgen`!][contributing]**

Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in this project by you, as defined in the Apache-2.0 license,
shall be dual licensed as above, without any additional terms or conditions.

[contributing]: https://rustwasm.github.io/docs/wasm-bindgen/contributing/index.html
