# Architecture

## Overview

This is an interactive AI coding agent delivered as a terminal-based CLI, with the CLI Entry & Distribution module (the user-facing binary and its npm wrapper) serving as the main entry point that parses arguments and routes subcommands. Interactive use is handled by the Terminal UI (TUI), while the App & Exec Server Stack exposes the same agent for headless, IDE, and non-interactive execution via the app-server and exec-server. At the core of the runtime is the Agent Core Engine, which owns the session/conversation loop, tool execution, and the core-client event protocol, backed by Cloud Backend & Authentication for OpenAI/ChatGPT API clients, login flows, and cloud tasks.

## Architectural Patterns

- Monorepo with polyglot workspace boundaries (Rust core, npm
- Cargo workspace / layered crate architecture (small single-purpose
- Hub-and-spoke agent kernel (codex-rs/core as orchestration hub for
- Client–server with protocol contract (JSON-RPC app-server, app-server-client, app-server-daemon,
- Plugin/extension architecture (codex-rs/ext with guardian-v2, memories, goal, web-search,
- MCP (Model Context Protocol) boundary for first-class external
- Defense-in-depth sandboxing (execpolicy, linux-sandbox, process-hardening, shell-escalation, network-proxy wrapping
- Event-sourced/session persistence (thread-store, agent-graph-store, rollout, thread-manager, memories)
- Hexagonal architecture flavor (TUI/SDK interfaces decoupled from engine

## Project Context

- **Project Type:** AI Coding Agent Platform / CLI Developer Tool
- **Domain:** AI/ML

## Tech Stack

`Python`, `Node.js/TypeScript`, `Gin`, `Pydantic`

## Common Commands

## Key Entry Points

_No standard entry points detected._

## Modules

_Each module links to a per-module keyword file listing its native symbols (file/function/class names kept verbatim for exact grep), ranked by importance. The exact formula depends on the module's graph density: dense graphs use `0.30·bridge + 0.30·usage + 0.15·type + 0.15·activity + 0.10·exported`; sparse graphs (calls hidden behind runtime dispatch) use `0.20·bridge + 0.20·usage + 0.15·type + 0.15·activity + 0.15·exported + 0.15·file_hub`. See each keyword file's header for the rule that produced its scores. Agents read a module's keyword file on demand._

### Agent Core Engine

The central orchestration layer handling the session/conversation loop, tool execution, patch application, prompt templates, and the core-client event protocol.

### Terminal UI (TUI)

The interactive terminal front-end rendering sessions, slash commands, and terminal-aware behavior.

### CLI Entry & Distribution

The user-facing binary and its npm wrapper providing argument parsing, subcommand routing, and package install/shim logic.

- Keywords: [`keywords/3.md`](keywords/3.md) — 9 scored symbol(s)

### App & Exec Server Stack

Headless/long-running server surfaces: the app-server for IDE/daemon-style integration and exec-server for non-interactive execution, plus their transports and clients.

- Keywords: [`keywords/4.md`](keywords/4.md) — 1 scored symbol(s)

### Cloud Backend & Authentication

Integration with the OpenAI/ChatGPT backend: API clients, OpenAPI-generated models, login/auth flows, cloud config, and cloud tasks.

### MCP, Plugins & Extensibility

Extensibility surfaces: MCP client, Codex-as-MCP-server, hooks, skills, connectors, and the ext/ extension layer.

- Keywords: [`keywords/6.md`](keywords/6.md) — 168 scored symbol(s)

### Sandboxing & Security

Command execution isolation and policy enforcement: Linux/Windows sandboxes, bubblewrap, execpolicy, network interception, and process/credential hardening.

- Keywords: [`keywords/7.md`](keywords/7.md) — 22 scored symbol(s)

### Model Providers & Transport

Provider abstraction and networking plumbing: OpenAI/oss provider selection, model catalog management, HTTP/WebSocket clients, local-model adapters, and the responses-API proxy.

### State, Persistence & Memory

Durable session state: rollout/resume files with tracing, thread store, conversation history, agent memory and identity, and graph storage.

### Code Mode / Embedded V8

The JavaScript "code mode" execution subsystem: protocol, host, and runtime crates running deterministic agent-authored code on an embedded V8.

### Language SDKs

Official client SDKs for driving Codex programmatically — Python and TypeScript — which consume the server protocol and ship with the binary.

- Keywords: [`keywords/11.md`](keywords/11.md) — 1289 scored symbol(s)

### Build & Release Infrastructure

Cross-language build and packaging: Bazel modules/rules/toolchains, third-party portability patches, dev/release scripts, lint tools, and root build manifests.

- Keywords: [`keywords/12.md`](keywords/12.md) — 309 scored symbol(s)

### Shared Foundation & Utilities

Cross-cutting crates consumed by nearly every other Rust module: general utils, config loading, Codex home management, filesystem/git/shell helpers, telemetry, and observability.

### Documentation

User and contributor documentation: installation, configuration, sandboxing, execpolicy, skills, and slash-command references.

