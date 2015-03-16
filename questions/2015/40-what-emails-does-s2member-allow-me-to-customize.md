---
title: What emails does s2Member allow me to customize?
categories: questions
tags: email-config
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/40
---

s2Member allows you to customize _some_ of the emails that WordPress normally sends out, specifically the _New User_ email that the user receives when their account gets created, and the _Administrative New User_ notification email (the email the administrator receives when a new account is created); both of these can be customized here:

- **Dashboard → s2Member → General Options → Email Configuration → New User Email Configuration**

There's also the Signup Confirmation email, which is the email sent to new Customers after they return from a successful signup (replace `[Payment Gateway]` with whatever payment gateway you're using; e.g., `PayPal`):

- **Dashboard → s2Member → [Payment Gateway] Options → Signup Confirmation (Standard)**
- **Dashboard → s2Member → [Payment Gateway] Options → Signup Confirmation (Pro)**

Any other emails that you see are most likely coming from WordPress itself. If you want to customize WordPress-related emails, I suggest posting a question on the [WordPress Support Forum](http://wordpress.org/support/).

![2015-01-16_18-17-34](https://cloud.githubusercontent.com/assets/53005/5785976/0678f740-9dac-11e4-9d7d-5739bf77dfbf.png)