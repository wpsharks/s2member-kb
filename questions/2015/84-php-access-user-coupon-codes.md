---
title: PHP to access user coupon codes?
categories: questions
tags: pro-coupon-codes, mu-plugins-hacks
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/84
---

> I don't see in the documentation what the option name is to `get_user_option()` for the coupon code... Also, which is the most recently used code? Will it be $array[0] ? What about no coupon... Null?

## Example PHP Code to Demonstrate

```php
<?php
$user_id      = get_current_user_id();
$user_coupons = get_user_option('s2member_coupon_codes', $user_id);
// ↑ Coupons the customer has used to complete checkout.
// This is an array of unique coupon codes, in chronological order.
// If the customer has never used a coupon code, this will be an empty array, or `FALSE`.

if(is_array($user_coupons) && !empty($user_coupons))
{
	$oldest_coupon_code = $user_coupons[0];
	$newest_coupon_code = $user_coupons[count($user_coupons) - 1];
}
```