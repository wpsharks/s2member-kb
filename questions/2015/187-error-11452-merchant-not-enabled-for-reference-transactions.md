---
title: Error 11452 Merchant not enabled for reference transactions?
categories: questions
tags: error-messages,paypal,troubleshooting
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/187
toc-enable: false
---

This error occurs only with PayPal Pro (Payflow Edition); i.e., when s2Member Pro has been integrated with PayPal Pro-Forms, and you are attempting to charge on a recurring basis. In addition, this errors occurs only when a customer attempts to complete checkout via PayPal Express Checkout.

## Why Am I Seeing This Error?

With PayPal Pro (Payflow Edition), in order to charge PayPal customers via Express Checkout on a recurring basis, you need to have both "Recurring Billing" and "Reference Transactions" enabled in your PayPal account.

- To enable Recurring Billing, please see: [PayPal Pro Recurring Billing](http://s2member.com/r/paypal-pro-recurring/)
- Reference Transactions require approval; i.e., it requires that you [contact PayPal](http://s2member.com/r/paypal-contact/). Please see: [How to Set up a Reference Transaction Using Express Checkout](http://s2member.com/r/paypal-reference-transactions/)

   > To request approval for a live PayPal account, contact [PayPal Customer Support](http://s2member.com/r/paypal-contact/).

---

## It Works w/ PayPal Buttons, Not With PayPal Express Checkout?

Correct. This is not an issue with PayPal Buttons. It's only an issue when you are integrating with PayPal Pro (Payflow Edition), and when you want to charge PayPal customers on a recurring basis via Express Checkout.

_**Note:** PayPal Express Checkout is used in Pro-Form integrations, and while this might appear to be same process that occurs when "Buttons" are used, it is actually using an entirely different API; i.e., there is a big difference between PayPal "Buttons" and PayPal Express Checkout. In order to charge customers on a recurring basis via PayPal Express Checkout, Reference Tranactions must be enabled so that s2Member Pro can acquire a Billing Agreement with the PayPal API._