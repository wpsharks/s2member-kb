---
title: How do I Update my s2Member Configuration when Upgrading from PayPal Express to PayPal Pro?
categories: questions
tags: paypal
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/32
toc-enable: false
---

> I recently upgraded to PayPal pro to allow my customers to check out on my site. I had everything set up already in s2Member using PayPal express. Do I need to change anything in my API keys?

Review your existing PayPal configuration to verify everything in your installation of s2Member Pro is still current with your newly upgraded PayPal account; i.e., make sure all of these are filled in correctly.

- **Dashboard → s2Member (Pro) → PayPal Options → PayPal Account Details**
- **Dashboard → s2Member (Pro) → PayPal Options → PayPal IPN Integration**
- **Dashboard → s2Member (Pro) → PayPal Options → PayPal PDT/Auto-Return Integration**

Newer PayPal Pro accounts come with the Payflow API for Recurring Billing service. If you have a newer PayPal Pro account, and you wish to integrate PayPal's Recurring Billing service with s2Member Pro Forms, you will need to fill in the necessary Payflow details:

- **Dashboard → s2Member (Pro) → PayPal Options → Payflow Account Details**

---

<i class="fa fa-lightbulb-o"></i> **See also:** [Supported PayPal Account Types](https://github.com/websharks/s2member-kb/issues/165)
