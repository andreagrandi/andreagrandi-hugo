---
title: "Using AI tools for coding: good or bad?"
date: 2024-03-09
categories:
- Personal Opinion
tags: 
- AI
- tools
- coding
- GPT
- ChatGPT
- GitHub Copilot
- LLM
- Large Language Models
- hallucination
- assistance
slug: "using-ai-tools-for-coding-good-or-bad"
description: "Every now and then, my Mastodon or LinkedIn timelines are full of messages either praising or condemning the use of AI tools for coding. Are they good or bad then? As usual I think the truth is in the middle, or to be more precise: it depends on how you use them."
image: "ai-tools-cover.webp"
---

Every now and then, my Mastodon or LinkedIn timelines are full of messages either praising or condemning the use of AI tools for coding.

Are they **good or bad** then? As usual I think the truth is in the middle, or to be more precise: **it depends on how you use them**.

## Context

In the last couple of years, thanks to the advancements in the field of **Large Language Models** (also known as **Generative AI**) a few "AI tools" have been made available, to help developers with coding tasks.

Tools like **GitHub Copilot** or **ChatGPT** are being used more frequently by developers. They can either open **new possibilities** (like helping us to write code in a language we are not familiar with) or just **speed up tasks** we would do in a different (often slower) way.

## Beware of hallucinations

Before we get into good or bad examples, it's important to remember that by definition, LLMs (large language models) can **hallucinate**, which means that under certain conditions (which can occur unexpectedly) the **model can make certain things up**.

Even ChatGPT reminds us about this, infact at the bottom of every page you will find:

> ChatGPT can make mistakes. Consider checking important information.

## An example of Good usage

Before the existance of ChatGPT, whenever I had to do something I didn't know exactly how to do it, my first "go-to" tool was Google.

> Example: "How do I find duplicated SQL rows with the same field?"

I would search the thing I wanted to do, read a couple of blog posts talking about the subject, figure out if something was possible and then refining my search to find some code examples (usually on Stack Overflow) which then I had to adapt to my existing code base, after reading some documentation.

Asking the **same question to ChatGPT produced a correct** (at least in my case) **SQL query along with an explanation** of the syntax being used (I tested this query on a local database, adapting field names to my own and it produced the expected result).

I still had to adapt the produced code to my needs (renaming fields, inserting this script in a larger context etc...) but I certainly **saved a lot of time** compared to the previous workflow.

AI tools are **like driving assistance systems**: **they are not supposed to drive for you**, but they will help you to maintain the correct distance from the front vehicle, stay below the speed limits, warn you of you start overtaking a car when another one is close behind you etc...

## Conclusion

AI tools can be very helpful with coding tasks. Like any tool, we are in charge of using them correctly and ensuring the end result is accurate. Paying attention to avoid introducing false information or non working code is crucial.
