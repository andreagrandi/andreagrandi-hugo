---
title: "CuteSoma (Soma.fm client) ported to BlackBerry10"
date: 2013-01-03
categories: 
- BlackBerry
- Programmazione
- Qt
slug: "cutesoma-soma-fm-client-ported-to-blackberry10"
draft: false
---

During these Christmas holidays I've ported the N9 version of
**CuteSoma** to **BlackBerry10** platform, thanks to the BB10 Alpha
device that RIM gave to me and thanks in particular to my friend
[**Cornelius Hald**](https://twitter.com/corneliushald) that helped me
with porting.

The porting itself was quite easy after all: if you have a Qt
application that uses **MeeGo** Qt components, you have to switch to
**Symbian** components (they're more portable and support higher
resolutions) and to do it I suggest you follow the informations on this
blog
post <http://www.johanpaul.com/blog/2011/12/porting-meego-qt-components-apps-to-symbian/>

If you need more detailed informations about Symbian Qt Components, you
can also read this nice blog post from Cornelius
Hald <http://kodira.de/2012/12/qt-components-on-blackberry-10/>

## How does it look

So, what's the result of my porting? Well, first of all a couple of
screenshots

[![IMG\_00000004](IMG_00000004-180x300.png){ width="180" height="300" }](IMG_00000004.png) 
 
[![IMG\_00000005](IMG_00000005-180x300.png){ width="180" height="300" }](IMG_00000005.png)

## Source Code

And finally the source
code: [https://github.com/andreagrandi/CuteSoma/tree/bb10  
](https://github.com/andreagrandi/CuteSoma/tree/bb10)The application
will be published soon in the BlackBerry App World and you will have it
available in time for the BlackBerry 10 launch!

