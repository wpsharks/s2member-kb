---
title: How can I set Per-Level Unique IP Access Restrictions?
categories: questions
tags: restriction-options
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/225
toc-enable: off
---

The s2Member Unique IP Access Restrictions (**WordPress Dashboard → s2Member → Restriction Options → Unique IP Access Restrictions**) apply to all s2Member Levels, however if you need to fine-tune these settings to apply different rules for different levels, you can use an [MU-Plugin](http://codex.wordpress.org/Must_Use_Plugins) with some PHP code to achieve this.

The code in the following examples should go into the following file (if this file and directory do not exist, please create them): `wp-content/mu-plugins/s2-ip-restrictions.php`

## Disable Unique IP Access Restrictions on a Per-Level Basis

To disable Unique IP Access Restrictions for a specific Level of user (Level 4 Users in the below example), use the following code:

```php
<?php
add_filter('ws_plugin__s2member_disable_specific_ip_restriction', '__s2_disable_certain_ip_restrictions', 10, 2);

function __s2_disable_certain_ip_restrictions ($bool, $vars) { 
    if(username_exists($vars['restriction'])) { 
        $user = new WP_User($vars['restriction']); 

        if($user->has_cap('access_s2member_level4')) 
            $bool = true; 
    }
    return $bool;
}
```
In this example, these custom settings will only apply to Level 4 users. All other users will have whatever Unique IP Access restrictions are configured in **Dashboard → s2Member → Restriction Options → Unique IP Access Restrictions**.

## Set Per-Level Maximum Allowed IPs

To set a custom Maximum Allowed Unique IP Addresses for a specific Level of users (in the exmple below, we set Level 8 users to have a maximum of 50 Unique IP addresses), use the following code:

```php
<?php
add_action('ws_plugin__s2member_before_ip_restrictions_ok', function(array $vars) {
    $username  = $vars['restriction'];
    $user              = $username ? get_user_by('login', $username) : null;
    $role               = $user ? c_ws_plugin__s2member_user_access::user_access_role($user) : '';

    if($role === 's2member_level8')
        $GLOBALS["WS_PLUGIN__"]["s2member"]["o"]["max_ip_restriction"] = '50';
});
```

In this example, these custom settings will only apply to Level 8 users. All other users will have whatever Unique IP Access restrictions are configured in **Dashboard → s2Member → Restriction Options → Unique IP Access Restrictions**.
