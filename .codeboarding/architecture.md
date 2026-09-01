# Architecture

## Overview

Codex is an AI coding agent written in Rust, entered primarily through the Interactive Terminal UI & CLI, which pairs a large terminal UI with a headless CLI and terminal plumbing. The core runtime is the Rust Agent Core Engine, whose agent execution loop drives the turn/protocol model and thread/rollout state. Around that core, the Client/Server App Platform exposes the agent programmatically via protocol definitions, daemon, and JSON-RPC transports, Backend API Connectivity & Authentication handles ChatGPT/OpenAPI clients and login flows, and Model Providers & Local Runtimes abstracts providers like Ollama and LM Studio.

## Architectural Patterns

- Cargo Workspace / Multi-Crate Monorepo (microkernel-with-modules design)
- Client-Server (Agent-as-a-Service)
- Layered Hub-and-Spoke
- Tool-Use / ReAct Agent Loop
- Sandboxed Execution Broker (Defense-in-Depth)
- Plugin/Extension Architecture
- Event-Driven / Message-Protocol Boundaries
- Polyglot Facade

## Project Context

- **Project Type:** AI Coding Agent CLI / Local Agent Runtime
- **Domain:** AI/ML

## Tech Stack

`Python`, `Node.js/TypeScript`, `Gin`, `Pydantic`

## Common Commands

## Key Entry Points

_No standard entry points detected._

## Modules

_Each module links to a per-module keyword file listing its native symbols (file/function/class names kept verbatim for exact grep), ranked by importance. The exact formula depends on the module's graph density: dense graphs use `0.30·bridge + 0.30·usage + 0.15·type + 0.15·activity + 0.10·exported`; sparse graphs (calls hidden behind runtime dispatch) use `0.20·bridge + 0.20·usage + 0.15·type + 0.15·activity + 0.15·exported + 0.15·file_hub`. See each keyword file's header for the rule that produced its scores. Agents read a module's keyword file on demand._

### Rust Agent Core Engine

The heart of the system: the agent execution loop, turn/protocol model, thread and rollout state.

### Interactive Terminal UI & CLI

User-facing interactive frontends: the large TUI (1,500+ files) and the headless CLI, plus terminal plumbing.

### Client/Server App Platform

Server binaries and transports that expose Codex programmatically (protocol definitions, daemon, JSON-RPC transport, remote exec server).

- Keywords: [`keywords/3.md`](keywords/3.md) — 1 scored symbol(s)

### Backend API Connectivity & Authentication

HTTP/websocket clients, OpenAPI models, and login/credential flows for ChatGPT/OpenAI backend access.

### Model Providers & Local Runtimes

Provider abstraction and local model runtimes for Ollama/LM Studio, plus model metadata management.

### Sandboxing & Execution Safety

OS-level isolation and approval enforcement for agent-run commands and patches.

- Keywords: [`keywords/6.md`](keywords/6.md) — 22 scored symbol(s)

### MCP, Connectors & Tooling Ecosystem

MCP client/server implementation, external connectors, and the built-in tool surface (file search, shell, git).

### Extensibility & Agent Capabilities

The extension/plugin framework and higher-level agent features layered on core (skills, prompts, memories, goals, guardian).

- Keywords: [`keywords/8.md`](keywords/8.md) — 168 scored symbol(s)

### Configuration, Persistence & Session Context

Config loading, home-directory layout, history, and session/context state.

### Cloud Services & Code-Mode Runtime

Cloud-backed task execution and the V8-powered "code mode" runtime for programmatic agent control.

### Observability, Diagnostics & Telemetry

OTel instrumentation, analytics, feedback, and build/diagnostic metadata.

### Language SDKs

Official Python and TypeScript SDKs that drive Codex via the app-server protocol.

- Keywords: [`keywords/12.md`](keywords/12.md) — 200 scored symbol(s)

### npm Distribution Layer

The codex-cli npm package that packages and ships the compiled Rust binaries.

- Keywords: [`keywords/13.md`](keywords/13.md) — 9 scored symbol(s)

### Build & Tooling Infrastructure

Bazel/Nix build system, dependency patches, vendored third-party code, and repo-wide scripts.

- Keywords: [`keywords/14.md`](keywords/14.md) — 200 scored symbol(s)

