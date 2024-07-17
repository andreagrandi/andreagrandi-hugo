---
title: "Python: it is now() time to migrate from utcnow()"
date: 2024-07-17
categories: 
- Python
tags: 
- python
- development
- programming
- datetime
- language
- changes
- deprecation
- timezone
slug: "python-now-time-to-migrate-from-utcnow"
description: "Python utcnow() method is not timezone aware, and Python 3.12 is deprecating it. Learn how to migrate your code to use now() instead."
image: "cover-python-utcnow.png"
---

This morning I randomly found this post from **Miguel Grinberg**: [It's Time For A Change: datetime.utcnow() Is Now Deprecated](https://blog.miguelgrinberg.com/post/it-s-time-for-a-change-datetime-utcnow-is-now-deprecated).

The main point is that Python `utcnow()` method is **not timezone aware**, and **Python 3.12 is deprecating it**. Therefore, you should start migrating your code to use `now()` instead.

## Current state until Python 3.11

Until Python 3.11, the `utcnow()` method returns a `datetime` object, and you would use it like this:

```python
>>> from datetime import datetime
>>> datetime.utcnow()
datetime.datetime(2024, 7, 17, 12, 17, 9, 835551)
```

The issue with this method is that **it doesn't include timezone information**, so you can't be certain if the time is in UTC or not.

## Changes in Python 3.12

In Python 3.12, the `utcnow()` method is being deprecated. The new method to use is `now()`, with the appropriate parameter to make it timezone aware:

```python
>>> from datetime import datetime, timezone
>>> datetime.now(timezone.utc)
datetime.datetime(2024, 7, 17, 12, 20, 21, 831261, tzinfo=datetime.timezone.utc)
```

## Start migrating now

The good news is that **you can start migrating your code now**, even if you are not using Python 3.12 yet. This way, when you upgrade to Python 3.12, you won't have to worry about this change.
