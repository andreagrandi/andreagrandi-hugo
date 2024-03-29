---
title: "A-GPS per Nokia N810"
date: 2008-06-27
categories: 
- Linux
- Maemo (IT)
tags: 
- a-gps
- gps
- maemo
- nokia
slug: "a-gps-per-nokia-n810"
draft: false
---

[![agps](agps1.jpg)]()

Insieme alla [nuova versione del firmware](http://maemo.org/news/announcements/view/os2008_feature_upgrade-reflash_your_tablet-for_the_last_time.html)
per Nokia N800/N810, Nokia ha rilasciato anche una utility che promette
di migliorare notevolmente i tempi di fix per il GPS del N810.

Si tratta di **agps-ui** ed è disponibile sia nei repository "Maemo
Extra", sia nel sito [Nokia Beta Labs](http://www.nokia.com/betalabs/agps-tablet). 
A-GPS sta per [**Assisted GPS**](http://it.wikipedia.org/wiki/Assisted_GPS) e si
tratta di una tecnica che "aiuta" il ricevitore GPS a sintonizzarsi con
i satelliti in un tempo assai minore da quello richiesto normalmente.

In sintesi, sia triangolando la posizione grazie all'ausilio delle celle
GSM, sia facendo indicare all'utente la posizione approssimativa di dove
ci si trovi, il ricevitore GPS cerca di connettersi a quei satelliti che
sa che sono visibili nella zona indicata, riducendo notevolmente il
tempo richiesto per fare il fix della posizione.

