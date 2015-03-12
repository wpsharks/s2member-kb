---
title: How can I hide specific fields on the [s2Member-Profile /] form?
categories: questions
tags: member-profile-modifications, mu-plugins-hacks
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/46
---

**Question:** How can I hide fields on the `[s2Member-Profile /]` form? For example, I don't want my users to be able to change their email address from this form; how would I hide the email field?

**Answer:** You can hide fields on the `[s2Member-Profile /]` form by adding a line to your theme's `functions.php` file, or to an [Must-Use Plugin](http://codex.wordpress.org/Must_Use_Plugins):

```php
add_filter('ws_plugin__s2member_during_profile_during_fields_display_email', '__return_false');
```

You can change `ws_plugin__s2member_during_profile_during_fields_display_email` to any of the following tags to hide the corresponding field. You can also hide multiple fields by repeating the `add_filter()` line, passing in the tag for each field you want to hide:

**Username:** `ws_plugin__s2member_during_profile_during_fields_display_username`
**Email:** `ws_plugin__s2member_during_profile_during_fields_display_email`
**First Name:** `ws_plugin__s2member_during_profile_during_fields_display_first_name`
**Last Name:** `ws_plugin__s2member_during_profile_during_fields_display_last_name`
**Display Name:** `ws_plugin__s2member_during_profile_during_fields_display_display_name`
**Custom Fields:** `ws_plugin__s2member_during_profile_during_fields_display_custom_fields`
**Password:** `ws_plugin__s2member_during_profile_during_fields_display_password`