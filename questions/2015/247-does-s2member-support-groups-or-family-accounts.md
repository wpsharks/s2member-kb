---
title: Does s2Member support groups or family accounts?
categories: questions
tags: pre-sale-faqs, buddypress
author: raamdev
github-issue:
github-issue: https://github.com/websharks/s2member-kb/issues/247
---

There is no concept of 'groups' or 'family accounts' in WordPress or s2Member, however there is something that comes close called [Roles](https://codex.wordpress.org/Roles_and_Capabilities). The s2Member plugin is built upon the WordPress user system (i.e., all s2Member users are WordPress users) and makes heavy use of the built-in system of Roles and Capabilities provided by WordPress.

The WordPress concept of Roles, which are a collection of permissions (Capabilities) that allow a particular user to do certain things on your site, is used by s2Member to define membership levels. When you first install s2Member you'll see 4 additional Roles available for assigning to users: s2Member Level 1-4 (with s2Member Pro you can enable an unlimited number of Membership Levels).

![s2Member Roles](https://cloud.githubusercontent.com/assets/53005/9049138/edcd919e-3a0c-11e5-8ae1-3a1ffe4b0330.png)

Note that all s2Member Level roles are built upon the WordPress Subscriber role, which only has capabilities (permissions) to access to front-end content; s2Member is [not designed to control access to Dashboard features](http://s2member.com/kb-article/can-i-allow-users-to-access-the-dashboard-or-edit-postspages/).

## Can I use Roles to group users together?

While there is no concept of groups in WordPress or s2Member and the s2Member levels are commonly used to group together various types of customers (e.g., Bronze, Silver, Gold), you could choose to not use Levels to control access and instead use only Custom Capabilities, effectively turning each s2Member Level into nothing more than a grouping of users.

This technique is commonly used by site owners who wish to get around the cumulative nature of level access.

As s2Member is primarily a membership plugin, all s2Member Levels provide cumulative access (i.e., higher levels have access to everything granted to lower levels), however you can override this behavior by using [Custom Capabilities](http://s2member.com/kb-article/video-custom-capabilities-for-wordpress/) in conjunction with Levels to restrict content to only those users who have the necessary Custom Capability (see [this tutorial](http://s2member.com/kb-article/setting-up-two-membership-types-professional-student-with-two-sub-types-gold-bronze-and-a-3-day-free-trial/) for an example of how this would work). 

If you don't restrict anything to any particular Level and instead only use Custom Capabilities to restrict access, then it won't matter which Level a user belongs to, so long as they have the necessary Custom Capability. 

## Roles don't work for me; are there any other options?

If your business model absolutely requires the concept of groups, we recommend looking into [BuddyPress](http://buddypress.org), which s2Member integrates with (see [s2Member + BuddyPress](http://s2member.com/kb-article/s2member-buddypress/)). 

With BuddyPress, you can enable the User Groups component and then create BuddyPress Groups, which users can then be assigned to.

![2015-08-03_18-39-59](https://cloud.githubusercontent.com/assets/53005/9049404/a8c2af96-3a0f-11e5-8e62-2fc5c72f0bde.png)
![2015-08-03_18-41-22](https://cloud.githubusercontent.com/assets/53005/9049405/ab1e6668-3a0f-11e5-81c6-b28552bd7b29.png)

If you decide to use s2Member with BuddyPress, we highly recommend reviewing the [s2Member + BuddyPress](http://s2member.com/kb-article/s2member-buddypress/) article to learn more about how to integrate s2Member with BuddyPress.

We also recommend reviewing the following articles, which answer some frequently asked questions about using s2Member with BuddyPress:

- [Can I automatically add users to BuddyPress Groups whenever they complete registration/checkout?](http://s2member.com/kb-article/how-can-i-automatically-add-a-user-to-a-buddypress-group/)
- [How do I require a certain Level to access various parts of BuddyPress?](http://s2member.com/kb-article/how-do-i-require-a-certain-level-to-access-various-parts-of-buddypress/)
- See also: [All KB Articles Tagged BuddyPress](http://s2member.com/kb/kb-tag/buddypress/)

## What about hierarchical groups, for 'family accounts'?

There is no concept of hierarchical groups in WordPress, s2Member, or even BuddyPress. While it's not possible to have 'parent' accounts that can create or control access to 'child' accounts, you could use the s2Member Pro [Gift Certificates](http://s2member.com/kb-article/can-i-sell-gift-certificates/) feature to sell collections of gift certificates that then allow someone to sign up multiple times using the gift certificates (which could provide a discounted signup, including a 100% discount, i.e., free).