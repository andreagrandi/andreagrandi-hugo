---
title: "How to install latest stable Node.js on Ubuntu"
date: 2013-02-08
categories: 
- HowTo
- Linux
- Programmazione
- Ubuntu (EN)
tags: 
- Javascript
- Node
- Node.js
- NodeJs
slug: "how-to-install-latest-stable-node-js-on-ubuntu"
draft: false
---

If you develop with [**Node.js**](http://nodejs.org) and you want to be
sure to have the latest stable version, luckly there is a PPA for it.
All you need is to follow these instructions:

```shell
sudo apt-get install python-software-properties python g++ make
sudo add-apt-repository ppa:chris-lea/node.js
sudo apt-get update 
sudo apt-get install nodejs npm
```

That's it!

Reference: <https://github.com/joyent/node/wiki/Installing-Node.js-via-package-manager>

