---
title: "Social Connect QML plugin: access Facebook, Twitter from your Qt/QML applications"
date: 2012-08-13
categories: 
- Maemo (EN)
- MeeGo
- Programmazione
- Qt
- Ubuntu (EN)
tags: 
- library
- Mobile
- nokia
- QML
- Qt
- Social
slug: "social-connect-qml-plugin-access-facebook-twitter-from-your-qtqml-applications"
draft: false
---

[**Social Connect**](https://projects.developer.nokia.com/socialconnect)
is a library written in **Qt** that allows applications to easily
connect to services like **Facebook** and **Twitter**. Recently I had
the opportunity to work on this library improving it and adding support
for **Instagram** (work is still in progress but it's almost finished).

[![social connect](SocialConnect.png)](SocialConnect.png)

The **main features** of this library are:

- Out-of-the-box support for Facebook and Twitter
- Integrated authentication implementation
- Simplified common interface for all supported services
- Provides interfaces for native API calls
- Design enabling easy addition of new services e.g. LinkedIn

If you are writing an application that needs to access these services,
this could be the library for you. It can be extended to support even
other services like LinkedIn, Flickr etc... and I would like to invite
people to contribute to the code. The library has been tested with **Qt
4.8.1** on **Ubuntu Linux 12.04** but it should be compatible with any
other versions/platforms.

For more informations about getting started with the library, I suggest
you to give a look at this
page <https://projects.developer.nokia.com/socialconnect/wiki/GettingStarted>

