---
title: "Changes to OPML import/export in 2.5.0"
date: 2023-08-09T22:00:57+02:00
draft: false
---

In `2.5.0`, an OPML export will include

* feed specific settings, such as *Fetch full articles by default* and *Open items by default with*
* global settings such as *Theme*, *Article style*, and maybe most significantly
* your **BLOCK LIST**.

This is a nice quality of life change if you ever need to re-install Feeder, or you want to copy everything over to another device. I finally read what the OPML specification allows (turns out a lot!) and this is an example of the data structure:

```
<?xml version="1.0" encoding="UTF-8"?>
<opml version="1.1" xmlns:feeder="https://nononsenseapps.com/feeder">
  <head>
    <title>
      Feeder
    </title>
  </head>
  <body>
    <outline title="Example Tag" text="Example Tag">
      <outline feeder:notify="false" feeder:fullTextByDefault="false" feeder:openArticlesWith="" feeder:alternateId="false" title="Example Feed" text="Example Feed" type="rss" xmlUrl="http://example.com/1/rss.xml"/>
    </outline>
    <feeder:settings>
      <feeder:setting key="pref_feed_item_style" value="SUPER_COMPACT"/>
      <feeder:setting key="pref_body_text_scale" value="1.6"/>
      <feeder:setting key="pref_is_mark_as_read_on_scroll" value="true"/>
      <feeder:blocked pattern="foo"/>
    </feeder:settings>
  </body>
</opml>
```

## Warning about shared block lists

This means it's possible to share only a block list with someone else. Just open it in a text editor and remove everything else.

For example like this:

```
<?xml version="1.0" encoding="UTF-8"?>
<opml version="1.1" xmlns:feeder="https://nononsenseapps.com/feeder">
  <head>
    <title>
      Feeder
    </title>
  </head>
  <body>
    <feeder:settings>
      <feeder:blocked pattern="foo"/>
    </feeder:settings>
  </body>
</opml>
```

There is currently no kind of validation for these patterns. So, hypothetically, the file you import has been modified, then it might get you stuck in a crash loop after import.

So please don't modify the individual patterns outside of Feeder for now.
