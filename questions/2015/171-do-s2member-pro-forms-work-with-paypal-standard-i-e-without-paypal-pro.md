---
title: Do s2Member Pro-Forms work with PayPal Standard; i.e., without PayPal Pro?
categories: questions
tags: paypal,pro-forms
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/171
toc-enable: false
---

Using s2Member Pro does _not_ mean that you must use PayPal Pro integration. Just don't generate any PayPal Pro-Form Shortcodes. Instead, you could use Standard PayPal Buttons, Stripe, ClickBank, or Authorize.Net if you prefer (you could even use them all together at the same time).

If you want to process credit cards on-site though, you _must_ have a PayPal Pro account, a Stripe account, or an Authorize.Net account (i.e., s2Member Pro-Forms also integrate with Stripe and Authorize.Net for on-site credit card processing).

## Pro-Forms w/ PayPal Standard (i.e., w/o PayPal Pro)

Although not ideal, it's also possible to integrate s2Member Pro-Forms with only PayPal Express Checkout (**no PayPal Pro account required**). If you are unable to obtain a PayPal Pro, Stripe, or Authorize.Net account, you can still use s2Member Pro-Forms with the free version of PayPal by following these instructions:

### In your s2Member Pro-Form Shortcode change these shortcode attributes:

```text
accept="paypal,visa,mastercard,amex,discover,maestro,solo"
accept_via_paypal="paypal"
```

### Change them to:

```text
accept="paypal" accept_via_paypal="paypal"
```

This way all customers are ultimately passed over to PayPal Express Checkout to complete their purchase. You won't have the ability to process on-site credit cards if you only have PayPal Express Checkout, but for some site owners that's not an issue.

_**Remember:** If you want to process credit cards on-site, you must have a PayPal Pro account, a Stripe account, or an Authorize.Net account (i.e., s2Member Pro-Forms also integrate with Stripe and Authorize.Net for on-site credit card processing)._
