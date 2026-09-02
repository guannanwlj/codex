# Architecture

## Overview

This is Codex, a Rust-based AI coding agent that runs model-driven conversations to help developers work on code. Users primarily enter through Interactive Frontends (TUI/CLI/npm) or programmatically through the Headless Service Layer's app-server and exec-server, which expose the agent to IDEs and SDKs without the terminal UI. At the center, the Core Agent Engine drives the conversation/turn loop, protocols, configuration, and plugin surface, backed by Cloud Backend, Auth & Model Providers for OpenAI and third-party model access and Network & Telemetry Infrastructure for shared HTTP/WebSocket plumbing and observability.

## Architectural Patterns

- Cargo Workspace / Polyglot Monorepo (one Rust workspace
- Layered Hexagonal-ish Architecture (Interface TUI/SDK → App Server
- Client–Server (local RPC)
- Agent Loop / Orchestrator Pattern (perceive → plan
- Policy & Sandbox Enforcement (Guard/Interceptor)
- Plugin / Extension Architecture (ext/ modules, skills/ with
- Template-driven Prompting (externalized prompts and model-specific instruction files)
- Event Streaming / async pipelines (stream-parser, reducers, streaming-first
- Repository / Persistence Layer (session and state persistence

## Project Context

- **Project Type:** AI Coding Agent Platform
- **Domain:** AI/ML

## Tech Stack

`Python`, `Node.js/TypeScript`, `Gin`, `Pydantic`

## Common Commands

## Key Entry Points

_No standard entry points detected._

## Modules

_Each module links to a per-module keyword file listing its native symbols (file/function/class names kept verbatim for exact grep), ranked by importance. The exact formula depends on the module's graph density: dense graphs use `0.30·bridge + 0.30·usage + 0.15·type + 0.15·activity + 0.10·exported`; sparse graphs (calls hidden behind runtime dispatch) use `0.20·bridge + 0.20·usage + 0.15·type + 0.15·activity + 0.15·exported + 0.15·file_hub`. See each keyword file's header for the rule that produced its scores. Agents read a module's keyword file on demand._

### Core Agent Engine

The heart of the system: the agent conversation/turn loop, its plugin surface, protocol definitions, configuration, and the exec entry crate.

### Interactive Frontends (TUI/CLI/npm)

User-facing entry points: the very large terminal UI, the CLI driver, and the npm distribution shim that wraps the Rust binary.

### Headless Service Layer

Programmatic, non-TUI access to Codex via the app-server family (server, protocol, daemon, transport, test/client crates) for IDEs and SDKs, plus the exec-server for headless execution.

- Keywords: [`keywords/3.md`](keywords/3.md) — 1 scored symbol(s)

### Cloud Backend, Auth & Model Providers

API clients and model-provider abstraction for OpenAI/ChatGPT and third-party backends, including login/auth flows and cloud-task integration.

### Network & Telemetry Infrastructure

Shared HTTP/WebSocket plumbing, API-traffic proxies, OpenTelemetry tracing, and product analytics/feedback.

### Sandboxing & Security

Command-execution isolation and policy enforcement across platforms, plus secrets and agent identity.

- Keywords: [`keywords/6.md`](keywords/6.md) — 22 scored symbol(s)

### Agent Tools, Skills & MCP Integrations

The capability layer the agent invokes: built-in tools, skills, hooks, prompt templates, MCP client/server, and external connectors/migration.

- Keywords: [`keywords/7.md`](keywords/7.md) — 168 scored symbol(s)

### Session State & Persistence

Durability of agent sessions: thread store, conversation history, rollout/session files and tracing, memories, and the agent graph store.

### Code Mode & Extension Runtime (V8)

The JavaScript extension environment: a host/runtime embedding V8, its protocol, and the ext/ extension sources.

### Shared Foundation Utilities

Cross-cutting low-level crates consumed by nearly every other crate: general utils, async helpers, filesystem and terminal primitives, build/install metadata, and feature flags.

### Client SDKs

Official language SDKs (TypeScript and Python) that wrap the app-server/exec-server surfaces for external embedding.

- Keywords: [`keywords/11.md`](keywords/11.md) — 200 scored symbol(s)

### Build, Release & Dev Infrastructure

Bazel modules/rules/toolchains, vendored dependencies, upstream patches, linters, packaging/install scripts, and top-level build config.

- Keywords: [`keywords/12.md`](keywords/12.md) — 200 scored symbol(s)

### Documentation

User and contributor docs covering setup, configuration, sandboxing, exec policy, skills, and contribution guidelines.

