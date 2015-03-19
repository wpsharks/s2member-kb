---
title: How do I display multiple checkout options?
categories: questions
tags: pro-forms, checkout-options
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/39
toc-enable: false
---

> How do I display multiple checkout options on a single checkout page?

## Using Pro-Form Checkout Options

If you would like to offer a single Pro-Form with multiple "Checkout Options", it's quite easy. See: **Dashboard → s2Member (Pro) → PayPal Pro-Forms → Wrapping Multiple Shortcodes as "Checkout Options"**

First, generate each of your Pro-Form shortcodes the same as you normally would (using some of the Pro-Form generators). Then, you can simply wrap them all inside another Pro-Form shortcode (as seen below). 

For instance, if you generate two Pro-Form shortcodes (or you have multiple Pro-Form shortcodes on-site already); you can simply take those and wrap them inside another Pro-Form shortcode; this consolidates all the Pro-Form shortcodes into a single Pro-Form with multiple "Checkout Options" (i.e., it creates a drop-down menu for your customers to choose from). 

```wpsc
[s2Member-Pro-PayPal-Form rp="1" rt="Y" rr="1" accept_coupons="1"]
	[s2Member-Pro-PayPal-Form level="1" desc="$39 USD / Product 1" ra="39.00" /]
	[s2Member-Pro-PayPal-Form level="2" desc="$79 USD / Product 2" ra="79.00" /]
	[s2Member-Pro-PayPal-Form level="3" desc="$117 USD / Product 3" ra="117.00" /]
[/s2Member-Pro-PayPal-Form]
```

---

This will generate a dropdown box like the following:

![](https://cloud.githubusercontent.com/assets/53005/5784416/ec810556-9d99-11e4-8f15-bc339519a0b8.png)

---

![](https://cloud.githubusercontent.com/assets/53005/5784417/ed01272c-9d99-11e4-8d78-30d826f675d5.png)

---

## Using Top-Level Parent Shortcode Attributes

Given the example (as seen above); s2Member will first take the primary default shortcode attributes (from the top-level parent shortcode); and then merge those together with shortcode attributes from a particular Checkout Option (i.e., a child). The one s2Member merges with is based on the currently selected Checkout Option (i.e., the Checkout Option selected by your customer).

In other words, the shortcode attributes in the top-level parent shortcode (`rp="1" rt="Y" rr="1" accept_coupons="1"`) will apply to _all_ of the child shortcodes. You don't need to give the top-level parent shortcode any attributes--this is simply a way to avoid repeating yourself.

Here's another way of writing the exact same example shown above:

```wpsc
[s2Member-Pro-PayPal-Form]
	[s2Member-Pro-PayPal-Form rp="1" rt="Y" rr="1" accept_coupons="1" level="1" desc="$39 USD / Product 1" ra="39.00" /]
	[s2Member-Pro-PayPal-Form rp="1" rt="Y" rr="1" accept_coupons="1" level="2" desc="$79 USD / Product 2" ra="79.00" /]
	[s2Member-Pro-PayPal-Form rp="1" rt="Y" rr="1" accept_coupons="1" level="3" desc="$117 USD / Product 3" ra="117.00" /]
[/s2Member-Pro-PayPal-Form]
```

---

## Linking To A Pro-Form w/ Multiple "Checkout Options"

It is also possible to link to a Pro-Form and pre-select a specific Checkout Option that appears in the list. This is useful if you have a Features Table with buttons for each Checkout Option. You can link each button to the checkout page so that the corresponding Checkout Option is preselected automatically.

Starting from the first Checkout Option in the list (we call this Checkout Option 1) you can choose which Checkout Option number you want to have selected by default. This is accomplished by linking to any Post/Page on your site which contains a Pro-Form shortcode; and then adding the `?s2p-option=[number]` onto the end of that URL (as seen below).

This example would pre-select option 2.

```text
http://www.example.com/my-checkout-form/?s2p-option=2
```

_The absolute default Checkout Option is always the first one (Checkout Option 1)._

This would pre-select option 1 (but this is _not_ necessary, because it's the default already).

```text
http://www.example.com/my-checkout-form/?s2p-option=1
```
