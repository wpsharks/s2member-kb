---
title: How can I enable Pro-Forms in the Dashboard?
categories: questions
tags: pro-forms, troubleshooting
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/30
---

> I am slightly confused. I am considering using pro forms on my site, but I haven't seen the Pro-forms option since I upgraded to Pro. It is not under the s2member menu options in the sidebar. Why is this?

First, it would be a good idea to make sure that you actually _do_ have s2Member Pro installed and that the s2Member Framework is loading it up from the location where it expects to find it in WordPress.

Please go to: **Dashboard → Plugins** and find this note regarding s2Member Pro.

![](https://cloud.githubusercontent.com/assets/1563559/5745565/43535048-9bd6-11e4-85b9-a1580caa5c05.png)

If you don't see this, s2Member Pro is not actually loading up. In this case, it is a good idea to review the full installation instructions again and double-check that you were correct in each case. See: [s2Member Pro Installation Instructions](http://s2member.com/installation/)

---

If you have s2Member Pro enabled, then next you should make sure that _have_ enabled PayPal Pro-Forms, Stripe Pro-Forms, or Authorize.Net Pro-Forms. These represent the payment gateways that integrate with s2Member Pro-Forms. Thus, one of these must be enabled for you to take advantage of s2Member Pro-Forms.

![](https://cloud.githubusercontent.com/assets/1563559/5745531/fbea2952-9bd5-11e4-9af3-2d580e43b94c.png)

---

Finally, select the menu option which leads to the available Pro-Forms for the payment gateway that you have chosen to integrate with s2Member.

![](https://cloud.githubusercontent.com/assets/1563559/5745645/be5f41e8-9bd6-11e4-950c-1af75601aa73.png)