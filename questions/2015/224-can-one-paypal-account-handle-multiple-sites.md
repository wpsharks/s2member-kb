---
title: Can one PayPal account handle multiple sites / plugins?
categories: questions
tags: paypal
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/224
toc-enable: off
---

Yes, if you have multiple sites (or multiple plugins) that are all configured to use the same PayPal account that you plan to use with s2Member, this will generally work fine (there is one exception; see below).

The IPN URL is where PayPal sends notifications about payments, cancellations, etc., so the IPN URL must be pointing to the site or plugin that originated the transaction. If you're using s2Member and someone signs up with s2Member, PayPal must send the IPN notification to the s2Member IPN URL.

PayPal only allows you to configure one IPN URL inside your PayPal account, however that's not a problem because in addition to [the default IPN settings inside your PayPal account](http://www.s2member.com/paypal-ipn-setup), the IPN URL is also set on a per-transaction basis by the special PayPal Button Code that s2Member provides you with. 

In other words, if you have multiple sites operating on one PayPal account, that's OK. s2Member dynamically sets the IPN URL for each transaction. The result is that the IPN URL configured from within your PayPal account, becomes the default, which is then overwritten on a per-transaction basis. 

In fact, PayPal recently updated their system to support IPN URL preservation. One PayPal account can handle multiple sites, all using different IPN URLs.

If you're not sure if the other plugin that you're connecting to PayPal supports setting the IPN URL on a per-transaction basis, you can point your PayPal Account to the IPN URL for the other plugin and then let s2Member handle setting the IPN URL whenever an s2Member transaction takes place.

## One Exception: PayPal Pro 

The above is NOT true w/ PayPal Pro: With PayPal Pro integration you absolutely must set an IPN URL inside your PayPal account. PayPal Pro integration does not allow the IPN location to be overridden on a per-transaction basis. 

If you're using a single PayPal Pro account for multiple cross-domain installations, and you need to receive IPN notifications for each of your domains; you'll want to create a central IPN processing script that scans variables in each IPN response, forking itself out to each of your individual domains. 

In the rare cases when this is necessary, you'll find two variables in all IPN responses for s2Member. The originating domain name (e.g., `example.com`) will always be included somewhere within, either: `custom` and/or `rp_invoice_id`; depending on the type of transaction. These variables can be used to test incoming IPNs, and fork to the proper installation. For your convenience, an example script has been provided inside: `/s2m-pro-extras/paypal-central-ipn.php`. You can download all Extras here: [s2m-pro-extras.zip](http://www.s2member.com/r/s2m-pro-extras-zip/).
