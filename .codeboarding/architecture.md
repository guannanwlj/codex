# Architecture

## Overview

Codex is an AI coding agent built in Rust, entered primarily through Terminal Frontends (the interactive terminal UI, CLI, and Node/npm wrapper). Its core is the Agent Core Engine, which orchestrates sessions, prompt templates, configuration, and built-in tools, while the App Server Platform exposes those sessions over a structured client/server protocol for IDEs and SDK consumers. Supporting this runtime are Execution & Sandboxing for OS-level command isolation and egress control, and Cloud & Backend Services for OpenAI/ChatGPT API clients, auth, and model-provider plumbing.

## Architectural Patterns

- Hexagonal / Ports & Adapters (primary): domain core
- Client–Server / RPC hub: app-server (daemon + client
- Plugin/Extension architecture: ext/ (web-search, image-generation, guardian-v2, goal, memories),
- Layered security (defense-in-depth): execpolicy → sandbox mode →
- Agent loop / pipeline: prompt templates → model
- Polyglot monorepo: Cargo workspace nested inside Bazel workspace

## Project Context

- **Project Type:** AI Coding Agent / Developer Productivity CLI Platform
- **Domain:** AI/ML

## Tech Stack

`Python`, `Node.js/TypeScript`, `Gin`, `Pydantic`

## Common Commands

## Key Entry Points

_No standard entry points detected._

## Modules

_Each module links to a per-module keyword file listing its native symbols (file/function/class names kept verbatim for exact grep), ranked by importance. The exact formula depends on the module's graph density: dense graphs use `0.30·bridge + 0.30·usage + 0.15·type + 0.15·activity + 0.10·exported`; sparse graphs (calls hidden behind runtime dispatch) use `0.20·bridge + 0.20·usage + 0.15·type + 0.15·activity + 0.15·exported + 0.15·file_hub`. See each keyword file's header for the rule that produced its scores. Agents read a module's keyword file on demand._

### Agent Core Engine

The central Rust engine that drives Codex sessions, handling orchestration, the internal session protocol, prompt templates, configuration, and the agent's built-in tools.

### Terminal Frontends

The user-facing entry points including the interactive terminal UI, the Rust CLI, and the Node/npm distribution wrapper.

- Keywords: [`keywords/2.md`](keywords/2.md) — 9 scored symbol(s)

### App Server Platform

The client/server surface that exposes Codex sessions over a structured protocol (daemon, transports, protocol types, test clients) for IDEs and SDKs to build on.

- Keywords: [`keywords/3.md`](keywords/3.md) — 1 scored symbol(s)

### Execution & Sandboxing

Command execution and OS-level isolation including the exec server, Linux/Windows sandbox implementations, network egress proxy, shell escalation, and execution policy.

- Keywords: [`keywords/4.md`](keywords/4.md) — 22 scored symbol(s)

### Cloud & Backend Services

All remote/API plumbing including OpenAI/ChatGPT backend clients, cloud tasks and config, login/auth, model provider abstraction, and HTTP/WebSocket transport.

### Extensibility

The extension subsystem providing JavaScript/V8-powered code mode, ext/ extensions, lifecycle hooks, plugins, agent skills, and external-agent migration.

- Keywords: [`keywords/6.md`](keywords/6.md) — 168 scored symbol(s)

### MCP & Integrations

Model Context Protocol support and external integrations including MCP client/server stacks, connectors to external systems, and local model runtimes.

- Keywords: [`keywords/7.md`](keywords/7.md) — 165 scored symbol(s)

### Session State & Persistence

Durable session data including threads, rollouts and rollout tracing, histories, memories, and agent identity/graph storage.

### Shared Foundations

Cross-cutting utility crates used by nearly every subsystem, including general utils, file search/watch/FS access, git helpers, patch application, async helpers, and feature flags.

### Telemetry & Observability

Instrumentation and diagnostics including OpenTelemetry, analytics, diagnostics, feedback capture, and response debug context.

### SDKs

Official language SDKs that wrap the Codex engine for programmatic use.

- Keywords: [`keywords/11.md`](keywords/11.md) — 1289 scored symbol(s)

### Build & Release Infrastructure

The build/CI/packaging layer including Bazel workspace config, portability patches for third-party deps, Nix, lint tools, and packaging/release scripts.

- Keywords: [`keywords/12.md`](keywords/12.md) — 309 scored symbol(s)

### Documentation & Project Meta

User/developer documentation and repository-level metadata.

