---
title: "Announcing LastGo: Maemo/MeeGo client for Last.fm"
date: 2010-07-16
categories: 
- Linux
- Maemo (EN)
- MeeGo
- Programmazione
- Qt
tags: 
- client
- last.fm
- music
- N900
- nokia
slug: "announcing-lastgo-maemomeego-client-for-last-fm"
draft: false
---

While I'm still working to
[mSoma]({filename}/2010/6-announcing-msoma-maemomeego-client-for-somafm.md)
with Lorenzo Bettini, I decided to start writing another application. I
needed to write something from scratch to learn better how to use
**C++** and **Qt** libraries, so I decided to write a client for
[Last.fm](http://www.lastfm.com) service. The application is still in
full development, but you can already taste it if you have
**extras-devel** repository enabled on your **N900**. At the moment it
only supports basic radio features: tuning user's radio, playing a song,
skipping a song and displaying song informations.

[![lastgo](Screenshot-20100716-222755.png)](Screenshot-20100716-222755.png)

Other basic Last.fm features like scrobbling, marking a song as loved or
banned ecc.. are not supported yet, but of course they're planned for
the stable release. Please not that the application is still a bit
unstable even if it works for normal tasks.

If you are a [**Last.fm**](http://www.lastfm.com) subscriber and you
want to test it, please install it from **extras-devel** repository and
send me your feedback.

**Note:** since it's not allowed to use Last.fm API from a mobile phone
(due to API license restrictions) I cannot distribute a valid api key
with the application. I'm writing this software mainly to learn C++ and
Qt and for the future tablets and netbooks that will be based on MeeGo.
If you feel to assume the responsability, you can [download the api key
file](http://gitorious.org/lastgo/lastgo/blobs/raw/master/LastGo/apikey.xml)
and import it using "Import Api Key" that you can find in the
application menu.

