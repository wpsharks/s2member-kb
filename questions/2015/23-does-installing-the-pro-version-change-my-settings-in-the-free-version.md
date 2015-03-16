---
title: Does installing the Pro version change my settings in the free version?
categories: questions
tags: pre-sale-faqs
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/23
---

> We've been running S2 Members on our site for almost 5 years now and we are only now going pro. We have a large amount of paying customers in each level and we are also integrated with BuddyPress a chat hosting system and sms system. My concern with adding the Pro plugin is that something will get messed up. If I add the Pro plugin, will it change any of my current S2 settings? Will there be any lag or issues in adding it?

Nope :-) All existing settings and integrations from the lite version remain as they were.

If it works in the free version it just works better in the Pro version! The [s2Member® Pro](http://www.s2member.com/pro/) add-on requires the s2Member® Framework (i.e., the free version) to be installed first. s2Member® Pro adds support for Stripe™, PayPal Pro, Authorize.Net, ClickBank, and many other features that are available only with s2Member Pro.

These Pro integrations have been specifically designed for compatibility with all s2Member Framework features. In other words, everything that works in the free version will _also_ work with s2Member Pro. Including, but not limited to: Membership Levels, Custom Capabilities, Content Restrictions, List Server integrations, API Notifications, Tracking Codes, Shortcodes, API Conditionals, API Functions, API Constants, General Options, Content Dripping, etc, etc.

---

There is one minor issue worth mentioning. With PayPal® Pro integration you absolutely _must_ configure a default IPN URL inside your PayPal account. Please see: **s2Member® → PayPal Options → IPN Integration** for full details—along with workarounds for any cross-domain issues you might run into. The free version of s2Member (with PayPal Standard Buttons) does _not_ require this, but with PayPal Pro you _must_ have an IPN URL configured inside your PayPal Pro account. s2Member cannot override the default IPN URL on a per-transaction basis with the PayPal Pro API.

If you're using a single PayPal Pro account for multiple cross-domain installations and you need to receive IPN notifications for each of your domains; you'll want to create a central IPN processing script that scans variables in each IPN response, forking itself out to each of your individual domains. In rare cases when this is necessary, you'll find two variables in all IPN responses for s2Member. The originating domain name (e.g., `www.example.com`) will always be included somewhere within, either: `custom` and/or `rp_invoice_id`, depending on the type of transaction. These variables can be used to test incoming IPNs and fork to the proper installation.

We've already built an example PHP script to facilitate this for you, when/if it's needed. You can download the [s2m-pro-extras.zip](http://www.s2member.com/r/s2m-pro-extras-zip/) file. You'll find `paypal-central-ipn-sample.php` inside the zip distribution. Instructions are provided in that file; i.e., the file explains how to properly configure the script and where to upload it on your web server.
