---
title: "Why add an agent skill to a CLI that already has a context command?"
date: 2026-06-07
categories:
- Development
- Tools
- AI
tags:
- cli
- coding-agents
- agent-skills
- claude-code
- skills
- logbasset
- golang
- open-source
slug: "why-add-agent-skill-cli-context-command"
description: "logbasset already self-documents for agents through a context command, so why add an installable agent skill on top? Because self-documentation and discovery are two different problems."
image: "logbasset.png"
---

## Introduction

[**logbasset**](https://github.com/andreagrandi/logbasset), my open source CLI for querying [Scalyr](https://www.dataset.com/) logs, was already built to be friendly to AI coding agents. It ships a `context` command that prints an agent-facing reference — every command, flag, output format, time syntax, and even a list of flags that *look* plausible but don't exist — plus a `schema` command that emits the same information as machine-readable JSON.

So when I sat down to add an installable [agent skill](https://www.skills.sh/), I had a fair question to answer first: if the binary already documents itself, what's the skill even for?

## Self-documentation isn't discovery

The `context` command answers *how* to use logbasset. But it only helps an agent that has **already decided** to reach for logbasset in the first place. Nothing tells the agent "this tool exists, and it's the right one when the user mentions Scalyr logs." That's a separate problem — discovery — and a context command can't solve it, because the agent has to know to run it.

An agent skill fills exactly that gap. A skill is matched by its description, so it acts as the trigger layer: *"when the user wants to investigate, search, or tail Scalyr/DataSet logs, use logbasset."* Once it fires, it hands off to the binary.

## A thin skill, not a second copy of the docs

The obvious mistake would be to stuff the whole command reference into the skill. That instantly creates a second source of truth that goes stale the moment I add a flag — and now I'm maintaining the same documentation in two places.

So the skill does almost nothing. It tells the agent: check that `logbasset` is installed, then run `logbasset context` and `logbasset schema` to load the *current* reference, then build the query. It deliberately lists no flags of its own. A CLI change can never make it lie, because it never claims anything specific — it just points at the binary, which is always right.

That combination is the whole idea: the `context` command makes logbasset **usable** by an agent, and the skill makes it **discoverable** — with near-zero maintenance, because the skill delegates instead of duplicating.

## Try it

If you use logbasset with a coding agent, install the skill alongside the binary:

```bash
npx skills add andreagrandi/logbasset
```

It works with any [skills.sh-supported agent](https://www.skills.sh/) — Claude Code, Codex, Cursor, and others — and the binary stays a separate install.

## Conclusion

Giving your CLI a `context` or `schema` command is great: it lets an agent use the tool correctly. But a small, thin skill on top is what gets the agent to reach for it in the first place. If your CLI already self-documents, you're most of the way there — a discovery layer is a cheap, high-leverage addition, as long as you keep it thin and let the binary remain the source of truth.
