---
title: %%full_coupon_code%% in Admin Notification Email?
categories: questions
tags: pro-forms,pro-coupon-codes,troubleshooting
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/31
toc-enable: false
---

> Question: I tried adding `%%full_coupon_code%%` to the Admin Email Notification email and it did not send the code used. Any idea how to get this to work?

All transaction-related email templates now support three additional Replacement Codes:

- `%%full_coupon_code%%`
- `%%coupon_code%%`
- `%%coupon_affiliate_id%%`

_These have been documented in your Dashboard in places where transaction-related email templates are configured._

Administrative notifications regarding a new user are not transaction-related. This notification is sent by WordPress and can be customized further when s2Member is installed; but unfortunately, this email is not sent within a context that would allow s2Member to fill it with a coupon code at this time.

The emails that support the coupon replacement codes are: Signup Confirmation Email, Modification Confirmation Email, Capability Confirmation Email, etc. All of these are displayed in areas such as: PayPal Pro Options, Stripe Options, and/or Authorize.Net Options. For example, see: **Dashboard → PayPal Options → Signup Confirmation Email**

---

## Possible Alternative Solution

s2Member _also_ supports event-driven notifications via email, and it's **much easier** to get information (such as the coupon code) from s2Member's API Notifications than it is to parse the content of a message sent to the customer, or a message sent to the admin regarding a new registration; i.e., the data in these notifications is structured so that it could even be parsed if you needed it to be.

For instance, please see: **Dashboard → s2Member → API / Notifications**

![](https://cloud.githubusercontent.com/assets/1563559/5745929/8adf2778-9bd8-11e4-85dd-3f1a0a960624.png)