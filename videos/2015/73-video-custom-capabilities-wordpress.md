---
title: Video: Custom Capabilities for WordPress
categories: videos
tags: custom-capabilities,membership-levels
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/73
---

Using one of s2Member's Payment Button and/or Pro Form Generators, you can add Custom Capabilities in comma-delimited format. These are great way to extend s2Member to cover all sorts of business models that Membership Levels alone cannot.

https://www.youtube.com/watch?v=_F91xzrmq-Q&feature=youtu.be

### Understanding Roles & Capabilities

See: http://codex.wordpress.org/Roles_and_Capabilities

s2Member builds upon existing functionality offered by WordPress Roles/Capabilities. s2Member supports Free Subscribers (at Level #0), and several Primary Roles created by the s2Member plugin (i.e. s2Member Levels 1-4, or up to the number of configured Levels).

Each s2Member Level (aka: s2Member Role) provides the Capability `current_user_can('access_s2member_level0')`, `1`, `2`, `3`, `4`, where `access_s2member_level[0-4]` is the Capability associated with each Role.

### Membership Levels Provide Incremental Access

Membership Levels provide incremental access (i.e. Level #4 Members can also access content at Levels 0, 1, 2, and 3 beneath them). In short, these Level-based permissions are the default Capabilities that come with each Membership Level being sold on your site.

### Combining Membership Levels w/ Custom Capabilities

Now, if you'd like to package together some variations of each Membership Level that you're selling, you can! All you do is add Custom Capabilities whenever you create your Payment Button and/or Pro Form Shortcode. There is a field in the Button & Form Generators where you can enter Custom Capabilities. You can sell Membership Packages that come with Custom Capabilities, and even with custom prices.

Custom Capabilities are an extension to a feature that already exists in WordPress core. The `current_user_can()` function can be used to test for these additional Capabilities that you allow. Whenever a Member completes the checkout process, after having purchased a Membership from you (one that included Custom Capabilities), s2Member will add those Custom Capabilities to the account for that specific Member automatically.

Custom Capabilities are always prepended with `access_s2member_ccap_`. You fill in the last part, with lowercase alphanumerics and/or underscores. For example, let's say you want to sell Membership Level #1 as-is; but, you also want to sell a slight variation of Membership Level #1. One that includes the ability to access the Music & Video sections of your site.

Instead of selling this additional access under a whole new Membership Level, you could just sell a modified version of Membership Level #1. Add the the Custom Capabilities: `music,videos`. Once a Member has these Capabilities, you can test for these Capabilities using `current_user_can('access_s2member_ccap_music'')` and `current_user_can('access_s2member_ccap_videos')`.