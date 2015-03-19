---
title: Performance Tuning EOT/ARB/IPN Status Checks
categories: tutorials
tags: troubleshooting,mu-plugins-hacks
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/8
toc-enable: false
---

If you have LOTS of paying customers. Good for you! With so many paying customers for s2Member to keep tabs on through it's EOT system and polling routines, you might want to increase the maximum number of EOTs per process, and ARB/IPN status checks per process, to a higher number.

The current default value is to check up to `6` member subscriptions every 10 minutes. However, there are some internal performance tuning filters for very large sites. I will offer the following suggested tweaks to help prevent issues when there are lots of paying customers.

Please create this directory and file:
`/wp-content/mu-plugins/s2-eots-per-process.php`

```php
<?php
// Up to `10` EOTs every 10 minutes.
add_filter('ws_plugin__s2member_auto_eot_system_per_process', function(){ return 10; });

// Up to `20` status checks every 10 minutes. This is for Authorize.Net.
add_filter('ws_plugin__s2member_pro_arb_service_ipns_per_process', function(){ return 20; });

// Up to `20` status checks every 10 minutes. This is for PayPal Pro.
add_filter('ws_plugin__s2member_pro_payflow_ipns_per_process', function(){ return 20; });
```

## Some Subscriptions are Not Getting Demoted Automatically?

Note that `ws_plugin__s2member_pro_arb_service_ipns_per_process` and  `ws_plugin__s2member_pro_payflow_ipns_per_process` have a default maximum of `6` every 10 minutes. So with that in mind, it is possible that you have so many active paying subscribers that s2Member is simply not getting around to the ones which are non-`ACTIVE` each day. 

You want to set these values to something that will allow s2Member to check every single subscriber that you have on a daily basis, where the check runs once every 10 minutes. Thus, if you have it set to `20` (as seen in the example above) every 10 minutes throughout a single day, you can check up to 2880 subscription profiles for a possible non-`ACTIVE` status each day.

You can increase from there, but don't go too far with it, because normally a hosting provider will limit the time each script can run to approx. 30 seconds. If you start seeing "script timeout" errors in your PHP error log after increasing the value too much, back it down until those go away.