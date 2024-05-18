---
title: "Truncating time when querying a PostgreSQL database"
date: 2024-05-18
categories: 
- SQL
tags: 
- Development
- SQL
- Programming
- Database
- Software
- Development
- PostgreSQL
slug: "truncating-time-in-postgresql-query"
description: "How to truncate time in a PostgreSQL query to get and compare dates without the time part."
image:
---

When you have to compare dates in a SQL query, you often want to ignore the time part. For example if you have two very common fields like `created_at` and `updated_at` and you want to know if they are the same day, you have to **truncate the time part**.

How to do this depends on the database you are using. Here is how you can do it in **PostgreSQL**.

```sql
SELECT * 
FROM users 
WHERE DATE(created_at) <> DATE(updated_at)
ORDER BY created_at DESC;
```

This query will return all the users where the `created_at` and `updated_at` fields are not on the same day, ignoring the time part.
