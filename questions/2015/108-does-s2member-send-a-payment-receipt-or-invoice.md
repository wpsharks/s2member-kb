---
title: Does s2Member send a payment receipt or automatically generate PDF invoices?
categories: questions
tags: email-config
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/108
---

By default, s2Member sends a Signup Confirmation Email with basic instructions and a polite thank-you message. However, this email (and others like it) are highly customizable. s2Member provides several Replacement Codes that you can use to turn the default Signup Confirmation Email into a receipt and/or invoice if you like.

See: **Dashboard → [Payment Gateway] Options → Signup Confirmation Email**

You'll find a full list of all Replacement Codes there, along with descriptions.

_**Note:** It is also possible to use PHP tags inside s2Member email templates. This exposes all the power of WordPress too._

_**Tip:** Along with emails that you can customize with s2Member, many payment gateways make it possible for you to have emails sent out automatically in response to completed transactions. Please review the documentation and configuration panel that is supplied by your payment gateway to learn more._

> Does s2Member support PDF invoices and/or file attachments?

No, while emails are highly customizable, they are sent in plain text. s2Member does _not_ support PDF invoice generation or PDF file attachments. If you want to generate PDF invoices on your own, or through a 3rd-party service that specializes in this, you can connect s2Member to an HTTP POST (or 3rd-party service) using s2Member's event-driven API Notifications.

Please see: **Dashboard → s2Member → API / Notifications**
