---
title: Can a Free Subscriber register more than once?
categories: questions
tags: pro-forms, login-registration
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/87
---

WordPress does not allow multiple registrations with the same email address, so while someone could use a different email address to register a new account, an existing user will not be able to "re-register" for another free account using an email address that matches their existing account.

> how do I prevent people from creating multiple accounts with different email addresses?

One way would be to leave the default option here, where it requires that the end-user receive an email before they actually get their password. Of course, it's still possible to use `me+this@` or another real email address variation, but it's a deterrent at least. I think that's really all you can do.

![2015-02-05_12-34-42](https://cloud.githubusercontent.com/assets/1563559/6069753/7d359802-ad33-11e4-8258-a6acdb72b3ac.png)
