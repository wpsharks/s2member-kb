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