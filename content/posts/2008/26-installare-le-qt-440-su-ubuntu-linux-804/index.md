---
title: "Installare le Qt 4.4.0 su Ubuntu Linux 8.04"
date: 2008-05-08
categories: 
- Linux
- Programmazione
- Qt
- Ubuntu (IT)
tags: 
- 4.4.0
- hardy
- installazione
- librerie
- multipiattaforma
- Programmazione
- Qt
- sviluppo
- Ubuntu (EN)
slug: "installare-le-qt-440-su-ubuntu-linux-804"
draft: false
---

[![QtLogo](qt_logo.thumbnail.png)]()

Da pochi giorni la **[Trolltech](http://trolltech.com/)** ha rilasciato la
[versione 4.4.0](http://trolltech.com/products/qt/learnmore/whats-new)
delle proprie librerie multipiattaforma Qt. La versione corrente di
Ubuntu (la 8.04) contiene al momento le librerie Qt nella versione
4.3.4.

Gli sviluppatori che utilizzano le Qt potrebbero voler installare
l'ultima release delle librerie, per testare le nuove funzionalità o per
verificare il funzionamento di una propria applicazione con questa
particolare versione.

La buona notizia è che non c'è bisogno di scaricarsi i sorgenti delle
**Qt 4.4.0** e ricompilarli, perchè il team di Ubuntu ha già preparato i
pacchetti per la Ubuntu Hardy.

Per installarli è necessario abilitare il repository chiamato
**`hardy-backports`** andando su**System->Administration->Software Sources**. 

A questo punto la versione **4.4.0** dovrebbe essere disponibile tra gli aggiornamenti di
sistema. Basterà quindi un **`apt-get upgrade`** per procedere
all'aggiornamento.

