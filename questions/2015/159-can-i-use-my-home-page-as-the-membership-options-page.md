---
title: Can I use my Home Page as the Membership Options Page?
categories: questions
tags: membership-options-page
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/159
---

No. Doing so causes hiccups for several [Conditional Tags](http://codex.wordpress.org/Conditional_Tags) that s2Member analyzes which can lead to unanticipated problems. When a "Post" (i.e., a Page) is reclassified as the Home Page in "the WordPress way", this changes some of the WordPress Conditional Tags when analyzing that content, which s2Member depends on in several places.

While it is a limitation so-to-speak, there's really very little reason to use your Home Page as the Membership Options Page. The Membership Options Page is there mostly to serve as a redirect for unprivileged users. You can put your Payment Buttons, Pricing Options, Pro-Forms, etc. anywhere you like. If you want them on the Home Page that's perfectly understandable and OK. However, you still need to configure a Membership Options Page for s2Member that is dedicated to that purpose; i.e., there needs to be a Page in WordPress that is specifically designated as the Membership Options Page—one which is not designated as something else, like your Home Page.