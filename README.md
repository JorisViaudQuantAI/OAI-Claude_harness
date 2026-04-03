# Claude Code Rust Reimplementation

A clean-room Rust reimplementation of Claude Code.

## Overview

This repository does **not** contain Anthropic’s proprietary TypeScript source code.

It contains:

- a behavioral specification in [`spec/`](./spec)
- a Rust implementation in [`src-rust/`](./src-rust)

The goal of this project is to reproduce the **behavior** and **system design** of Claude Code in idiomatic Rust, without copying the original source.

## Goals

This project aims to build a Rust-native coding agent runtime that is:

- compatible with Claude Code’s core behavior
- easier to inspect, test, and extend
- more modular than the original implementation
- suitable as a base for multi-provider support

The target is not just “Claude Code in Rust”.

The target is a clean and maintainable harness with:

- a real CLI
- an agent loop
- tool calling
- session history and memory
- orchestration support
- clear provider and transport boundaries

## Status

This project follows a clean-room process:

1. **Specification** — document the behavior and architecture in [`spec/`](./spec)
2. **Implementation** — build the Rust version from that specification in [`src-rust/`](./src-rust)

The objective is to reproduce the **behavior**, not the original expression.

## Repository layout

- `spec/` — behavioral and architectural documentation
- `src-rust/` — clean-room Rust implementation

## Requirements

- Rust toolchain
- Cargo
- a Unix-like shell is recommended

## Quick start

Clone the repository and enter the Rust workspace:

```bash
git clone https://github.com/<your-user>/<your-fork>.git
cd <your-fork>/src-rust
```

Build the CLI:

```bash
cargo build -p claude-code
```

Build an optimized binary:

```bash
cargo build --release -p claude-code
```

Install the CLI locally:

```bash
cargo install --path crates/cli
```

After installation, the binary is available as:

```bash
claude
```

## Build

Run these commands from `src-rust/`.

Debug build:

```bash
cargo build -p claude-code
```

Release build:

```bash
cargo build --release -p claude-code
```

Run all tests:

```bash
cargo test --workspace
```

Format the code:

```bash
cargo fmt --all
```

Lint the workspace:

```bash
cargo clippy --workspace --all-targets
```

## Usage

Show help:

```bash
claude --help
```

Or without installing first:

```bash
cargo run -p claude-code -- --help
```

Start the interactive CLI:

```bash
claude
```

Or:

```bash
cargo run -p claude-code --
```

Run a one-shot prompt:

```bash
claude --print "Explain this repository"
```

Or:

```bash
cargo run -p claude-code -- --print "Explain this repository"
```

Use a specific model:

```bash
claude --model claude-sonnet-4-6
```

Run from a specific working directory:

```bash
claude --cwd /path/to/project
```

Resume a previous session:

```bash
claude --resume <session-id>
```

## Authentication

The authentication layer is moving toward multi-provider support.

### Current support

Today, the CLI supports Anthropic credentials.

Use an API key:

```bash
export ANTHROPIC_API_KEY=your_key_here
claude
```

Or pass it directly:

```bash
claude --api-key your_key_here
```

Anthropic OAuth is also supported:

```bash
claude auth login
claude auth status
claude auth logout
```

### Planned support

The next planned addition is native OpenAI / Codex OAuth support.

Expected usage:

```bash
claude auth login --openai
claude auth status
claude auth logout
```

### Long-term direction

The target authentication model is:

- Anthropic API key support
- Anthropic OAuth support
- OpenAI / Codex OAuth support
- provider-aware credential resolution in one unified CLI

This keeps the runtime independent from any single provider-specific login flow.

## Roadmap

Current priorities:

- CLI stability
- agent loop fidelity
- tool-call compatibility
- clearer module boundaries
- provider abstraction
- stronger tests

The medium-term goal is a provider-agnostic coding agent runtime with first-class support for multiple backends.

## Design principles

This project should preserve the most important ideas behind Claude Code:

- CLI-first workflow
- strong tool runtime
- modular prompt construction
- safe permission handling
- session memory
- orchestration support
- clean extensibility

It should also improve on the original where possible:

- clearer architecture
- less provider-specific coupling
- easier testing
- easier maintenance
- cleaner Rust code

## Contributing

Contributions should improve one of these areas:

- correctness
- compatibility
- architecture
- safety
- tests
- documentation

Useful contributions include:

- missing subsystem ports
- provider abstraction work
- tool compatibility fixes
- auth and transport cleanup
- better tests
- better docs

## Legal note

This repository is intended as a clean-room reimplementation and technical study.

It is based on documented behavior and architecture, not on redistribution of proprietary source code.

This repository is not legal advice.

## Why this project exists

Claude Code is one of the most important AI coding runtimes in production.

Its design is worth studying, and many of its ideas are worth rebuilding in a cleaner, more inspectable system.

This repository exists to do exactly that.

## Summary

This repository is:

- a clean-room Rust reimplementation effort
- a technical study of Claude Code’s architecture
- the foundation for a modular coding agent runtime in Rust
