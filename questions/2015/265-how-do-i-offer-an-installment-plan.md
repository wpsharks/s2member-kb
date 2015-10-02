---
title: How do I offer an installment plan?
categories: questions
tags: pro-forms
author: raamdev
github-issue:
github-issue: https://github.com/websharks/s2member-kb/issues/265
---

The [s2Member Pro-Forms](http://s2member.com/kb-article/s2member-pro-forms/) support a Recurring Times attribute (`rrt=""`) which allows you to define the number of times a payment should recur, i.e., a fixed number of installments. Note that this functionality is only valid with Membership Level Access (i.e., when the Recurring directive is set to true (`rr="1"`, i.e., when you are creating a recurring Subscription).

When the Recurring Times (`rrt=""`) attribute is unspecified, any recurring charges will remain ongoing until cancelled, or until payments start failing. If Recurring Times (`rrt=""`) is set to `1` or higher the regular recurring charges will only continue for X billing cycles, depending on what you specify. 

### A fixed number of installments, also means a fixed period of access!

If a Customer's billing is monthly, and you set `rrt="3"`, billing will continue for only 3 monthly installments. After that, billing would stop, and their access to the site would be revoked as well (based on your EOT Behavior setting under: **Dashboard → s2Member → [Payment Gateway] Options**). 

### Preventing loss of access with installment plans

If you're only offering installment plans on your site, then you can simply disable s2Member's Automatic EOT System to prevent accounts from being downgraded once their installment completes. To disable the Automatic EOT System, see **Dashboard → s2Member → [Payment Gateway] Options → Automatic EOT Behavior**. 

### Important note regarding Trials

If you don't offer a trial period; i.e., the first charge occurs when a customer completes checkout, you should set the Recurring Times (`rrt=""`) attribute to the number of additional payments, and NOT to the total number. For instance, if I want to charge the customer a total of 3 times, and one of those charges occurs when they complete checkout, I set should set Recurring Times to 2 (`rrt="2"`) for a grand total of three charges all together.