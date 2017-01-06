---
title: How do I protect embedded content?
categories: questions
tags: shortcodes, s2if
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/201
---

If you want to protect embedded content on a Post/Page, you can wrap the embed code in an s2Member shortcode conditional (see **WordPress Dashboard → s2Member → API / Scripting → Simple/Shortcode Conditionals**) to prevent the embed code from showing for users who don't have the necessary access.

The following example only allows users with **Level 1** access to see the embedded YouTube video:

```text
[s2If current_user_is(s2member_level1)]
    <iframe width="420" height="315" src="https://www.youtube.com/embed/qlKn-I-0W6U" frameborder="0" allowfullscreen></iframe>
[/s2If]
```

See also: [\[s2If /\] Simple Shortcode Conditionals](https://s2member.com/kb-article/s2if-simple-shortcode-conditionals/)
