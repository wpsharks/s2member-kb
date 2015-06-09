---
title: How do you create a subscription that ends on a fixed date? i.e., same day for everyone.
categories: questions
tags: eot-time, mu-plugins-hacks, tricks, paypal, pro-forms
author: patdumond
github-issue: https://github.com/websharks/s2member-kb/issues/218
---

> How do you create a subscription that ends on a fixed date? i.e., always on an exact date in the future, no matter when the customer actually registers and completes checkout.

This requires a bit of PHP logic that works together with a Pro-Form shortcode supplied by s2Member. In this article I will demonstrate how this can be accomplished, so that you may adapt the technique shown below to match your own requirements.

## Forcing an EOT to occur *31 October 2025*

_**Note:** You will need [ezPHP](https://s2member.com/kb-article/ezphp-for-wordpress/) (provided by s2Member)._

Use this PHP code on your page to assign the EOT date (it must be placed before the Pro-Form shortcode), and you will need to enter this in the Text tab of the WordPress editor. If you use the Visual tab it may corrupt the raw PHP code, so don't do that.

```php
[php]
    $now = strtotime('now'); // The time now (in seconds).
    $fixed_eot_time = strtotime('31 October 2025'); // Future time (in seconds).
    $days_until_fixed_eot_time = round(($fixed_eot_time - $now) / DAY_IN_SECONDS);
    // ↑ This is where we calculate the number of days until an EOT should occur.
[/php]
```

### Create a Pro-Form Shortcode Using the s2Member Control Panel

![2015-06-03_09-06-30](https://cloud.githubusercontent.com/assets/1563559/7966336/de9e79c6-09cf-11e5-8b7b-ee8e4274f627.png)

_**Note:** If you didn't integrate with PayPal Pro; i.e., you integrated with Authorize.Net or Stripe Pro-Forms, that's fine. Just use the Pro-Form generator that is specifically for the payment gateway that you've selected. As long as you are using s2Member Pro-Forms, these instructions will apply the same way._

### Change the Following Attributes in Your Shortcode

- `rr="BN"` _(non-recurring Buy Now access)_
- `rt="D"` _(forces the EOT calculation to be based on days)_
- `rp="[php]echo esc_attr($days_until_fixed_eot_time);[/php]"` _(number of days until the EOT should occur)_

## Full Example (Based on Instructions Above)

```php
[php]
    $now = strtotime('now'); // The time now (in seconds).
    $fixed_eot_time = strtotime('31 October 2025'); // Future time (in seconds).
    $days_until_fixed_eot_time = round(($fixed_eot_time - $now) / DAY_IN_SECONDS);
    // ↑ This is where we calculate the number of days until an EOT should occur.
[/php]

[s2Member-Pro-PayPal-Form level="1" desc="$0.01 USD / Access Until October 31st, 2025" ra="0.01" rr="BN" rt="D" rp="[php]echo $days_until_fixed_eot_time;[/php]" /]
```
_**Note:** The above `[s2Member-Pro-PayPal-Form /]` shortcode has been abbreviated for clarity, yours will be longer and contain more attributes—that's fine. Also, these same instructions work for Authorize.Net and/or Stripe Pro-Forms too. Just change the name of the shortcode._

---

- See also: **Dashboard → s2Member → PayPal Pro-Forms → Shortcode Attributes (Explained)**
- See also: **Dashboard → s2Member → PayPal Options → Automatic EOT Behavior → Grace Period**
- See also: [Specifying a future start date for a recurring subscription (aka Custom EOT)](http://s2member.com/kb-article/specifying-a-future-start-date-for-a-recurring-subscription-aka-custom-eot/)
- See also: [How can I offer a fixed-term Free Registration?](http://s2member.com/kb-article/how-can-i-offer-a-fixed-term-free-registration/)
