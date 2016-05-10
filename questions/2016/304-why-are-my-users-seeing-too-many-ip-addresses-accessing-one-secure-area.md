---
title: Why are my users seeing "Too many IP addresses accessing one secure area"?
categories: questions
tags: ip-access-restrictions
author: raamdev
github-issue:
github-issue: https://github.com/websharks/s2member-kb/issues/304
---

This is caused by Unique IP Access Restrictions.

See: **Dashboard → s2Member → Restriction Options → Unique IP Access Restrictions**

If you're running the pro version you can avoid this altogether by using Simultaneous Login Monitoring instead of Unique IP Restrictions. See: **Dashboard → s2Member → Restriction Options → Simultaneous Login Restrictions** for details.

However, it's still good to keep Unique IP Restrictions enabled to some degree if you're using Specific Post/Page Access, as that helps to protect that form of access also. So for instance, if I were running the pro version of s2Member I might set Unique IP Restrictions to around `50` (so it's on), but only for really abusive behavior, and then use SLM (Simultaneous Login Monitoring) to be more strict about how many people can access a single account at the same time.

See: **Dashboard → s2Member → Restriction Options → Simultaneous Login Restrictions**

_Simultaneous Login Restrictions requires s2Member Pro._