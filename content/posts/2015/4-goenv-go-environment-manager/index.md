---
title: "Goenv - Go Environment Manager"
date: 2015-04-19
categories: 
- Go
- HowTo
- Programmazione
tags: 
- go
- golang
slug: "goenv-go-environment-manager"
draft: false
---

To briefly explain what
[**Goenv**](https://bitbucket.org/ymotongpoo/goenv) is, I will assume
you have previously worked with **Python**. Basically it's what
**Virtualenv** is for Python. Goenv (and it's wrapper **goof**) creates
a folder for a new project and set the `$GOPATH` env variable to that
folder path. At this point every time you do **go get**, the libraries
will be installed in that specific `$GOPATH`.

It's very important to use separate `$GOPATH` for each project, because
this allow us to use different library versions for each project and
**avoid version conflicts**.

## Installation

```shell
git clone https://bitbucket.org/ymotongpoo/goenv
cd goenv
go build -o goenv *.go
chmod +x goenv
sudo cp goenv /usr/bin
```

Goenv is now installed, we will now install its wrapper **goof**:

```shell
sudo cp shellscripts/goenvwrapper.sh /usr/bin
```

Edit `.bashrc` (or `.zshrc` if you use zsh) and append these lines:

```shell
export GOENVHOME=$HOME/goenvs
source /usr/bin/goenvwrapper.sh
```

## How to use it

To **create** a new go environment use **make**:

```shell
goof make go-test
Do you want to create all parental directory of '/Users/andrea/goenvs/go-test'? [y/N]: y
Environment /Users/andrea/goenvs/go-test created!
(go:go-test) ➜  go-test
```

To exit the go environment use **deactivate**:

```shell
(go:go-test) ➜  go-test  deactivate
go-test
```

To use an environment use **workon**:

```shell
go-test  goof workon go-test
(go:go-test) ➜  go-test
```

To show available environments use **show**:

```shell
(go:go-test) ➜  go-test  goof show
go-test
```

Goenv itself is not enough to manage Go packages. It would be like using
**Virtualenv** only and not using **pip** and **requirements**. In a
future post I will explain how to use
[**Godep**](https://github.com/tools/godep).

 

 

