---
title: "Scanner Mustek ScanExpress 1248 USB su Ubuntu Linux"
date: 2008-12-17
categories: 
- HowTo
- Linux
tags: 
- mustek
- scanner
slug: "scanner-mustek-scanexpress-1248-usb-su-ubuntu-linux"
draft: false
---

[![scanner mustek](se1248ub.jpg)](http://www.mustek.de/eng_/html/produkte/se1248ub.htm)

Lo scanner [**Mustek ScanExpress 1248 USB**](http://www.mustek.de/eng_/html/produkte/se1248ub.htm) è
pienamente compatibile con Linux, però purtroppo non basta connetterlo
per farlo funzionare. **Ubuntu Linux 8.10** non distribuisce il firmware
necessario al suo funzionamento, però è possibile reperirlo ed
installarlo con molta facilità.

Per prima cosa dobbiamo assicurarci di avere il modello esatto di questo
scanner. Per scoprirlo è sufficiente dare il comando **lsusb** da
terminale. Dovremmo ottenere una stringa come la seguente:

```shell
Bus 002 Device 003: ID 055f:021f Mustek Systems, Inc. SNAPSCAN e22
```

A questo punto possiamo scaricare il suo firmware da [un sito](http://www.meier-geinitz.de/sane/gt68xx-backend/) che li raccoglie
tutti (quelli che sono compatibili ovviamente):
**[http://www.meier-geinitz.de/sane/gt68xx-backend/firmware/SBSfw.usb](http://www.meier-geinitz.de/sane/gt68xx-backend/firmware/SBSfw.usb)**

Questo file va messo all'interno della cartella
**`/usr/share/sane/gt68xx/`** (occorrono i permessi di root per poterlo
fare, quindi il file andra' copiato tramite il comando **`sudo cp SBSfw.usb /usr/share/sane/gt68xx/`** ).

Infine dobbiamo assicurarci di aver installato tutti i pacchetti
necessari a farlo funzionare:

```shell
sudo apt-get install sane libsane sane-utils libsane-extras xsane xsane-common
```

Lo scanner è adesso pronto per funzionare.

**Nota:** nella **Ubuntu 12.04** la
directory **/usr/share/sane/gt68xx/** non è presente di default e va
creata manualmente con **sudo mkdir **/usr/share/sane/gt68xx/****

