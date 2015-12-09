---
title: Why can't I use the same Trial Amount and Regular Amount with PayPal?
categories: questions
tags: paypal, pro-forms, error-messages
author: raamdev
toc-enable: off
github-issue: https://github.com/websharks/s2member-kb/issues/279
---

Due to PayPal-imposed limitations, it's not possible to set the Trial Amount (`ta=""`) and Regular / Recurring Amount (`ra=""`) to the same value. The most common use-case for this scenario is when you want to create a Pro Coupon Code that discounts only the initial trial amount, thereby discounting the first payment but then charging the regular recurring amount for every subsequent period.

Attempting to set the `ta=""`, `tp=""`, and `tt=""` Trial Period attributes to the exact same value as your `ra=""`, `rp=""`, and `rt=""` Regular / Recurring attributes will result in the following error:

![s2Member - Invalid Form Configuration screenshot](https://cloud.githubusercontent.com/assets/53005/11686262/5fbc4c38-9e4d-11e5-9145-fd184baf232c.png)

## How can I work around this PayPal limitation?

To work around this you can set one of the amounts to `.01` higher or lower, or change the billing cycle by one day, or something else. The attributes just need to be different (even if just slightly). That allows you to bypass this limitation with PayPal's API.

Or if you're open to switching payment gateways, you could switch to the [Stripe](https://stripe.com/) payment gateway, which allows you to have identical Trial and Regular/Recurring amounts.
