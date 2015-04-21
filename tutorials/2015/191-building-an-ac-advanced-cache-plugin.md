---
title: PayPal Error: DPRP is disabled for this vendor?
categories: questions
tags: error-messages,troubleshooting,paypal
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/191
toc-enable: false
---

This Pro-Form error can occur whenever you attempt to charge a customer on a recurring basis, or when you attempt to offer an initial/trial period before collecting a fee. In either of these cases, a "Subscription" is used in the underlying PayPal API call. A "Subscription"-based term will always require access to PayPal's [Recurring Billing](http://www.s2member.com/paypal-pro-recurring-payments-faqs) service (aka: DPRP).

**Solution:** Add PayPal's [Recurring Billing](http://www.s2member.com/paypal-pro-recurring-payments-faqs) service to your account.

---

## Additional Details (Recurring Billing)

If you plan to use any of the "Subscription" options in the s2Member Pro-Form Generator for PayPal Pro, you will also need [Recurring Billing](http://www.s2member.com/paypal-pro-recurring-payments-faqs) enabled for your PayPal Pro account.

PayPal's Recurring Billing service for Pro accounts is required for all types of "Subscriptions", whether you intend for them to be recurring or not. However, it is not required for "Buy Now" functionality.

The drop-down menus in s2Member Pro-Form Generators have been marked "Subscription" and "Buy Now" to help you make this distinction. See: **Dashboard → s2Member → PayPal Pro-Forms**.

From that section, you can see which options will require the use of PayPal's [Recurring Billing](http://www.s2member.com/paypal-pro-recurring-payments-faqs) service. PayPal will charge you a small monthly fee for their Recurring Billing service; which is an add-on for PayPal Pro accounts.

![](https://www.filepicker.io/api/file/tLcjEKIjTkCj2hGNYByZ#.png){.fancy-image .aligncenter}
