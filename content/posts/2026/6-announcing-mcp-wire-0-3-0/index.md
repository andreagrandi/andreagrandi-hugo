---
title: "Announcing mcp-wire 0.3.0"
date: 2026-06-14
categories:
- Development
- Tools
- AI
tags:
- mcp
- model-context-protocol
- cli
- coding-agents
- claude-code
- opencode
- codex
- golang
- open-source
- configuration
slug: "announcing-mcp-wire-0-3-0"
description: "mcp-wire 0.3.0 is out with a new doctor command, richer TUI metadata, machine-readable metadata for agents, and more curated MCP services including GitHub, Notion, and Linear."
image: "mcp-wire-logo.png"
---

## Introduction

[**mcp-wire**](https://github.com/andreagrandi/mcp-wire) is a small Go CLI that installs and configures MCP (Model Context Protocol) servers across multiple AI coding tools — Claude Code, Codex, and OpenCode — from a single interface. If you're new to the project, the [original release post](/posts/2026/releasing-mcp-wire-tool-easily-configure-mcps-coding-agents/) covers the motivation and the basics.

Version [0.3.0](https://github.com/andreagrandi/mcp-wire/releases/tag/v0.3.0) is a usability-focused release. It makes the tool easier to understand, safer to use, and more useful when driven by agents.

## What's new in 0.3.0

- **`mcp-wire doctor`** — a new read-only diagnostics command that tells you which targets are installed, where their config files live, what feature flags are enabled, and where mcp-wire keeps its own files and credentials. It's the first thing to run when something looks off.
- **Richer TUI service list** — the install wizard now shows each service's source, transport, install method, and auth type right in the list, so you know what you're picking before you select it.
- **`mcp-wire metadata`** — prints a stable, machine-readable JSON document describing targets, services, transports, scopes, and feature flags. Handy for scripts and CLI coding agents that need to inspect capabilities without driving the interactive UI.
- **More curated services** — GitHub, Notion, and Linear join the bundled catalog, all OAuth-based and ready to install out of the box.
- **Safer credential storage** — the credentials directory and file permissions are now tightened and re-applied on every write, so stored credentials stay owner-readable only.
- **Smoother installs** — this release adds install smoke tests for release artifacts and Homebrew, plus golden tests for TUI and plain wizard output, which should make upgrades more reliable.

## Installation

Install via Homebrew (macOS/Linux):

```bash
brew tap andreagrandi/tap
brew install mcp-wire
```

Or build from source:

```bash
git clone https://github.com/andreagrandi/mcp-wire
cd mcp-wire
make build
./bin/mcp-wire
```

## Conclusion

mcp-wire 0.3.0 keeps the same simple workflow — pick a service, pick your targets, apply — while making it easier to diagnose issues, browse services, and integrate with automation. If you use more than one AI coding tool and you're tired of keeping MCP configs in sync by hand, give it a try.

The full source code and release notes are available on GitHub: https://github.com/andreagrandi/mcp-wire

It's open source and contributions are welcome, especially new service definitions. If you have feedback or run into issues, feel free to [open an issue](https://github.com/andreagrandi/mcp-wire/issues) or send a pull request 🙂
