---
title: "Skype on N770 (using Os2007 HE)"
date: 2007-12-10
categories: 
- HowTo
- Linux
- Maemo (EN)
- Skype
tags: 
- 770
- maemo
- nokia
- Skype
slug: "skype-on-n770-using-os2007-he"
draft: false
---

Great news for all **N770** users! Someone discovered that is possible to make **Skype**
run on N770 with **Os2007 HE**.

All you have to do is follow these steps:

1. Install skype-ui through Application Manager

2. Download [this package](http://catalogue.tableteer.nokia.com/certified/pool/chinook/user/s/skype/skype_1.7.62.48.5_armel.deb)
in your PC and extract the file named `skyhost`

3. Find a way to copy the file **skyhost** to your maemo device in
**`/usr/bin`**

4. execute this from root on your device:

`chown user:users /usr/bin/skyhost`

That's all! You can find more information on the [original post](http://www.internettablettalk.com/forums/showthread.php?t=12740).

