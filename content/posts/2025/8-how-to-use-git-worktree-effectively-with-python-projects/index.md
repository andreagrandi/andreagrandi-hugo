---
title: "How to use git worktree effectively with Python projects"
date: 2025-07-13
categories: 
- Development
tags:
- git
- python
- worktree
- development
- productivity
- version-control
slug: "how-to-use-git-worktree-effectively-with-python-projects"
description: "Learn how to leverage git worktree to manage multiple branches simultaneously in Python projects, improving your development workflow and productivity."
image:
---

## Introduction

Working with multiple branches in Python projects can be challenging, especially when you need to switch between different features, bug fixes, or versions while maintaining separate virtual environments and dependencies.

[`git worktree`](https://git-scm.com/docs/git-worktree) provides an elegant solution to this problem by allowing you to check out multiple branches simultaneously in separate working directories, but it doesn't keep Python development requirements in mind.

I won't go into details about how to use `git worktree` in this post (for that you can check the manual I linked), 
but I will explain its limitations and present my workaround.

## The Problem with Traditional Branch Switching

When working on Python projects, switching branches often means recreating the virtual environment, 
reinstalling the dependencies, setting the env variables etc...

`git` isn't tight to a specific programming language, so by default it can't do any of this.

In my case I create the virtual environments with `uv` (like I explain in [this other post]({{< ref "6-using-uv-to-install-python-create-virtualenv.md" >}})) but this won't be automatically available in the worktree folder and it won't be active.

## The Helper Script

To streamline the git worktree workflow with Python projects, I've created a helper script that automates the common tasks:

[https://gist.github.com/andreagrandi/542b438bf0017d93aff2b640037e3ce1](https://gist.github.com/andreagrandi/542b438bf0017d93aff2b640037e3ce1)

The script basically does this:

- it uses `git worktree` as usual
- it creates a symbolic link to the existing `.venv/`
- it creates a symbolic link to the existing `.envrc` (which is where I keep my env variables, automatically activated by `direnv`)
- it runs `direnv allow` to give direnv permissions to read the env variables

**Note:** You will need to customise the script replacing `/my-project-worktrees/` with the name of the folder where you intend to keep your worktrees and `/my-project/` with the main folder of your project.

## Conclusion

Git worktree is a great tool for working on multiple branches, but it needs some extra setup for Python projects. The helper script makes this much easier by automatically linking your virtual environment and environment variables to new worktrees, saving you time and hassle.
