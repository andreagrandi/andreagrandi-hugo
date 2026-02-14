---
title: "Releasing mcp-wire: a tool to easily configure MCPs in coding agents"
date: 2026-02-14
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
slug: "releasing-mcp-wire-tool-easily-configure-mcps-coding-agents"
description: "Introducing mcp-wire, a CLI tool that installs and configures MCP servers across multiple AI coding tools like Claude Code, OpenCode, and Codex from a single, unified interface."
image: "mcp-wire-logo.png"
---

## Introduction

If you've been using AI coding agents like Claude Code, OpenCode, or Codex, you've probably noticed that each one has its own way of configuring MCP (Model Context Protocol) servers. Claude Code uses JSON, OpenCode uses JSONC, Codex uses TOML, and they all store things in different locations. Adding a new MCP service means manually editing the right config file for each tool you use.

I found myself repeating this process every time I wanted to add or update an MCP server, and it got old really fast.

[**mcp-wire**](https://github.com/andreagrandi/mcp-wire) is a CLI tool that does all of this for you. It installs and configures MCP servers across multiple AI coding tools from a single, guided interface.

## Why mcp-wire?

I use multiple coding agents depending on the task, and I want them all to have access to the same MCP services. Manually editing JSON, JSONC, and TOML config files across different tools is tedious and error-prone. I wanted a single command that would:

1. Detect which coding tools I have installed
2. Let me pick an MCP service to install
3. Handle credentials
4. Write the correct configuration to each tool's config file

So I built mcp-wire to do exactly that.

## How It Works

Run `mcp-wire` and you get a guided menu:

```text
$ mcp-wire
Use Up/Down arrows, Enter to select.
> Main Menu
  Install service
  Uninstall service
  Status
  List services
  List targets
  Exit
```

The install wizard walks you through the whole process step by step: pick a service, select one or more targets, review, and apply. No config files to find or edit by hand.

```text
$ mcp-wire install
Install Wizard

Step 1/4: Service
Use Up/Down arrows, Enter to select. Type to filter.
> Select service
  jira - Atlassian Rovo MCP server (OAuth)

Step 2/4: Targets
Detected targets:
  Claude Code (claude) [installed]
  OpenCode (opencode) [installed]
  Codex (codex) [installed]
[ ] Claude Code (claude)
[x] OpenCode (opencode)
[ ] Codex (codex)

Step 3/4: Review
Service: jira
Targets: OpenCode
Credentials: prompt as needed

Step 4/4: Apply
Installing to: OpenCode
  OpenCode: configured
Equivalent command: mcp-wire install jira --target opencode
```

If you prefer one-liners over menus, every action has a direct command equivalent:

```bash
mcp-wire install jira --target claude --scope project
mcp-wire uninstall sentry --target opencode
mcp-wire status
```

## Supported Targets

mcp-wire currently supports three coding agents:

- **Claude Code** (`claude`) - with user and project scope support
- **Codex** (`codex`)
- **OpenCode** (`opencode`)

It automatically detects which ones are installed on your system and only shows those as available targets.

## Scope-Aware Installs

For Claude Code, mcp-wire supports scoped installations:

- **user** (default): MCP service is available across all projects
- **project**: MCP service is only available for the current project

```bash
mcp-wire install jira --target claude --scope user
mcp-wire install jira --target claude --scope project
mcp-wire status --scope effective
```

The `effective` scope shows you the merged result of user and project configurations, so you can see exactly what's active.

## Bundled Services

mcp-wire comes with a few services out of the box:

- **context7** - Context7 documentation lookup MCP
- **jira** - Atlassian Rovo MCP server
- **sentry** - Sentry MCP server
- **playwright** - Playwright browser automation MCP

You can list what's available with `mcp-wire list services`.

## Adding New Services

One thing I'm particularly happy about is how easy it is to add new services. You don't need to write any Go code — just create a YAML file in the `services/` directory:

```yaml
name: example
description: "Example MCP"
transport: http
auth: oauth
url: "https://mcp.example.com/mcp"
env: []
```

For local command-based MCP servers (`stdio` transport):

```yaml
name: example-stdio
description: "Example local MCP"
transport: stdio
command: npx
args: ["-y", "@example/mcp-server"]
env: []
```

This is also the easiest way to contribute to the project: adding service definitions for MCP servers you use.

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

Complete source code is available on GitHub: https://github.com/andreagrandi/mcp-wire

## Conclusion

mcp-wire is a small tool that scratches a very specific itch: keeping MCP configurations consistent across multiple coding agents without the manual toil. If you use more than one AI coding tool and you're tired of editing config files by hand, give it a try.

It's open source and contributions are welcome, especially new service definitions. If you have feedback or run into issues, feel free to [open an issue](https://github.com/andreagrandi/mcp-wire/issues) or send a pull request 🙂
