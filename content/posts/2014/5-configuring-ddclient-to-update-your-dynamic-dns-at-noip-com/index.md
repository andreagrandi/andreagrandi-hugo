---
title: "Configuring ddclient to update your dynamic DNS at noip.com"
date: 2014-09-02
categories: 
- HowTo
tags: 
- howto
- linux
- dns
slug: "configuring-ddclient-to-update-your-dynamic-dns-at-noip-com"
draft: false
aliases:
  - /2014/09/02/configuring-ddclient-to-update-your-dynamic-dns-at-noip-com/
---

[**noip.com**](http://noip.com) is one of the few dynamic DNS free
services that are reliable to use. If you have, like in my situation, a
RaspberryPi connected to your home DSL and you want it to be always
reachable without knowing the current IP address (the IP could change if
you have a normal DSL service at home), you need a dynamic DNS service.

To update the noip.com one you just need **ddclient** a tool that is
available in Raspbian/Debian repository. You can install it with this
command:

```shell
sudo apt-get install ddclient
```

then you just need to edit **/etc/ddclient.conf**

```shell
protocol=dyndns2
use=web, web=checkip.dyndns.com/, web-skip='IP Address'
server=dynupdate.no-ip.com
login=yourusername
password=yourpassword
yourhostname.no-ip.org
```

and restart the client:

```shell
sudo /etc/init.d/ddclient restart
```

That's all! Please remember that noip.com **free accounts** have a
**limitation**: they need to be confirmed every 30 days (you will
receive an email and you need to click on the link contained to update
your DNS).

