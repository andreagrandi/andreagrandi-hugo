---
title: "How to fix pip under Debian 6.0 (squeeze): ImportError: cannot import name parser"
date: 2013-05-02
categories: 
- HowTo
- Linux
- Programmazione
- Python
- Ubuntu (EN)
slug: "how-to-fix-pip-under-debian-6-0-squeeze-importerror-cannot-import-name-parser"
draft: false
---

The **pip** utility distributed with Debian 6.0 has a bug once you
upgrade it with **pip install -U pip**. You will easily get this error
when you try to install a new package with it:

```shell
root@worker2:~# pip install setproctitle
Traceback (most recent call last):
File "/usr/bin/pip", line 8, in 
from pip.baseparser import parser
ImportError: cannot import name parser
```

Luckly there is a very easy workaround:

```shell
easy_install pip
rm /usr/bin/pip
ln -sv /usr/local/bin/pip-2.6 /usr/bin/pip
pip install pip --upgrade
```

Reference: <http://blog.102web.ru/tag/virtualenvs/>

