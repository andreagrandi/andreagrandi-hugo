---
title: "Announcing logbasset 0.5.0"
date: 2026-05-20
categories:
- Development
- Tools
tags:
- scalyr
- logging
- cli
- open-source
- golang
- log-analysis
slug: "announcing-logbasset-0-5-0"
description: "logbasset 0.5.0 is out, bringing a compact output mode with pager integration, bounded retries with rate-limit handling, machine-readable command metadata, and token redaction in verbose logs."
image: "logbasset.png"
---

## Introduction

[**logbasset**](https://github.com/andreagrandi/logbasset) is an open source command-line tool, written in Go, for accessing and analyzing [Scalyr](https://www.dataset.com/) logs. It's a from-scratch rewrite of Scalyr's original Python client, focused on the read-only operations you actually reach for day to day: `query`, `power-query`, `numeric-query`, `facet-query`, `timeseries-query`, and a live `tail`. Being a single Go binary, it's trivial to distribute and run — no virtual environment to set up — and it plays nicely with CLI coding agents, which increasingly need reliable command-line access to services. If you want the full background, I covered it in the [original release post](/posts/2025/releasing-log-basset-open-source-cli-access-scalyr-logs/).

## What's new in 0.5.0

Version [0.5.0](https://github.com/andreagrandi/logbasset/releases/tag/v0.5.0) is mostly about making logbasset more pleasant and more robust in everyday use. Here are the highlights:

- **Compact output mode with pager integration** — browsing large result sets is now far more readable straight from the terminal.
- **Bounded retries with backoff** — API requests automatically recover from transient failures instead of giving up.
- **Rate-limit handling** — throttled requests are detected and retried gracefully, so queries no longer break under load.
- **API token redaction** — Scalyr tokens are stripped from verbose request payload logs, making it safe to share debug output.
- **Machine-readable command metadata** — particularly handy when logbasset is driven by CLI coding agents.
- **Go 1.26.1** — the toolchain has been upgraded from Go 1.25.
- **Better tests and docs** — end-to-end CLI tests, installation smoke tests, and a README expanded with query recipes and troubleshooting guidance.

## Installation

Install via Homebrew (macOS/Linux):

```bash
brew tap andreagrandi/tap
brew install logbasset
```

Or grab a binary from the GitHub [release page](https://github.com/andreagrandi/logbasset/releases), or build from source:

```bash
git clone https://github.com/andreagrandi/logbasset
cd logbasset
make build
```

## Conclusion

logbasset 0.5.0 keeps the same simple, read-only workflow while making it nicer to use and more dependable under load. If you work with Scalyr logs, give it a try — and if you have feedback or ideas, feel free to [open an issue](https://github.com/andreagrandi/logbasset/issues) or send a pull request 🙂
