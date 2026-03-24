# Contributing to stellar-router

Thanks for your interest in contributing! This guide covers everything you need to get started.

## Prerequisites

- [Rust](https://rustup.rs/) (stable toolchain)
- `wasm32-unknown-unknown` target
- [Soroban CLI](https://developers.stellar.org/docs/tools/developer-tools/cli/install-cli)

```sh
rustup target add wasm32-unknown-unknown
cargo install --locked stellar-cli --features opt
```

## Setup

```sh
git clone https://github.com/Maki-Zeninn/stellar-router.git
cd stellar-router
cargo build
```

## Running Tests

```sh
cargo test
```

To test a specific contract:

```sh
cargo test -p router-core
```

## Building WASM Artifacts

```sh
stellar contract build
```

This compiles each contract to `target/wasm32-unknown-unknown/release/*.wasm`.

> **Note:** The `wasm32-unknown-unknown` target must be installed separately via `rustup target add wasm32-unknown-unknown` — it is not included with the default Rust installation.

## Branching & PR Conventions

- Branch naming: `feat/<short-description>`, `fix/<short-description>`, `docs/<short-description>`
- Commit style: use the [Conventional Commits](https://www.conventionalcommits.org/) format (e.g. `feat: add route validation`, `fix: handle empty registry`)
- Keep PRs focused — one logical change per PR
- Ensure `cargo test` passes before opening a PR
- Add a clear description of what changed and why

## Known Gotchas

- The `wasm32-unknown-unknown` target must be installed manually — `cargo build` alone won't install it.
- Soroban SDK version is pinned in `Cargo.toml`; avoid bumping it without testing all contracts.
- `stellar contract build` must be run from the workspace root to pick up all contracts.
