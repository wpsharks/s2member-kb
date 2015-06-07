---
title: How can I show the End-of-Term (EOT) date in the Signup Confirmation Email?
categories: questions
tags: mu-plugins-hacks, email-config, eot-time, 
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/219
toc-enable: off
---

There are many special Replacement Codes that can be used in the Signup Confirmation Email template (see **WordPress Dashboard → s2Member → PayPal Options → Signup Confirmation Email (Pro Form)**), however there is no Replacement Code for the EOT Date. The reason for this is that only some types of memberships will have an EOT Date set immediately (Fixed-Term Subscriptions), while other types will leave the EOT Date blank until the membership ends (Recurring Subscriptions). For more details please see [When is an EOT Time set for each user?](http://s2member.com/kb-article/when-is-an-eot-time-set-for-each-user/)

If you are using a Fixed-Term Subscription model on your site and you want to include the EOT Date inside the Signup Confirmation Email, you can use the following bit of PHP code to query the database and display the EOT Date in Signup Confirmation Email:

```php
<?php 
$user_id = c_ws_plugin__s2member_utils_users::get_user_id_with($paypal['subscr_id']);
$eot_time = get_user_option('s2member_auto_eot_time', $user_id);
echo date('F jS, Y, g:i a', $eot_time); // See: <http://php.net/manual/en/function.date.php
?>
```

You can paste this code directly into the Signup Confirmation Email Message template box, in place of where you want the EOT Date to appear. For date formatting options, please see the [PHP `date()` function reference](http://php.net/manual/en/function.date.php).
