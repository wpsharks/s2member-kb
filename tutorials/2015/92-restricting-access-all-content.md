---
title: Restricting Access to All Content
categories: tutorials
tags: restriction-options
author: brucewsinc
github-issue: https://github.com/websharks/s2member-kb/issues/92
---

If you're looking for the ability to restrict all, or most of your content on your site to registered / paying Users, the usual methods for restriction probably won't seem useful to you. s2Member allows you to set up restrictions on a page-by-page basis, and that's typically all that's required in 95% of installations.

In installations where Users should only be able to access your entire site if they've registered and/or paid for access, **URI, Category, and Tag Restrictions are your friend**.

![screen shot 2015-02-06 at 2 54 28 pm](https://cloud.githubusercontent.com/assets/1568616/6086475/1546d8d6-ae10-11e4-8289-c3fd159b0cf6.png)

s2Member's Membership Options Page is **always** unrestricted, and even setting your entire site to be restricted won't change that. This is the Page that Users are sent to when they attempt to access restricted content. You can use that to your advantage.

For example, setting any field within **_Dashboard -> s2Member -> Restriction Options -> URI Restrictions_** field to `/` in your Dashboard will prevent any URL within WordPress on your site from being accessed without a User at least being registered and logged-in on your site.

![screen shot 2015-02-06 at 2 57 29 pm](https://cloud.githubusercontent.com/assets/1568616/6086515/823e2ac0-ae10-11e4-96f2-49b8136ca200.png)

Simiarly, you can use the keyword `all` within the Post and Page Restrictions section to block access to all Posts/Pages (with the Membership Options Page being an exception).

See: **_Dashboard -> s2Member -> Restriction Options -> Post Access Restrictions_**