---
title: Why am I not receiving any emails from s2Member or WordPress?
categories: questions
tags: email-config, troubleshooting
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/44
---

There are various reasons why you or your users may not be receiving emails sent by WordPress and/or s2Member. The most common issue revolves around the delivery of the email itself. WordPress (and therefore s2Member, since s2Member is a WordPress plugin) will, by default, use whatever your hosting company has configured on the web server to send email.

However, if there is an issue with the server email configuration, WordPress (and therefore s2Member) may send emails, but those emails may never be properly delivered to their destination.

If you find that emails often go into the Spam folder of the recipient, this is also most often the result of a badly configured web server. Web servers can also sometimes become blocked by email servers, which results in failed delivery or the emails always going into the Spam folder of recipients.

The best way to ensure reliable email delivery is to configure WordPress to send all email through an SMTP server. For further details and other email troubleshooting tips, please see [Troubleshooting Email Delivery Problems](https://github.com/websharks/s2member-kb/issues/140).