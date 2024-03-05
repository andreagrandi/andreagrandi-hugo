---
title: "iA Writer Authorship: a brilliant feature with a problematic implementation"
date: 2024-03-05
categories:
- Writing
- Review
tags: 
- iA
- Writer
- iAWriter
- writing
- review
- feedback
- iOS
- Hugo
- Authorship
- GPT
- YAML
- issue
slug: "ia-writer-authorship-brilliant-feature-problematic-implementation"
description: "iA Writer recently introduced Authorship to help writers keep track of external contributors. The feature is brilliant but its implementation creates issues for static websites generators. I implemented a workaround and wrote some feedback for iA."
image: "ia-writer-authorship-cover.webp"
---

I recently started using **[iA Writer](https://ia.net/writer)** to edit my MarkDown files on iPad and I'm honestly quite impressed by its simplicity.

With the latest version they introduced a feature called [Authorship](https://ia.net/writer/support/editor/authorship) which basically helps you to keep track of external contributors.

For example, suppose you asked a friend (or even ChatGPT) to write a conclusion for one of your articles, you copy-paste the text on your article and you start editing it. How do you keep track of what you or the other source wrote? With the Authorship feature, text edited by you will be rendered in a different way, so you can distinguish it.

I think this is a brilliant idea and even if I don't make much usage of GPT to write my posts (almost none so far), I may use it in the future.

## The problem

The problem with this feature is that if you enable it for one of your documents, iA Writer will add an "hidden" `Authorship` section at the end of the file. 

This section won't be visible in iA while editing the text, but it will be visible in any other editor.

In my case, I plan to use iA Writer to write my blog posts, which I then push to GitHub using [Working Copy](https://workingcopy.app/), where they are finally transformed by Hugo to my static website.

**Unless I edit the file with a different editor**, if I submit my article as is, **Hugo** (but even Pelican, or Jekyll etc... basically any engine which doesn't know how to handle this block of information) **will render the Authorship block into the final HTML page**, which is something nobody really wants.

## Possible solutions

I asked iA people on Mastodon about this issue and [they told me](https://mastodon.online/@ia/112037948788436778) they had considered different options but in any case something will break for someone.

I agree, it's not easy to find a solution which can cover every possible case, but I still think there could be margin for improvement.

### Saving Authorship in an external file

If these additional data was saved in an external file, it would be much easier to exclude it from the built pages. By the way, this would mean spreading the information across different files, making it more difficult to maintain.

### Using YAML metadata

Adding the Authorship as metadata could be the best option, for a couple of reasons.

iA Writer already makes use of YAML metadata where you can add information, so existing users would be used to see something at the beginning of the file which is not their content.

Any unknown metadata is usually ignored by static websites generators (at least Hugo and Pelican behave in this way) so the Authorship won't be rendered in the final HTML page.

## A workaround for Hugo

While I hope iA will consider giving alternative options in the future, I've written a simple script you can use to remove all Authorship blocks from any MarkDown file found in your content.

{{< gist andreagrandi 800e5e33ec05f8d51f61a1cdc4fc4d91 strip-annotation.sh >}}

Please note that this will remove any Authorship block from your MarkDown files, even if you include them in a code block. If you want to improve the script, feel free to do it and let me know.

## Conclusion

The introduction of the Authorship feature in iA Writer presents a creative solution for managing and distinguishing between original content and external contributions within documents. 

While the feature offers significant advantages for content creators seeking to track their collaborations, it also introduces challenges, particularly in the integration with static site generators like Hugo.

My advice is that, as users, we give some **constructive feedback** to iA (you can contact them at `support+newfeature@ia.net`) to let them know how to improve this feature.

Additionally, if you are more familiar with GitHub, you can discuss this specific feature directly in their [repository](https://github.com/iainc/Markdown-Annotations).
