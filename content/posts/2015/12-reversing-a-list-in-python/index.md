---
title: "Reversing a List in Python"
date: 2015-10-11
categories: 
- Development
tags: 
- lists
- Python
- reversed
slug: "reversing-a-list-in-python"
draft: false
---

Sometimes we need to reverse the order of the elements in a Python list.
While there can be many different ways of implementing this task, I
found three in particular that I appreciate for different reasons. Let's
define first a list of integers that we will reverse later.

```python
l = [1, 2, 3, 4, 5, 6]
```

### List slicing

This method can be a bit obscure at first read, but basically it slices
the whole list proceding in the reverse order:

```python
[input]: print l[::-1]
[output]: [6, 5, 4, 3, 2, 1]
```

### Reversed method

We use the
**[reversed](https://docs.python.org/2/library/functions.html#reversed)** method
that returns an iterable object and a list comprehension to generate the
new list

```python
[input]: print [x for x in reversed(l)]
[output]: [6, 5, 4, 3, 2, 1]
```

### Swapping values in place

This last method is more verbose and it basically divides the list in
two parts and swaps the first with sixth, the second with fifth, etc...

```python
[input]:
for i in range(0, len(l) / 2):
    l[i], l[len(l) -1 -i] = l[len(l) -1 -i], l[i]
print l

[output]: [6, 5, 4, 3, 2, 1]

