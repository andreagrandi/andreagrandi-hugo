---
title: "Using uv to install Python and create a virtual environment"
date: 2025-01-30
categories: 
- Howto
tags:
- uv
- python
- virtual
- venv
- virtualenv
- pip
- macos
- rust
- speed
- performance
- astral
- pyenv
- package
- manager
slug: "using-uv-to-install-python-create-virtualenv"
description: "uv can be used to install and manage Python versions and virtual environments."
image:
---

Following my [previous post]({{< ref "5-stepping-my-feet-into-uv-world-part-1.md" >}}), today I wanted to see if I could replace my `pyenv` and `pyenv-virtualenv` [usage]({{< ref "1-install-python-with-pyenv-and-pyenvvirtualenv-create-virtual-environment-with-specific-python-version-macos.md" >}}) with `uv`.

## Install uv

If you haven't done it yet, you need to first install `uv` using either this method or one of the methods [described in the documentation](https://docs.astral.sh/uv/getting-started/installation/):

```shell
brew update
brew install uv
```

## Install Python

`uv` can detect Python versions installed in different ways in the system or it can install its own copies. You can check which ones are installed, using this command:

```shell
uv python list --only-installed
```

Now we are going to install the latest (at the time of writing) version of **Python**:

```shell
uv python install 3.13.1
```

## Create a virtual environment

Creating virtual environment with `uv` is quite easy. We can do it in this way:

```shell
uv venv --python 3.13.1 --prompt my-project
```

With `--python 3.13.1` we specify the Python version we want and with `--prompt my-project` we customise the text that will appear in the prompt.

As the output will say, we can simply activate the environment with this command:

```shell
source .venv/bin/activate
```

### Automatically activate the virtual environment

Running `source .venv/bin/activate` every time we enter the project directory can be boring. We can automate this by using [**direnv**](https://direnv.net).

`direnv` is a tool which can automatically set environment variables or run simple commands when we enter inside a directory.

You can install it with:

```shell
brew install direnv
```

Once it's installed, we need to add this configuration inside our `.zshrc`:

```bash
eval "$(direnv hook zsh)"
```

or, in case we are using `bash`, we need to do it inside `.bashrc`:

```bash
eval "$(direnv hook bash)"
```

At this point simply close and reopen your terminal (it's the quickest way to reload the configuration) and finally create a file named `.envrc` inside your project folder, containing these two lines (or append these two lines in case you are already using this file):

```shell
export VIRTUAL_ENV=$PWD/.venv
export PATH=$VIRTUAL_ENV/bin:$PATH
```

After you save this file and you get back to your terminal, you will get an error like this:

```shell
direnv: error /Users/andrea/Projects/my-project/.envrc is blocked. Run `direnv allow` to approve its content
```

Just run that command to allow direnv to load your configuration:

```shell
direnv allow
```

## Installing Python packages

At this point you can use `uv pip` (which is a drop in replacement for `pip` with a few [limitations](https://docs.astral.sh/uv/pip/compatibility/)) just like you would use `pip`:

```shell
uv pip install requests
```

## Make an alias for uv pip

If you are happy to use the `uv` version of `pip`, you can use it anywhere, even in virtual environments which are not managed by `uv`. You can create an alias by adding this to your `.zshrc` (or `.bashrc` etc...)

```shell
alias pip="uv pip"
```

This way, every time you invoke `pip`, you will use the `uv` version:

```shell
pip --version
```

## Conclusion

Using `uv pip`, `uv venv` and `uv python` you can definitely speed up Python installation, virtual environments creations and Python packages installation.

But `uv` is much more. You can also manage dependencies, [**lock them**](https://docs.astral.sh/uv/guides/projects/#uvlock) and do many other things. At this point I don't feel like switching completely to this tool, especially because a few things (like dependencies locking) are not standard across Python ecosystem and the risk is to use a workflow which is not supported by other existing tools (for example if you are using **dependabot** you won't be able to just use `uv.lock` file, you will need to [extract](https://docs.astral.sh/uv/pip/compile/) `requirements.txt` files)

My final advice is to use just the parts which are compatible with your existing workflow and wait until a standard for locking dependencies will be universally accepted, before jumping in with both feet.
