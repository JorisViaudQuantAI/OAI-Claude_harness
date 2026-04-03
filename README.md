# Claude Code Rust Reimplementation

A clean-room Rust reimplementation of Claude Code.

## Overview

This repository does **not** contain Anthropic’s proprietary TypeScript source code.

Instead, it contains:

- a behavioral specification in [`spec/`](./spec)
- a Rust implementation in [`src-rust/`](./src-rust)

The purpose of this project is to reproduce the **behavior**, **architecture**, and **core runtime ideas** of Claude Code in idiomatic Rust, without copying the original implementation.

## Project goal

The goal is to build a Rust-native coding agent runtime that is:

- compatible with Claude Code’s core behavior
- easier to inspect, test, and extend
- more modular than the original implementation
- suitable as a base for future multi-provider support

This is not just a rewrite for the sake of a rewrite.

The target is a clean and maintainable harness with:

- a real CLI
- an agent loop
- tool calling
- session history and memory
- orchestration support
- clear provider and transport boundaries

## Clean-room process

This project follows a two-step clean-room process.

### Specification

The [`spec/`](./spec) directory documents the system at the level of:

- architecture
- runtime behavior
- tool interfaces
- data flow
- prompts
- subsystem design

This phase describes how the system works. It is not a copy of the original source code.

### Implementation

The [`src-rust/`](./src-rust) directory contains the Rust implementation built from the specification.

The objective is to reproduce the **behavior**, not the original expression.

## Repository layout

.
├── spec/        behavioral and architectural documentation  
├── src-rust/    clean-room Rust implementation  
└── README.md

## Current focus

The implementation is moving toward a full, usable agent runtime.

Current priorities include:

- stabilizing the CLI
- improving agent loop fidelity
- preserving tool-call behavior
- separating provider, auth, transport, and query logic
- improving tests and maintainability

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

## Legal note

This repository is intended as a clean-room reimplementation and technical study.

It is based on documented behavior and architecture, not on redistribution of proprietary source code.

Nothing in this repository should be understood as legal advice.

## Why this project exists

Claude Code is one of the most important AI coding runtimes in production today.

Its design is worth studying, and many of its ideas are worth rebuilding in a cleaner and more inspectable system.

This repository exists to do exactly that.

## Contributing

Contributions should improve one of these areas:

- correctness
- compatibility
- architecture
- safety
- tests
- documentation

Good contributions include:

- missing subsystem ports
- provider abstraction work
- tool compatibility fixes
- auth and transport cleanup
- better tests
- better documentation

## Summary

This repository is:

- a clean-room Rust reimplementation effort
- a technical study of Claude Code’s architecture
- the foundation for a modular coding agent runtime in Rust
