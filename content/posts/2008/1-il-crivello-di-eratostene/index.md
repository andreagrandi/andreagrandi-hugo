---
title: "Il crivello di Eratostene"
date: 2008-01-30
categories: 
- Python
tags: 
- crivello
- eratostene
- numeri primi
- Python
slug: "il-crivello-di-eratostene"
draft: false
---

Questo codice Python di esempio, genera una lista di numeri primi che
vanno da 2 fino al numero passato come parametro.

```python
def eratostene(x):  
    primi = range(3, x + 1, 2)  
    for i in primi:  
        if(pow(i, 2) > x):  
            break  
        for j in primi:  
            if(i != j) and (j % i == 0):  
                primi.remove(j)  
                primi.insert(0, 2)
    return primi  

