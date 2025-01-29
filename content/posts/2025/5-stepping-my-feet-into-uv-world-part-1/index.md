---
title: "Stepping my feet into uv world - part 1"
date: 2025-01-29
categories: 
- Howto
tags:
- uv
- python
- virtual
- venv
- virtualenv
- pip
- rust
- nox
- speed
- performance
- astral
- pyenv
- package
- manager
slug: "stepping-my-feet-into-uv-world-part-1"
description: "I just started using uv for a few things and I'm sharing my experience."
image: "uv-speed.png"
---

I heard about [`uv`](https://docs.astral.sh/uv/) and [**Astral**](https://astral.sh) last year and as I previously mentioned in [this blog post]({{< ref "22-building-healthy-sustainable-funding-model-opensource.md" >}}), I did (and still have) have some concerns about them.

By the way, inspired by some work a colleague of mine is doing, I wanted to give it a chance and I checked if I could start using it without disrupting my `pyenv` [workflow]({{< ref "1-install-python-with-pyenv-and-pyenvvirtualenv-create-virtual-environment-with-specific-python-version-macos.md" >}}).

**Note:** Even if you don't want to migrate away from your favourite Python environment and virtualenv manager, there are a few ways to use it to speed up your existing configuration, so stay with me.

## What is uv?

`uv` is a package manager for **Python** which is written in **Rust**, it's extremely fast and it's becoming the favourite package manager across the Python community. As usual, please refer to the official website for more details: [https://docs.astral.sh/uv/](https://docs.astral.sh/uv/)

## Installing uv

It seems obvious but before proceeding with this tutorial, you need to install `uv`. There are a few different ways described in the official [documentation](https://docs.astral.sh/uv/getting-started/installation/), but if you are using **MacOS** and also use `brew`, you can install it with:

```shell
brew install uv
```

## Using uv pip

`uv` reimplements `pip` so instead of doing `pip install -r requirements.txt` you can do `uv pip install requirements.txt` (or similar), and believe me: It's faster!

This is a `pip` command I used to upgrade the dependencies in the virtual environment of one of the work projects (I only renamed the project name)

```python
❯ uv pip install -U -r requirements/base.txt
Using Python 3.12.8 environment at: /Users/andrea/.pyenv/versions/3.12.8/envs/my-project
Resolved 74 packages in 879ms
Prepared 8 packages in 1.50s
Uninstalled 8 packages in 300ms
Installed 8 packages in 28ms
 - alembic==1.14.0
 + alembic==1.14.1
 - attrs==24.3.0
 + attrs==25.1.0
 - boto3==1.35.98
 + boto3==1.36.2
 - botocore==1.35.99
 + botocore==1.36.8
 - deprecated==1.2.15
 + deprecated==1.2.18
 - s3transfer==0.10.4
 + s3transfer==0.11.2
 - sentry-sdk==2.19.2
 + sentry-sdk==2.20.0
 - structlog==24.4.0
 + structlog==25.1.0
```

The speed is impressive! I almost thought the command had failed because it finished so quickly. You can find more details in the docs: [https://docs.astral.sh/uv/pip/packages/](https://docs.astral.sh/uv/pip/packages/)

## Using nox[uv]

For the same project, we use [`nox`](https://nox.thea.codes/en/stable/) as a wrapper to run tests and it takes care of creating specific virtual environments. By default it uses `virtualenv` but there is a simple trick to make it use `uv`.

First you need to install `nox[uv]`

```shell
uv tool install 'nox[uv]'
```

Then you just need to set this environment variable:

```shell
export NOX_DEFAULT_VENV_BACKEND=uv
```

That's it! I can't provide the full output of our test suite, but I timed (`time nox -s test ...`) the execution and by using `uv` as backend, our virtual environment is created **13 seconds faster**!

## Conclusion

I used "part 1" as suffix for this blog post, because I'm sure these experiments will continue in the next days, by using more of the available `uv` tools. Once I've learned more, I will share my experience again.
