---
title: "We need an evolved robots.txt and regulations to enforce it"
date: 2024-06-22
categories: 
- Opinion
tags: 
- ai
- robots.txt
- crawlers
- OpenAI
- Google
- Bing
- Perplexity
slug: "we-need-evolved-robotstxt-and-regulations"
description: "In the age of AI, existing robots.txt are not enough to express the rules for web crawlers. We need a new standard and regulations to enforce it."
image: "we-need-new-robots.png"
---

The `robots.txt` file is a simple text file that tells web robots (like search engine crawlers) which pages on your site to crawl and which not to crawl. It's a [standard](https://en.wikipedia.org/wiki/Robots.txt) that has been around for a long time and it's still used today.

Some examples of rules you can put in a `robots.txt` file are:

```txt
User-agent: *
Disallow: /private/
```

This rule tells all web robots to not crawl the `/private/` directory.

```txt
User-agent: Googlebot
Disallow: /users/
```

This rule tells Googlebot to not crawl the `/users/` directory.

## Then AI came

In the age of AI, the existing `robots.txt` specification is not enough to express the rules for web crawlers. We can only tell agent if they can or cannot crawl a certain path, but we cannot express more complex rules.

In my opinion we should be able to express more detailed rules, like:

- **Indexing:** should a web crawler be able to index the content?
- **Caching:** should a web crawler be able to cache the content?
- **LLM Training:** should a web crawler be able to use the content to train a language model?
- **Summarising:** should a web crawler be able to summarise the content?
- etc...

Some of the above things were not possible in the past and it should be up to the website owner to decide if they want their content to be used in such ways.

## Enforcing the rules

In addition to more detailed rules, **we need new regulations to enforce them**. It looks like the `robots.txt` file is not enough to stop certain companies from doing what they want.

As someone [recently found out](https://rknight.me/blog/perplexity-ai-is-lying-about-its-user-agent/), **Perplexity AI is using a fake user agent to crawl websites**, pretending to be a regular user. This is a clear violation of the rules specified in `robots.txt` file. This claim has recently been [confirmed by Wired](https://www.wired.com/story/perplexity-is-a-bullshit-machine/) and by [MacStories](https://www.macstories.net/stories/wired-confirms-perplexity-is-bypassing-efforts-by-websites-to-block-its-web-crawler/).

## Conclusion

As we have seen, having good rules is not enough if they are not enforced. In particular we need regulators to take care of complaints from content owners and **fine companies that do not respect the rules** (like Perplexity AI), because small content creators cannot afford to take legal actions against big companies.

As with every single thing, it's never "the tool", but rather "how you use it". AI itself can bring innovation in certain fields, but this can't be done at the expense of other people's work and rights.

### Disclaimer

Yes, of course the cover image has been generated with AI. It's far from perfect, but it's still better than my drawing skills. The content of this article instead is 100% human generated.
