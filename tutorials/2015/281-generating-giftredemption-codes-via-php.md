---
title: Generating Gift/Redemption Codes via PHP
categories: tutorials
tags: tricks, mu-plugins-hacks, giftredemption-codes
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/281
---

s2Member provides an easy-to-use shortcode called [`[s2Member-Gift-Codes /]`](http://s2member.com/kb-article/can-i-sell-gift-certificates/). The shortcode makes it easy to create and sell Gift Codes (aka: Redemption Codes) to new and/or existing customers in a variety of ways. **However**, a developer might like to generate these codes on their own, in response to specific events that occur. This can be done using PHP tags in s2Member Pro.

## PHP Code Samples

_**Note:** These samples require PHP 5.4+._

### Generate one new gift/redemption code (100% off discount).

```php
<?php
echo s2member_pro_redemption_code_generate()['code'];
    // Output: GC00K1BUA2NZ5CTRCL5M31
```

### Generate one new gift/redemption code that provides 50% off.

```php
<?php
$args = ['discount' => '50%'];
echo s2member_pro_redemption_code_generate($args)['code'];
    // Output: GC00K1BUA74Z5CTRCL5M31
```

### Generate one new gift/redemption code that provides 50% off, and it will only apply the discount to an initial/trial period.

```php
<?php
$args = ['discount' => '50%', 'directive' => 'ta-only'];
echo s2member_pro_redemption_code_generate($args)['code'];
    // Output: GC87K1BUA2NZ5CTRCL5M31
```

### Generate one new gift/redemption code that provides 50% off, and it will only apply the discount to the regular/recurring rate; not to any initial/trial period.

```php
<?php
$args = ['discount' => '50%', 'directive' => 'ra-only'];
echo s2member_pro_redemption_code_generate($args)['code'];
    // Output: GC55K1BUA2NZ5CTRCL5M31
```

### Generate one new gift/redemption code that only works in a Pro-Form that lives in Post ID 123 or Post ID 456.

```php
<?php
$args = ['discount' => '50%', 'singulars' => '123,456'];
echo s2member_pro_redemption_code_generate($args)['code'];
    // Output: GC99K1BUA2NZ5CTRCL5M31
```
