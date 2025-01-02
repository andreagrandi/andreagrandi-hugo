---
title: "My ZSH history"
date: 2025-01-02
categories: 
- System
tags:
- zsh
- shell
- history
- bash
- system
- macos
slug: "my-zsh-history"
description: "A list of my most used commands in my terminal"
image:
---

Inspired by [this post](https://nicolaiarocci.com/my-most-used-command-line-commands/) from **[Nicola Iarocci](https://nicolaiarocci.com)**, I decided to check my own ~bash~ **zsh** history:

- 1082 git
- 99 cd
- 95 nox
- 38 pip
- 37 ls
- 33 pytest
- 29 brew
- 26 code
- 19 curl
- 16 pyenv

Even for me, my biggest usage of the terminal is because of **git** 😅

You can produce your own list by using this command: `history | awk '{print $2}' | sort | uniq --count | sort --numeric-sort --reverse | head -10`
