---
title: "Migrating from Pelican to Hugo"
date: 2024-02-25
categories: 
- Development
tags: 
- Pelican
- Python
- blog
- writing
- Hugo
- migration
- Golang
- Go
slug: "migrating-from-pelican-to-hugo"
draft: false
description: "I recently migrated my blog from Pelican to Hugo. In this article I will explain why I decided to do it and how I did it."
image: migrating-from-pelican-to-hugo.webp
---

As you may have noticed, the blog has a new look. I recently migrated from Pelican to Hugo and I am very happy with the result. I've known Hugo for a long time, but I never had the opportunity to use it in a real project. With a little help from a couple of friends, I was able to complete the migration in a few days.

## Why did I migrate?

I have been using Pelican for a long time and I have always been very happy with it. It is a great static site generator and it has served me well. However, I recently started having issues with PIP dependencies. For example one of the plugins required an older version of a sub dependency, which was causing conflicts with other plugins. I tried to fix it, but it was a rabbit hole and I decided to give Hugo a try.

In addition to the dependency issues, I realised that I was using a theme that was not being maintained anymore. The author himself had moved to Hugo and I was left with an outdated theme.

Last but not least, the javascript library I was using to generate the indexing and search functionality was also not being maintained anymore.

## How did I migrate?

Both Pelican and Hugo are static site generators, and they both expects the content to be in Markdown format. This made the migration process a lot easier. By the way, there are some differences in the syntax of the Markdown files, and other few differences in the front matter (the metadata inside the MarkDown file), so I decided to write a small script to convert the files.

You can find the full script here https://gist.github.com/andreagrandi/0a7bf6e217d6561b00b6a5de6211ddaa but I have to warn you that it's very specific to my blog (because of how I structured the content in Pelican and because of how I'm structuring it in Hugo) and it may not work for you. However, it can be a good starting point if you want to migrate from Pelican to Hugo.

Other than migrating the content, I had to find a new theme and customise it to my needs. This honestly took most of the time. I'm really bad with CSS and I had to learn a lot of new things. I'm still not 100% happy with the result, but I think it's good enough for now.

The theme I picked comes with a built-in search functionality, so I don't have to worry about that anymore.

Finally I had to rewrite the CircleCI configuration file to build the site with Hugo instead of Pelican. This took me a bit of try and error, but I managed to get it working.

## Conclusion

I'm very happy with the result. The site is easy to manage and I don't have to worry about dependencies anymore. I'm also happy with the new theme, even if I still have to tweak it a bit (ie: comments don't seem to be working yet). I wish I had done this migration earlier, but I'm glad I did it now. I hope you like the new look and if you find any issues, please let me know.
