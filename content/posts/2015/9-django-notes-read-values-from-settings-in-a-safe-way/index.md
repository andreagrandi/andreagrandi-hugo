---
title: "Django Notes: read values from settings in a safe way"
date: 2015-08-29
categories: 
- Django
- HowTo
- Programmazione
- Python
tags: 
- Django
- getattr
- Python
- settings
slug: "django-notes-read-values-from-settings-in-a-safe-way"
draft: false
---

Working on **Django** projects I find very often that many developers
access the values that are defined in **settings** in this way

```python
from django.conf import settings

my_value = settings.MY_SETTING
```

What happens if `MY_SETTING` has not been defined in **settings.py**?
The code will raise an error and crash, of course. How can we make the
code more reliable? We could *try/except* the code block that tries to
read the value and maybe set a value if we get an exception, but this
would not be a clean way to do this job.

A cleaner way to do it is to use **getattr** in this way:

```python
from django.conf import settings

my_value = getattr(settings, 'MY_SETTING', 'my-default-value')
```

**getattr** will try to read `MY_SETTING` value from **settings.py**,
if the value doesn't exist `my_value` will be assigned with
`'my-default-value'`

