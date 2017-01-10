---
title: s2Member Roles/Capabilities
categories: tutorials
tags: roles-capabilities, mu-plugins-hacks
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/122
---

## What are Roles/Capabilities?

When you install s2Member it integrates seamlessly with an existing WordPress concept that facilitates varying degrees of permission across different portions of a site or service (including the back-end of WordPress itself). So Roles/Capabilities are not something new that s2Member introduces, it simply works with and customizes an existing WordPress community concept: [WordPress Roles/Capabilities](http://codex.wordpress.org/Roles_and_Capabilities)

For example, you probably already know that site owners are normally WordPress Administrators. A WordPress "Administrator" being your **Role** on the site. This Administrator Role grants you the ability to do certain things, because it includes many different **Capabilities** (e.g., `edit_posts`, `install_plugins`, etc). To learn more about Roles/Capabilities in WordPress, see [this article](http://codex.wordpress.org/Roles_and_Capabilities).

## s2Member Roles/Capabilities (Including bbPress Support)

When you install s2Member it adds some additional Roles and Capabilities to a default installation of WordPress. s2Member also makes extensive use of an existing Role in WordPress, the "Subscriber" Role. s2Member uses the Subscriber Role to classify Free Subscribers (i.e., people with an account, but they’ve not paid you anything yet). Or, maybe they _have_ paid you for something in the past, but they were since demoted back down to the Subscriber Role (so they no longer have Membership privileges, or Capabilities I should say).

### Membership Levels Provide Incremental Access

<div class="li-margins"></div>

- A Member with Level `4` access will also be able to access Levels `0`, `1`, `2` & `3`.
 - **WordPress Role:** `s2member_level4`
 - **WordPress Capabilities:** `read`, `level_0`, `access_s2member_level0`, `access_s2member_level1`, `access_s2member_level2`, `access_s2member_level3`, `access_s2member_level4`
 - **bbPress Capabilities:** `spectate`, `participate`, `read_private_forums`, `publish_topics`, `edit_topics`, `publish_replies`, `edit_replies`, `assign_topic_tags`
 
- A Member with Level `3` access will also be able to access Levels `0`, `1` & `2`.
 - **WordPress Role:** `s2member_level3`
 - **WordPress Capabilities:** `read`, `level_0`, `access_s2member_level0`, `access_s2member_level1`, `access_s2member_level2`, `access_s2member_level3`
 - **bbPress Capabilities:** `spectate`, `participate`, `read_private_forums`, `publish_topics`, `edit_topics`, `publish_replies`, `edit_replies`, `assign_topic_tags`

- A Member with Level `2` access will also be able to access Levels `0` & `1`.
 - **WordPress Role:** `s2member_level2`
 - **WordPress Capabilities:** `read`, `level_0`, `access_s2member_level0`, `access_s2member_level1`, `access_s2member_level2`
 - **bbPress Capabilities:** `spectate`, `participate`, `read_private_forums`, `publish_topics`, `edit_topics`, `publish_replies`, `edit_replies`, `assign_topic_tags`

- A Member with Level `1` access will also be able to access Level `0`.
 - **WordPress Role:** `s2member_level1`
 - **WordPress Capabilities:** `read`, `level_0`, `access_s2member_level0`, `access_s2member_level1`
 - **bbPress Capabilities:** `spectate`, `participate`, `read_private_forums`, `publish_topics`, `edit_topics`, `publish_replies`, `edit_replies`, `assign_topic_tags`

- A Subscriber with Level `0` access will _only_ be able to access Level `0`.
 - **WordPress Role:** `subscriber`
 - **WordPress Capabilities:** `read`, `level_0`, `access_s2member_level0`
 - **bbPress Capabilities:** `spectate`, `participate`, `read_private_forums`, `publish_topics`, `edit_topics`, `publish_replies`, `edit_replies`, `assign_topic_tags`

- A public Visitor will have _no_ access to protected content whatsoever (and no access to bbPress Forums).

_WordPress Subscribers are at Membership Level 0. If you’re allowing Open Registration, Subscribers will be at Level 0 (a Free Subscriber). WordPress Administrators, Editors, Authors, and Contributors have Level 4 access with respect to s2Member. All of their other Roles/Capabilities are left untouched. bbPress Keymasters/Moderators have Level 4 access with respect to s2Member. All of their other Roles/Capabilities are left untouched._

## Modifying s2Member Roles/Capabilities

If you would like to modify the default s2Member Roles/Capabilities, see: [Enhanced Capability Manager](http://wordpress.org/extend/plugins/capability-manager-enhanced/). 

**However (please note):** s2Member will _not_ offer help with a site that is running modified Roles/Capabilities. If you customize your installation you will be responsible for debugging anything that may not be working as expected.

If you _do_ modify your Roles/Capabilities, please be sure to install this MU plugin (see below) to prevent s2Member from resetting your customization in the future—should you attempt to update your copy of s2Member or s2Member Pro. This will lock-in your customizations; telling s2Member NOT to reset your Roles/Capabilities during future plugin updates.

Please create this directory and file:
`/wp-content/mu-plugins/s2-lock-roles-caps.php`

```php
<?php
add_filter('ws_plugin__s2member_lock_roles_caps', '__return_true');
```

## Other Related Articles (Suggested Reading)

- See: **Dashboard → s2Member → General Options → Membership Levels/Labels**
- See: **Dashboard → s2Member → API / Scripting → Advanced PHP Conditionals**
- See: **Dashboard → s2Member → API / Scripting → Advanced PHP Query Conditionals**
- See: **Dashboard → s2Member → API / Scripting → Custom Capabilities (Packages)**

- See: [Simple Shortcode Conditionals](https://github.com/websharks/s2member-kb/issues/119)
- See: [WordPress Conditional Tags](http://codex.wordpress.org/Conditional_Tags)
- See: [WordPress Roles/Capabilities](http://codex.wordpress.org/Roles_and_Capabilities)
- See: [bbPress Roles/Capabilities](http://codex.bbpress.org/bbpress-user-roles-and-capabilities/)
- See: [Extending s2Member w/ Custom Capabilities](https://www.youtube.com/watch?v=_F91xzrmq-Q)
