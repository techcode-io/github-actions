# setup-rust

Proxy for [dtolnay/rust-toolchain](https://github.com/dtolnay/rust-toolchain), pinned to a commit SHA. Installs a Rust toolchain with rustup, plus optional targets and components.

All inputs and outputs are forwarded unchanged, except for pinned defaults; see the upstream documentation for details.

The `toolchain` input defaults to a pinned Rust release instead of `stable`; any rustup toolchain specification is still accepted (e.g. `stable`, `nightly`, `1.89`).

## Usage

```yaml
- uses: techcode-io/github-actions/setup-rust@setup-rust/v1
```
