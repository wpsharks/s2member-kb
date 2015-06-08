---
title: Why are my registration links returning a 404 Error (when using BuddyPress)?
categories: questions
tags: error-messages, login-registration
author: raamdev
github-issue:
github-issue: https://github.com/websharks/s2member-kb/issues/222
---

If the Registration URL that appears inside a Signup Confirmation Email is returning a 404 Error and you're also running the [BuddyPress](http://buddypress.org) plugin, you may not have configured your BuddyPress Registration Pages.

You must configure the BuddyPress Registration pages by selecting the corresponding pages inside **WordPress Dashboard → Settings → BuddyPress → Pages**. Note that BuddyPress automatically generates the content for these pages, so you can just create a blank page called "Register" and another one called "Activate" and then select them inside the BuddyPress configuration.

![2015-06-08_15-00-04](https://cloud.githubusercontent.com/assets/53005/8042789/95784096-0def-11e5-84ed-0500b51d2564.png)