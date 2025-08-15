---
title: "Claude Code Status Line Script"
date: 2025-08-15
categories: 
- Development
- AI
- Tools
tags:
- claude-code
- shell
- bash
- productivity
- automation
- status-line
- ccusage
- claude
- antropic
- statusline
slug: "claude-code-status-line-script"
description: "A shell script that displays project information and cost tracking from ccusage in Claude Code's status line, helping developers monitor their AI coding sessions and usage patterns."
image: "cc-statusline.png"
---

## Introduction

A few days ago, Anthropic released an update for Claude Code that adds an [interesting feature](https://docs.anthropic.com/en/docs/claude-code/statusline): a new command named `/statusline`, which will create a script to fetch and show useful information in the app’s status bar and automatically add the configuration for it.

You can either let Claude generate the script for you, or provide your own.

## Installation

To install my script, you need to download the bash script from [this location](https://gist.github.com/andreagrandi/362c1fc77909b202476aba9b57cb0145) save it in `~/.claude/statusline-script.sh`, make it executable with 

```shell
chmod +x ~/.claude/statusline-script.sh
```

and add this configuration in `~/.claude/settings.json`

```json
...
"statusLine": {
    "type": "command",
    "command": "~/.claude/statusline-script.sh"
}
...
```

## Features

As you can see from the above screenshot, the script will display the following information:

```shell
📁 logbasset | 🦫 1.24.5 | 🌿 10-logging | 🤖 Opus 4.1 | 💸 $0.00 | 💰 $14.64/day
```

- 📁 current folder
- 🦫 language version (in this case it's a Go app but for Python it will show `💼 (my-app) | 🐍 3.12.9`)
- 🌿 git branch name
- 🤖 current model
- 💸 cost of the current session
- 💰 total cost for the day
- ⏱️ time left for the current session

The app uses `ccusage` to fetch costs.

## Conclusion

In the last few days there has been an explosion of scripts and small apps which can provide a status line for Claude Code. I decided to give it a try and do my custom one. I hope it can be useful for other people too 😉
