---
title: How can I reset the user login count when a user is upgraded?
categories: questions
tags: mu-plugins-hacks
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/196
---

If you're using One-Time Offers (**WordPress Dashboard → s2Member → General Options → One-Time-Offers (Upon Login)**) to show members a special page upon their first login, you may want to reset the login counter if you plan to show those One-Time Offers to members after they upgrade their membership.

The number of logins is not reset when they upgrade, so someone upgrading from one level to another would not see a one-time login offer that is configured to be shown on the first login. 

However, you could reset the login counter to `0` whenever a user is upgraded from one level to another. To do this, create an [MU-Plugin](http://codex.wordpress.org/Must_Use_Plugins) with the following code, which will trigger whenever a user's role is changed (e.g., when they are upgraded from one Level to another). 

Create the following directory and file: `wp-content/mu-plugins/s2-reset-login-counter.php`

```php
<?php
add_action('set_user_role', function($user_id, $new_role, $old_role)
{
    if(strpos($new_role, 's2member_') === 0)
        update_user_option($user_id, 's2member_login_counter', 0);
}, 10, 3);
```