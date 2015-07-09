---
title: How can I let a customer set the amount they will pay?
categories: questions
tags: mu-plugins-hacks, tricks, pro-forms
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/233
---

If you accept donations, or if you would like the customer to be able to choose an arbitrary amount that they will pay you for access, we suggest the use of an s2Member Pro-Form (available in s2Member Pro).

---

## Step 1. ezPHP For WordPress

Install the [ezPHP plugin provided by s2Member](http://s2member.com/kb-article/ezphp-for-wordpress/). This is required if you intend to use PHP tags in a Post/Page (or together with a shortcode). This plugin is what makes arbitrary amounts possible.

---

## Step 2. Generate an s2Member Pro-Form Shortcode

See: **Dashboard → s2Member → Stripe Pro-Forms**

_Note: this example uses Stripe, but the same technique works with other payment gateways also._

Generate an s2Member Pro-Form shortcode as you normally would. Set the amounts to anything you like, we will alter them later with the ezPHP plugin. For now, the most important thing is just to _have_ an s2Member Pro-Form shortcode prepared. One that provides access to the Membership Level and CCAPs that you want to offer.

```wpsc
[s2Member-Pro-Stripe-Form level="1" ccaps="" desc="$0.50 USD / One Time (for lifetime access, non-recurring, no trial)" cc="USD" ta="0" tp="0" tt="D" ra="0.50" rp="1" rt="L" rr="BN" coupon="" accept_coupons="0" default_country_code="US" captcha="0" /]
```

---

## Step 3. Insert the s2Member Pro-Form Shortcode Into a Post/Page

The URL to this page might be something like:
`http://example.com/checkout/`

![2015-07-09_11-10-46](https://cloud.githubusercontent.com/assets/1563559/8604468/2fe7089e-262b-11e5-8685-ad46abc0d94b.png)

---

## Step 4. Make the Amount Dynamic; Based On An Input Variable

Working with: `http://example.com/checkout/`

This is where the magic happens. Using the ezPHP plugin, we set the `$amount` variable to the value of `$_GET['amount']`. The superglobal variable `$_GET['amount']` comes from the query string; e.g., `http://example.com/checkout/?amount=5.00`. Thus, the amount that a customer is charged is defined by the query string variable: `?amount=[amount]`.

```php
<?php
$amount = (float)@$_GET['amount'];
if($amount <= 0) $amount = '0.50'; // Default amount.
$amount = number_format($amount, 2, '.', ''); // Format the amount with two decimal points.
?>

[s2Member-Pro-Stripe-Form level="1" ccaps="" desc="$<?php echo esc_attr($amount); ?> USD / One Time (for lifetime access, non-recurring, no trial)" cc="USD" ta="0" tp="0" tt="D" ra="<?php echo esc_attr($amount); ?>" rp="1" rt="L" rr="BN" coupon="" accept_coupons="0" default_country_code="US" captcha="0" /]
```

_Notice that we changed the hard-coded amounts in the shortcode to `<?php echo esc_attr($amount); ?>` instead. This way the Pro-Form shortcode is configured with the correct/dynamic amount._

![2015-07-09_11-13-11](https://cloud.githubusercontent.com/assets/1563559/8604513/86418c96-262b-11e5-9eef-96c61ff7f3fa.png)

---

## Step 5. Build An Amount Entry Form

The URL to this page might be something like:
`http://example.com/donate/`

```html
<form method="get" action="/checkout/">
    <label>Amount:</label>
    <input type="number" name="amount" />
    <button type="submit">Proceed to Checkout</button>
</form>
```

![2015-07-09_11-16-26](https://cloud.githubusercontent.com/assets/1563559/8604569/fb015412-262b-11e5-83a4-588246f057ad.png)

![2015-07-09_11-17-29](https://cloud.githubusercontent.com/assets/1563559/8604597/1fe33eb2-262c-11e5-97fe-d65f3b44f6b5.png)

---

## Step 6. Accept Donations!

Direct those who will donate to: `http://example.com/donate/` where they will enter the amount they want to donate and submit the amount entry form. This will move them over to: `http://example.com/checkout/?amount=[amount they entered]` where your ezPHP + s2Member implementation picks up the amount and presents an s2Member Pro-Form preconfigured with the amount they want to pay you.