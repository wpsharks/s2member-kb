---
title: Troubleshooting Email Delivery Problems
categories: tutorials
tags: troubleshooting, email-config
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/140
---

## Is s2Member Actually Sending Emails?

To check if s2Member is actually sending the emails that you're expecting, please install the [WP Mail Logging](https://wordpress.org/plugins/wp-mail-logging/) plugin. From the plugin's description:

> Logs each email sent by WordPress. This can be useful if you don't want to lose such mail contents. It can also be useful for debugging purposes. Features of the plugin include:
> - Complete list of sent mails - view and search through the mails.
> - Zero-configuration - just install and enjoy.
> - Log rotation - decide which emails you want to keep.
> - Developer: Boost your development performance by keeping track of sent mails.
> - Developer: Filters are provided to extend the columns.

## Check your s2Member Log Files

If s2Member is _not_ sending emails, this could be related to a problem that occurred during post-processing of a customer's transaction. To find out if _that's_ the issue, please enable s2Member's own logging functionality and review your log files. Please see: **Dashboard → s2Member → Log Files (Debug)** for more information.

## Ensuring Reliable Email Delivery

By default, WordPress and s2Member will use your local web server to send emails (i.e., the PHP `mail()` function). Sometimes this can cause problems. Email servers may not trust your web server to send emails, and it could mark those emails as spam (or simply not deliver them at all). To avoid this issue, you should configure WordPress to send all email using an SMTP server that can be trusted (e.g., Mandrill, Amazon SES, Google GMail, or another). You can do this by installing and configuring the [WP Mail SMTP plugin](http://wordpress.org/extend/plugins/wp-mail-smtp/).

## Ending Up in the Spam Folder?

There's also the possibility that your email is ending up in the Spam folder. If you find that to be the case, you can improve your chances of making the Inbox by editing the email so it's unique instead of having the default template.

<div class="li-margins"></div>

- The Signup Confirmation email can be edited from:
  **Dashboard → [Payment Gateway] Options → Signup Confirmation Email**

- The New User email can be edited from:
  **Dashboard → General Options → Email Configuration**

_**Note:** Configuring a reliable/trusted SMTP server can help with Spam issues also._