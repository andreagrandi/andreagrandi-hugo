---
title: "Building a healthy and sustainable funding model for open source software"
date: 2024-09-07
categories: 
- Opinion
tags:
- opensource
- funding
- sustainability
- business
- community
- software
- vc
- investment
- contributing
- python
- money
- rust
- astral
- ruff
- uv
- pydantic
- fastapi
- django
- flask
- sqlalchemy
- development
- programming
- software
- libraries
- frameworks
- languages
- tools
- companies
- donations
slug: "building-healthy-sustainable-funding-model-opensource-software"
description: "How we can build a healthy and sustainable funding model for open source software which is being used by thousands of companies and developers around the world."
---

If you work in software development, chances are high that your company is **using open source software to build their products**. Nowadays open source software is nearly everywhere: it can be included in your operating system, in commercial software or it can be responsible for hosting your website or your application.

In this post I will focus mainly on **languages, libraries and frameworks** which are being used to build software applications, because they are the components I'm most familiar with.

## Context

Suppose your company needs to build a new software service which is going to be offered as an API. You will need to pick a **language** (for example **Python**), possibly **a web framework** (like **Django**, **Flask** or **FastAPI**) and some additional **libraries** (like **SQLAlchemy**, **requests**, etc...) to build your service.

Usually developers will pick the tools they are most familiar with, or the tools which are most popular in the community, but very few people ask themselves: **who is behind these tools? Who is maintaining them? Who is fixing the bugs? Who is adding new features?**

And most importantly: **how are these people being paid?** (You are not expecting them to work for free, right? 😏)

## The current funding models

Some languages and frameworks have a no profit foundation behind them (ie: [**Python**](https://www.python.org) has [**Python Software Foundation**](https://www.python.org/psf-landing/), [**Django**](https://www.djangoproject.com) has [**Django Software Foundation**](https://www.djangoproject.com/foundation/), etc.) which are responsible for managing the project and the community around it.

They can receive a lot of **independent donations** or being **funded by big companies** like Google or Microsoft (ie: **Guido Van Rossum**, the creator of **Python**, was previously working for Google and now he is currently working for Microsoft).

**Big companies** (those earning billions every year) usually don't have any problem spending some money to sustain the tools they also use, but this also means they **can have a big influence on the direction** the project is taking.

Some smaller projects (like [FastAPI](https://fastapi.tiangolo.com)) are being funded entirely by **independent donations**: [https://fastapi.tiangolo.com/fastapi-people/#sponsors](https://fastapi.tiangolo.com/fastapi-people/#sponsors) but this is not a sustainable model for the long term because there is no guarantee that the donations will keep coming.

### The Venture Capital model

A different way to fund open source projects is through private investors or **venture capital**. For example [`pydantic`](https://pydantic.dev) (a library which is also used by FastAPI) has recently received a **$4.7 million investment** from a few VCs: [https://techcrunch.com/2023/02/16/sequoia-backs-open-source-data-validation-framework-pydantic-to-commercialize-with-cloud-services/](https://techcrunch.com/2023/02/16/sequoia-backs-open-source-data-validation-framework-pydantic-to-commercialize-with-cloud-services/)

Another quite recent example (which has sparked a lot of discussions in the Python community) is the case of [**Astral**](https://astral.sh), a small company backed by VCs which are developing a couple of tools for the Python community: [`ruff`](https://astral.sh/ruff) which is a code linter and [`uv`](https://github.com/astral-sh/uv) which is a Python package and project manager written in [**Rust**](https://www.rust-lang.org).

### The opinions from the Community

With specific regard to **Astra**, there is an **interesting conversation** happening in a [Mastodon thread](https://social.jacobian.org/@jacob@jacobian.org@jacob@jacobian.orgian.org/113091418140504394), and from what I've seen, the **opinions are quite divided**.

Some of them are concerned because this company is using **Rust** to implement these tools. This could cut Python developers out from directly contributing to the project, because they would need to learn a new language to do so.

Others are concerned because the company is backed by **VCs**, and they **could cut funds** at any time, leaving the project in an abandoned state. This of course is a valid concern, but since the project is open source, the community could fork it and continue the development. 

Another issue that seems to be mentioned by a few people is the fact that Astral doesn't seem to have a **clear business model** (at least until the time of this article). When asked directly, they have been vague about how they intend to monetize their projects and for this reason some **people are being cautious before adopting their tools**.

Some people are being optimistic instead and looking at this funding as a **good thing**, because observing how quickly `ruff` and `uv` have evolved in so little time, they recognise **a lot can be done when people are allowed to work full time** on a project.

### My own opinion

In the specific case of `ruff` and `uv`, I personally don't have anything against the fact that they are written in Rust. My mantra is **"use the right tool for the job"**, and if Rust is the right tool for the job (according to their tests, linting the whole CPython code base **only takes 0.16s** with `ruff`, while it takes **11.63s** with `flake8` and even **60s** with `pylint`), then so be it.

By the way, relying on **VCs for funding is a double-edged sword**: on one side you now have a lot of money to hire people and let them work full time on the project. This ensures the **development will proceed at fast pace** and issues will be addressed quickly. On the other side, other companies and community members could initially be attracted by the tool, decide to adopt features which are not available (nor compatible with) in other similar tools and **eventually find themselves locked in a proprietary ecosystem** (check what recently happened to the data scientists community using [**Anaconda**](https://www.theregister.com/2024/08/08/anaconda_puts_the_squeeze_on/)).

## What could we do instead

**I think an alternative** and mid ground solution to the ones described above **exists**: each company should **fund the projects** they use and rely on most and / or they should **allow employees** to dedicate some time to **contribute back** to these projects.

### Funding projects

Let's pick for example the 5 top components a company could rely on: **Python, FastAPI, SQLAlchemy, Pydantic and PostgreSQL**.

The company should allocate a yearly budget for these components and donate regularly to the projects. Many companies have no issues purchasing licenses and seats for the services they use, so why donating regularly should be a problem?

By having many companies donating to a project, **we avoid that a single company has too much influence** on the direction of development. If a single company decides to stop funding a component, there would be many other continuing to support it.

Small projects (those with a single lead developer) could **use the money** income to be able **to work full time** on it. Larger projects could **hire more people** to work full time. The necessary structure and organisation should reflect the size of the project itself.

This would be a **win win situation**. **Developers** could **work on something they love** and being paid for it. **Companies** could trust the components they use even more because with people working full time on it, it's more **unlikely the project can be abandoned**.

This is quite similar to the funding model of [**Django Rest Framework**](https://www.django-rest-framework.org/#funding).

### Allowing employees to contribute back

Sometimes project owners need some direct help fixing bugs, preparing releases etc... another way of contribute could be **allowing employees to dedicate some work time to contribute back** directly. This can have multiple advantages: employees can **work on something fun** and they can **learn new things** (reminder: often employees leave a company because they want to work on more interesting stuff and because they are not learning enough in their current role) while **projects** can **get additional** (even if not regular) **help**.

## Conclusion

I'm convinced **a more sustainable way for funding open source projects is possible**. As **software developers** we **can have an high impact on companies** (spreading the word, speaking at conferences, leading by example etc...) and this can be beneficial both for the longevity of existing projects and for the safety of companies.

What do **you** think about this possibility?
