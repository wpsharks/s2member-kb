---
title: How do I control access to an entire category of content?
categories: questions
tags: restriction-options, category-access-restrictions
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/67
---

To restrict all content in a specific category, you can use the s2Member Category Access Restrictions (see **Dashboard ⥱ s2Member (Pro) ⥱ Restriction Options ⥱ Category Restriction Options**). Simply enter the Category ID (the [WP Show IDs](http://wordpress.org/extend/plugins/wp-show-ids/) plugin is helpful for finding the Category ID) into the appropriate Level field and press "Save All Changes" at the bottom.

When a Category ID is placed inside one of the Level fields in Category Access Restrictions, that Level of access will be required to access any content inside that category. If the user does not have the required access, they will be redirected to your Membership Options Page.

_Note that s2Member Level access is cumulative, meaning that Level 2 users have access to everything offered to Level 1. If you restrict access to a specific category to Level 1, that means Level 1 and any higher levels (Level 2-4) will also have access._

If you want to allow access to a category _without_ logging in (i.e., anyone visiting your site, even if they don't have an account, can view the content), then simply don't restrict that category at all. Any content not restricted by s2Member will remain freely accessible to anyone visiting your site. 

If you want to require a free account to view a category of content (e.g., if you offer a free signup at Level 0 in addition to paid access at higher levels), then you can restrict that category to Level 0 and only users who are logged in will have access to that content.