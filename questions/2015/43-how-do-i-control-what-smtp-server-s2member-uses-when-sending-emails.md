---
title: How do I control what SMTP server s2Member uses when sending emails?
categories: questions
tags: email-config, troubleshooting
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/43
---

s2Member will use the default WordPress routines for sending email. If you want to specify SMTP servers for sending email, or if you want to use an email service like Amazon SES or Mandrill, you'll need to install a WordPress plugin such as [WP-Mail-SMTP](https://wordpress.org/plugins/wp-mail-smtp/), which allows you to configure an SMTP server that all WordPress emails (including those from s2Member) will go through.

Configuring an SMTP server is one of the best ways to fix many common email delivery issues. If you have a GMail account, for example, you can use [Gmail's SMTP server details](http://email.about.com/od/accessinggmail/f/Gmail_SMTP_Settings.htm) to send all your WordPress emails through your Gmail account.

See also: [Troubleshooting Email Delivery Problems](https://github.com/websharks/s2member-kb/issues/140)