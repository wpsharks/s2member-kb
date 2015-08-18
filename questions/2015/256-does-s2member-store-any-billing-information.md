---
title: Does s2Member store any billing information?
categories: questions
tags: billing, pre-sale-faqs
author: raamdev
toc-enable: off
github-issue: https://github.com/websharks/s2member-kb/issues/256
---

s2Member does not store any billing or credit card information. At the time of purchase, the billing and payment information is sent securely to the payment gateway (e.g., PayPal or Stripe) using modern encryption technologies (SSL). 

s2Member retains no records of the information that was sent to the payment gateway for billing purposes (with one exception: when logging is enabled; see below). Instead, s2Member listens for messages from the payment gateway so that if a recurring payment (or a one-time payment) fails, s2Member can use the success/failure notification to determine what to do (to grant access, deny access, or revoke existing access). All of that is handled by s2Member automatically behind the scenes, between s2Member and the payment gateway.

## What about personal information?

The only personal member information that s2Member will store inside your WordPress database are the member's First Name, Last Name, Email Address, Username, IP Address used during registration, Payment Gateway used (e.g., PayPal, Stripe, Authorize.Net, etc.), Subscriber ID and/or Transaction Number from the payment gateway, and any other information that you choose to collect as part of your registration process through Custom Registration/Profile Fields (again, excluding any billing address or specific payment details).

If you do not create any new Custom Registration/Profile Fields (**Dashboard → s2Member → General Options → Registration/Profile Fields & Options**), only the data described above will be collected for each member. 

You can review the information collected for each member by editing the member's account inside the WordPress Dashboard (**Dashboard → Users → Edit User**).

## One Special Exception: s2Member Logging

s2Member log files do contain personally identifiable information and even credit card numbers, expiration dates, CVV codes, API credentials, and more. We do our best to XXXX those out, but the purpose of log files is to gather information for the purpose of debugging the software and/or your site.

s2Member Logging is disabled by default (see **Dashboard → s2Member → Log Files (Debug) → Logging Configuration**). If you enable logging for debugging purposes, we highly recommend that logging be disabled once your site goes live.
