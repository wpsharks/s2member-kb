---
title: How can I manually approve user accounts?
categories: questions
tags: manual-intervention
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/105
---

**Question:** How can I manually approve user accounts?

**Answer:** There are many scenarios where manual account approval might be necessary. For example, let's say that you accept payments offline but you want to use s2Member to restrict content and let users sign-up on your site. You take care of processing the payment for user offline (outside of s2Member) and then you login to your WordPress site to manually "approve" their account and give them access after receiving their payment.

What I would recommend here is that you use a Free Registration Form (`s2Member ⥱ PayPal Pro-Forms ⥱ PayPal Pro / Free Registration Forms`) to allow your members to sign up for a free account. Then, after processing their payment offline, you can come back to WordPress, search for their user account in `Dashboard ⥱ Users`, and then edit their account and select whatever Level of membership they paid for.

That would be the "manual account approval process", i.e., you are manually approving their account by changing their account from a Free Subscriber (Level 0) to a Paid Member (Level 1-4).