---
title: "Quali sono i comandi bash che usate di piu'?"
date: 2008-08-05
categories: 
- Linux
- Ubuntu (IT)
tags: 
- bash
- Linux
slug: "quali-sono-i-comandi-bash-che-usate-di-piu"
draft: false
---

Prendendo spunto da alcuni post apparsi sulla versione inglese di Planet
Ubuntu, ho deciso di provare questo comando:

```shell
history | awk '{a[$2]++ } END{for(i in a){print a[i] " " i}}' | sort -rn | head
```

che dovrebbe stampare la lista dei comandi piu' digitati nella bash
della vostra macchina Linux. Il risultato è stato il seguente:

```shell
history | awk '{a[$2]++ } END{for(i in a){print a[i] " " i}}' | sort -rn | head 
4884 git
1023 eval
382 isort
381 docker-compose
379 nox
318 cd
305 ls
228 docker
224 pip
151 workon
```

interessante, non trovate?!

