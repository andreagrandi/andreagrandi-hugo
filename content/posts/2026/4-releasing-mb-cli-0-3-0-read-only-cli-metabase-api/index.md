---
title: "Releasing mb-cli 0.3.0: a read-only CLI for the Metabase API"
date: 2026-05-22
categories:
- Development
- Tools
- CLI
tags:
- metabase
- cli
- command-line
- api
- golang
- open-source
- coding-agents
- data-exploration
slug: "releasing-mb-cli-0-3-0-read-only-cli-metabase-api"
description: "mb-cli 0.3.0 is out: a read-only CLI for the Metabase API, with new exploration recipes, collection browsing, parameter discovery and session token authentication."
---

## What is mb-cli?

[**mb-cli**](https://github.com/andreagrandi/mb-cli) is a read-only command-line interface for the Metabase API, written in Go. It lets you explore databases, inspect schemas and run ad-hoc queries straight from the terminal, without opening the Metabase UI. It was designed with AI coding agents in mind, so tools like Claude Code can investigate data on their own, and it redacts PII (emails, names, phone numbers) from results by default so the output is safe to hand to an agent.

## What's new in 0.3.0

Version 0.3.0 focuses on making Metabase resources easier to discover and on giving agents the context they need to explore an instance without guessing. Here's what's new:

- **Exploration recipes**: a cookbook of exploration recipes to discover Metabase resources step by step.
- **Collection management**: new commands to browse collections and discover their metadata.
- **Parameter discovery**: new commands to find the parameters available on cards and dashboards.
- **Context-aware requests**: requests now carry context, with configurable timeout settings.
- **Session token authentication**: added support for authenticating via `MB_SESSION_TOKEN`, alongside the existing API key option.

This release also improves error handling by classifying errors from typed JSON instead of matching message strings, strengthens the PII redaction tests, and adds mocked CLI-level integration tests for the new exploration flows.

## Installation

You can install mb-cli via Homebrew (macOS/Linux):

```bash
brew tap andreagrandi/tap
brew install mb-cli
```

Or build it from source:

```bash
git clone https://github.com/andreagrandi/mb-cli
cd mb-cli
make build
```

## Conclusion

The full source code and release notes are available on GitHub: https://github.com/andreagrandi/mb-cli

mb-cli is open source and contributions are welcome. If you have feedback or run into issues, feel free to [open an issue](https://github.com/andreagrandi/mb-cli/issues) or send a pull request 🙂
