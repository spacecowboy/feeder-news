---
title: "Changes to read status in 2.5.0"
date: 2023-08-08T12:00:57+02:00
draft: true
---

Today I'd like to demonstrate a change to the read status in `2.5.0`. This is probably best shown in
[video](https://youtube.com/shorts/b-sH-giJwDs?feature=share).

In short though, from `2.5.0`, read items will not immediately disappear from the view. Instead they will remain until you either

1. Swipe them away
2. Toggle show read / unread
3. Navigate to a different feed
4. Restart the app

This has a couple of benefits.

* You accidentally close an article and decide you want to read more or star it. Well now it's not gone, it's right in front of you.
* The list is the same before opened the article as when you closed it - so no visual jumps or janky animations.
* Marking as read on scroll feels much smoother because items aren't disappearing which would cause all other items to slightly re-position themselves.
* Mark as read on scroll actually works on tablets and grid view now.

There are still a couple of tweaks possible here but overall I like this change a lot and think it solves several small annoyances people have reported.

Tomorrow, let's talk about the expanded OPML import/export.
