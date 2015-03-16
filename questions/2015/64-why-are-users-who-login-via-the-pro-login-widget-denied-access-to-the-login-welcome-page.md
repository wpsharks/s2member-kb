---
title: Why are users who login via the Pro Login Widget denied access to the Login Welcome Page?
categories: questions
tags: troubleshooting, login-registration
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/64
toc-enable: false
---

> Why are users who login via the Pro Login Widget denied access to the Login Welcome Page? They are automatically redirected to the Membership Options Page after they login with s2Member MOP Vars like this: `?_s2member_vars=sys..level..0..page..`

That sounds like they are not actually getting logged-in. It could be the www vs. without issue, or an https vs. http issue. I'd ask them to verify cookies are being set as expected. Please see: [How to Avoid WordPress Member Login Issues](https://github.com/websharks/s2member-kb/issues/72) for further details on this topic.