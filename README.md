# Rust `cargo` Action

This GitHub Action runs specified [`cargo`](https://github.com/rust-lang/cargo)
command on a Rust language project.

## Example workflow

```yaml
on: [push]

name: CI

jobs:
  build_and_test:
    name: Rust project
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@master
      - uses: actions-rs/cargo@v1
        with:
          command: build
          toolchain: nightly
          arguments: --release --all-features
      - uses: actions-rs/cargo@v1
        with:
          command: test
          toolchain: nightly
          arguments: --all-targets
```

## Inputs

* `command` (*required*) - Cargo command to run (ex. `check` or `build`)
* `toolchain` - Rust toolchain to use (without the `+` sign, ex. `nightly`)
* `args` - Arguments for the cargo command
* `use-cross` - Use [cross](https://github.com/rust-embedded/cross) instead of cargo (default: `false`)
