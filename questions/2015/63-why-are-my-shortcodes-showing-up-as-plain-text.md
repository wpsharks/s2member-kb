---
title: Why are my shortcodes showing up as plain text?
categories: questions
tags: troubleshooting, shortcodes
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/63
toc-enable: false
---

> My site all of a sudden stopped rendering my 's2Member-Pro-PayPal-Form' shortcode. Now the shortcode is rendering as text instead of the signup form that used to be there.

It sounds like another plugin or possibly even your theme somehow introduced a conflict with s2Member that is preventing WordPress from processing the s2Member shortcode(s). If you recently installed or updated any plugins, I'd start with trying to disable those. If that doesn't work, I'd try switching your theme to one of the default WordPress themes (e.g., TwentyFifteen).

See also: [Testing in a Clean Installation](https://github.com/websharks/s2member-kb/issues/81)

## Another reason this can occur...

Did you receive a notice in your Dashboard about there being an update available for s2Member? If you complete an update of the s2Member Framework, and then somehow miss the second notice that pops up after this, which explains that s2Member Pro needs to be updated also; you will end up with an outdated copy of s2Member Pro.

So what's happening is that you have a newer version of the Framework, with an outdated version of the Pro add-on. The Pro add-on is designed NOT to load unless both versions match up. Until you complete the second portion of the update, all pro functionality (e.g., pro shortcodes) will be unavailable.

**Solution:** update your copy of the s2Member Pro add-on.
