---
title: "Self hosting a Copilot replacement: my personal experience"
date: 2024-03-03
categories: 
- Review
- Tutorial
tags: 
- AI
- LLM
- Ollama
- GPT
- llama2
- Python
- API
- REST
- Copilot
- GitHub
- hosting
slug: "self-hosting-copilot-replacement"
description: "Being able to run a Large Language Model locally also means to be able to use existing models (fine tuned for coding) to implement a self hosted solution to replace GitHub Copilot. In this post I will talk about my personal experience."
image: "self-hosting-copilot-cover.webp"
---

For my job (Software Developer) I make a daily use of tools like [GitHub Copilot](https://github.com/features/copilot) and [ChatGPT](https://chat.openai.com/). I want to explore alternative solutions which can be hosted autonomusly, without relying on an external service.

## Disclaimer

Before I continue, let me clarify that these are **tools** which makes my job faster, they don't do the job for me: a wrong assumption made by so many people is that AI tools will do the work for you. 

This is quite **not true**. You are still responsible of knowing what to do, understanding the problem, asking the right questions and knowing what to do with the answers.

If you regularly search for stuff on Google or any other engine, to find examples in blog posts or Stack Overflow, read someone else example and then adapt the code for your needs, there is nothing wrong automating this: **you are still in charge of the final result**.

## The experiment

After I recently experimented with [local LLMs using Ollama]({{< ref "/posts/2024/6-ollama-running-llm-locally" >}}), I wanted to figure out if I could use some of these models to **replace GitHub Copilot**.

My intent is not to save some money (my company pays for these tools) or for privacy reasons (it would be pointless to keep your code "secret" from GitHub if you use it to host it), but to **find out how good these alternative tools are** and... for fun!

## Setup and available resources

The laptop I'm using is a MacBook Pro with **M2 Pro** CPU and **32 GB RAM**.

This machine must be able to run my basic **requirements**, which are:

- Slack
- Docker (running my work containers)
- VSCode
- Safari / Chrome

Let's see if it can also run a Copilot replacement.

## Tested models and extensions

Basically, to run a Copilot replacement, you need to be able to run an LLM and use one of the available extensions for VSCode (in my case I use VSCode, but similar extensions exist for other IDEs).

I'm running the models locally using [Ollama](https://ollama.com). If you need to know how to use it, you can refer to my [previous post]({{< ref "/posts/2024/6-ollama-running-llm-locally" >}}).

The **models** I tested are:

- `stable-code:3b-code-q4_0`
- `codellama:7b-code-q4_K_M`
- `codellama:13b-code-q4_K_M`

The number before the `b` usually represents the number of parameters (**3 billions**, **7 billions**, **13 billions** etc...) and you approximately need **4 GB**, **8 GB** and **16 GB RAM** to use them.

[Meta](https://about.meta.com) has released models with **34 billions** and **70 billions** parameters, which are even more powerful, and you can find them here: [https://ollama.com/library/codellama](https://ollama.com/library/codellama) but you will need **64-128 GB RAM** to run them properly.

The extensions I tested are:

- **LLama Coder** https://marketplace.visualstudio.com/items?itemName=ex3ndr.llama-coder
- **Code GPT** https://marketplace.visualstudio.com/items?itemName=DanielSanMedium.dscodegpt
- **twinny** https://marketplace.visualstudio.com/items?itemName=rjmacarthy.twinny

## Results

The results I got have been quite mixed and **mostly depending on the LLM model** I was testing, rather than on the extension I was using.

A model like `stable-code:3b-code-q4_0` was quite **fast** to complete the code I was typing, **but very often** giving me **wrong** code or pure garbage (ie: the model wasn't even able to correctly structure a simple Python method or to maintain the correct indentation)

Models like `codellama:7b-code-q4_K_M` or `codellama:13b-code-q4_K_M` were giving me **better results** but despite having 32 GB RAM available and a quite fast CPU, they were **taking 3-4 seconds** to complete what I was typing, making themselves useless (at least for my use case).

**None of them was even remotely close to the speed and accuracy of GitHub Copilot**.

## Conclusion

While the idea of having a personal and private instance of a code assistant is interesting (and can also be the only available option in certain environments), **the reality is that achieving the same level of performance as GitHub Copilot is quite challenging**.

Despite these challenges, I think with time both available models and extensions **will get better** and better, improving their quality and maybe reducing the amount of required resources.

In case I missed some better model or extension, please feel free to **let me know** in the comments. I will be glad to do more tests and update this posts or write a new one in the future.

**In the mean time**, at least for my personale usage, I think I will **stick with GitHub Copilot**.
