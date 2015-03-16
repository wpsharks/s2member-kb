---
title: Locking s2Member Roles/Capabilities
categories: tutorials
tags: roles-capabilities,api-scripting,mu-plugins-hacks
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/149
---

## Why Lock Roles/Capabilities?

If you've customized your WordPress Roles/Capabilities in more advanced ways, and you'd like to make sure s2Member does _not_ reset it's default set of Roles/Capabilities when you upgrade in the future, this trick is for you.

## Instructions; How to Lock Roles/Capabilities

Create this directory and file:
`/wp-content/mu-plugins/s2-lock-roles-caps.php`

```php
<?php
add_filter('ws_plugin__s2member_lock_roles_caps', '__return_true');
```

This will prevent future upgrades from resetting and/or re-configuring your Roles/Caps. In addition, this will disable the Reset Roles/Capabilities button in the Dashboard, under: **s2Member → General Options → Membership Levels/Labels**. Actually, the Reset Roles/Capabilities button is not disabled completely, but clicking the button does no good, because s2Member will simply return a message indicating that Roles/Capabilities have been locked by this Filter.