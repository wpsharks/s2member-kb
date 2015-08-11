---
title: Why are users seeing a "link expired" error?
categories: questions
tags: paypal, troubleshooting
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/252
---

This error can occur with PayPal Buttons. However, it only happens when a customer takes longer than 2 days to respond to the email they receive after completing checkout. As you can imagine, that's a rare occurrence. Most customers follow up right away in order to gain access to what they've bought.

To clarify. The Registration Access Link in the s2Member Signup Confirmation Email is good for 2 days. If you click that link after 2 days, you will get a "link expired" error--this is a security precaution.

If you want to modify this, you can add a filter.

Create this directory and file:
`/wp-content/mu-plugins/s2-hacks.php`

```php
<?php
add_filter('ws_plugin__s2member_register_link_exp_time', function(){
  return '10 days';
});
```