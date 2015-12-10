---
title: Generating Gift/Redemption Codes via PHP
categories: tutorials
tags: tricks, mu-plugins-hacks, giftredemption-codes
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/281
toc-enable: true
---

s2Member provides an easy-to-use shortcode called [`[s2Member-Gift-Codes /]`](http://s2member.com/kb-article/can-i-sell-gift-certificates/). The shortcode makes it easy to create and sell Gift Codes (aka: Redemption Codes) to new and/or existing customers in a variety of ways. **However**, a developer might like to generate these codes on their own, in response to specific events that occur.

This can be done using PHP tags in s2Member Pro.

## PHP Code Samples

_**Note:** These samples require PHP 5.4+._

### 100% Off

```php
<?php
echo s2member_pro_redemption_code_generate()['code'];
    // Output: GC00K1BUA2NZ5CTRCL5M31
```

### 50% Off (i.e., Passing Arguments)

```php
<?php
$args = ['discount' => '50%'];
echo s2member_pro_redemption_code_generate($args)['code'];
    // Output: GC00K1BUA74Z5CTRCL5M31
```

### $5.00 Off (i.e., Flat-Rate)

```php
<?php
$args = ['discount' => '5.00'];
echo s2member_pro_redemption_code_generate($args)['code'];
    // Output: GC00K1BUA74Z5CTRCL5M31
```

### 50% Off (Initial Amount Only)

```php
<?php
$args = ['discount' => '50%', 'directive' => 'ta-only'];
echo s2member_pro_redemption_code_generate($args)['code'];
    // Output: GC87K1BUA2NZ5CTRCL5M31
```

### 50% Off (Regular|Recurring Amount Only)

_i.e., does not discount any initial/trial period. Only impacts the regular Buy Now rate. Or, the regular recurring rate if you are selling a subscription plan._

```php
<?php
$args = ['discount' => '50%', 'directive' => 'ra-only'];
echo s2member_pro_redemption_code_generate($args)['code'];
    // Output: GC55K1BUA2NZ5CTRCL5M31
```

### Post ID #123 or Post ID #456 Only

_This prevents the code from being used anywhere other than these Post IDs._

```php
<?php
$args = ['discount' => '50%', 'singulars' => '123,456'];
echo s2member_pro_redemption_code_generate($args)['code'];
    // Output: GC99K1BUA2NZ5CTRCL5M31
```

---

## Frequently Asked Questions

### When I generate codes are they stored in my database?

Yes. Generating a Redemption Code triggers a database write, which stores a new row in your `wp_options` table. This row is used to identify the Redemption Code as being valid, and also to flag it as having been used once a customer redeems it.

### How can a customer use the Redemption Code(s) that I generate?

You will need to generate an s2Member Pro-Form and set `accept_coupons="1"` to enable a box that allows a customer to enter a Coupon Code (aka: Gift Code; aka: Redemption Code). See: **Dashboard → s2Member → Pro Coupon Codes** for further details.
