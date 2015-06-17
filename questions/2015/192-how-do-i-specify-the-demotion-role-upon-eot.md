---
title: How do I specify the Demotion Role upon EOT?
categories: questions
tags: eot-time, mu-plugins-hacks
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/192
toc-enable: off
---

When a user's account reaches End-of-Term (EOT) and your Membership EOT Behavior settings (see **WordPress Dashboard → s2Member → [Payment Gateway] Options → Automatic EOT Behavior → Membership EOT Behavior**) are set to Demote the user upon reaching EOT, the user will, by default, be demoted to **Level 0 / Subscriber**. However, it is possible to override this default behavior.

If your particular business rules require that users be demoted to a different level upon EOT, e.g., **Level 1** instead of **Level 0 / Subscriber**, you can create an [MU-Plugin](http://codex.wordpress.org/Must_Use_Plugins) with the following code to tell s2Member to demote to **Level 1**:

Create this file and directory: `wp-content/mu-plugins/s2-eot-role.php`:

```php
<?php
add_filter('ws_plugin__s2member_force_demotion_role', function(){ return 's2member_level1'; });
```

----

## Custom Demotion Role Based On Previous Role?

This requires a slightly different technique. Instead of forcing a specific demotion role for all demotions, we need to hook into s2Member and see what the Role was before a demotion occurred, and then alter this in custom ways. Here is a quick example.

_**Note:** This example does not depend on the one above that was mentioned previously; i.e., if you choose this route, use this route **only**. Do not attempt to mix both code samples together at the same time please._

Create this file and directory: `wp-content/mu-plugins/s2-custom-eot-roles.php`:

```php
<?php
add_action('ws_plugin__s2member_during_auto_eot_system_during_demote', 's2_custom_eot_demotion_role');
add_action('ws_plugin__s2member_during_paypal_notify_during_subscr_eot_demote', 's2_custom_eot_demotion_role');

function s2_custom_eot_demotion_role(array $vars) {
  $user                 = $vars['user']; // WP_User object instance.
  $role_before_demotion = $vars['existing_role']; // Role ID before demotion by s2Member.
  
  if($role_before_demotion === 's2member_level5') {
    $user->set_role('s2member_level3'); // If they were at level 5, force a custom demotion to level 3.
  } else if($role_before_demotion === 's2member_level4') {
    $user->set_role('s2member_level2'); // If they were at level 4, force a custom demotion to level 2.
  }
}
```
