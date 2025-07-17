---
title: "Comparing Claude Code vs OpenCode (and testing different models)"
date: 2025-07-17
categories: 
- Development
- AI
tags:
- claude-code
- opencode
- ai-tools
- development
- productivity
- comparison
- models
slug: "comparing-claude-code-vs-opencode-testing-different-models"
description: "A practical comparison of Claude Code and OpenCode (using Sonnet-4, Gemini Pro 2.5, and GPT-4.1), evaluating their reliability, code generation quality, and integration with developer workflows based on a real-world task."
image: "opencode.png"
---

## Introduction

In the past few days [**Claude Code**](https://github.com/anthropics/claude-code) had some reliability issues and was sometimes unavailable. I started looking for alternative solutions (for context: through my job, I already have paid subscriptions to [**GitHub Copilot**](https://github.com/features/copilot) and [**ChatGPT**](https://chatgpt.com)) but I wanted something that would better fit my workflow.

While I initially used Copilot in **VSCode**, in the last month I’ve mostly been using VSCode for small fixes, code reviews, and navigating the codebase (asking questions using `@workspace` still beats any other tool I’ve tried so far). I was primarily using Claude Code (I have a **Pro** subscription, which is usually enough for my needs).

I discovered [**OpenCode**](https://opencode.ai) and liked that it’s not tied to a single provider—it can be used with most existing subscriptions and API keys (in particular, **you can use your existing Claude Code Pro/Max or GitHub Copilot subscription**).

Having recently worked on a task at work (which I admit it's simple to medium difficulty), after work I decided to give the same task to Claude Code and OpenCode (used with different models) logged in with my GitHub Copilot subscription.

## The Task

I won't (and I can't) go into specific details of the task, since it's work stuff, but I can say it was about:

- add a new field `new_field` to `ExistingEntity` entity
- add `new_field` to `ExistingModel` model
- create an `alembic` migration
- fix existing tests

## The results

Overall, the code produced by these models was correct (with one exception), but in a few cases I had to make some manual fixes or request a second iteration, specifying what needed to be corrected.

### Claude Code

Claude was, hands down, the best overall. The initial iteration had a couple of minor problems:

- the field was marked as not nullable while I wanted it nullable, but I didn't specify this initially so it couldn't guess it correctly
- the default value given to the field was quite "odd"

### OpenCode (copilot/sonnet-4)

OpenCode (configured with the Anthropic `sonnet-4` model from Copilot) unsurprisingly produced almost the same code as Claude Code (with the same minor problems), but it also reformatted some existing code without permission. Last but not least, it added two tests (like Claude), but it removed six existing ones 😨

I had to iterate and tell it to fix, which was very quick to do.

### OpenCode (copilot/gemini-pro-2.5)

Gemini… oh dear! I’m not sure if it’s the model itself or if it’s just not optimized for agentic coding (though it should be, since Google just released `gemini-cli` 🤷🏻‍♂️). It started hallucinating (I could see this as the code was being written) about existing fixtures, added a new unnecessary one, duplicated some existing code, and completely rewrote an existing class—in a bad way—instead of importing it. I honestly didn’t try a second iteration; I just scrapped the whole thing.

### OpenCode (copilot/gpt-4.1)

Last, but not least, I switched to `gpt-4.1` from the Copilot subscription. The first iteration wasn’t perfect (it was probably a bit inferior to the one produced by `sonnet-4`) and needed a couple of fixes, but once I told it what to correct, it did so quickly, and the final version was perfect.

Bonus point: using `gpt-4.1` through a Copilot subscription offers **unlimited** usage 🎉

## Conclusion

The best tool I’ve tried so far remains Claude Code, but I have to admit that OpenCode with `sonnet-4` could replace it soon (especially considering it was released less than a month ago). Even `gpt-4.1` wasn’t bad, and honestly, using it through OpenCode yields much better results than using it from within VSCode.

All three models I used with OpenCode tried to reformat existing code. This must be an OpenCode bug, which I’ve tried to mitigate with a rule in the `AGENT.md` file.

I will keep testing OpenCode over the next few days, and maybe I’ll write a dedicated review about it.
