---
title: Automatic EOT System option goes blank, why?
categories: questions
tags: eot-time, troubleshooting
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/189
toc-enable: false
---

> s2Member's automatic EOT system usually works flawlessly, however over the past couple of months I've noticed an issue wherein the option to "Enable s2Member's Auto-EOT system" periodically goes blank.

This can happen when/if you have plugins running in WordPress that periodically erase and/or corrupt scheduled tasks that interface with the [WP Cron API](https://codex.wordpress.org/Category:WP-Cron_Functions). In other words, when you see that field go blank, it's because the WP Cron task that s2Member created no longer exists. Or, because the WP Cron functionality was disabled in some way by another plugin, by your hosting company, or in some other way. 

Enabling it again and saving your s2Member options recreates the WP Cron task automaticaly. However, that's only a short-term solution. This is not a bug in s2Member, but with rogue plugins installed alongside s2Member—it can happen! It may continue to happen until you find the conflicting theme or plugin that is causing a corruption of the WP Cron task.

### Suggested next step: [Testing in a Clean Installation](http://s2member.com/kb-article/testing-in-a-clean-wordpress-installation/)

---

![](https://www.filepicker.io/api/file/UtzrElGsRySqcWMBdUsJ#.png){.aligncenter}
