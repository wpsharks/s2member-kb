---
title: Configuring s2Member Payment Gateways
categories: tutorials
tags: authorize-net, auto-return, clickbank, log-files-debug, paypal, pci-compliance, pro-forms, stripe, s2member-users-guide
author: patdumond
github-issue: https://github.com/websharks/s2member-kb/issues/306
---

In this article, you’ll be introduced to *s2Member’s* supported payment gateways: *PayPal*, *Stripe*, *Authorize.net*, and *ClickBank*. This Knowledge Base Article covers configuration options common to all of the payment gateways. Configurations unique to a particular gateway are covered in separate articles for each gateway:

- [PayPal](https://github.com/websharks/s2member-kb/issues/311)
- [Stripe](https://github.com/websharks/s2member-kb/issues/312)
- [Authorize.net](https://github.com/websharks/s2member-kb/issues/313)
- [ClickBank](https://github.com/websharks/s2member-kb/issues/314)


*This article is part of the [s2Member User's Guide](http://s2member.com/kb/kb-tag/s2member-users-guide/), a series of articles that cover the fundamentals of using s2Member.*

## Supported Payment Gateways

*s2Member Pro* supports the payment gateways listed below. All payment gateways support both *Buy Now* and *Recurring* payments. The only payment gateway supported in the free *s2Member Framework* is *PayPal Website Payments Standard*.

- *PayPal Website Payments Standard* w/Buttons [s2Member Framework] [s2Member Pro] 
- *PayPal Website Payments Pro* w/Pro-Forms [s2Member Pro] 
- *Stripe + Bitcoin* w/Pro-Forms [s2Member Pro] 
- *Authorize.net* w/Pro-Forms [s2Member Pro] 
- *ClickBank* w/Buttons [s2Member Pro]

## Enabling Payment Gateways in s2Member Pro

To enable payment gateways other than *PayPal Website Payments Standard* in *s2Member Pro*, go to **WordPress Dashboard → s2Member (Pro) → Other Gateways**. Select the gateways you would like to use on your website by clicking on the check box next to the gateway name (or names) and then clicking the **Save Changes, (then refresh)** button at the bottom of the page.

**Tip:**  Keep in mind that *s2Member* can support multiple payment gateways on a single website, but can only support one account for each gateway selected.

## Configurations Common to All Payment Gateways

### Secure Server

Most payment gateways require all traffic between your website and their’s to be encrypted using SSL (sent via `https://`). To comply with payment gateway and [PCI Compliance](https://s2member.com/kb-article/pci-compliance/) policies as set forth by major credit card companies, you should host all of your **s2Member Pro-Forms and Buttons** on an SSL-enabled site. Please check with your hosting provider to ask about obtaining an SSL certificate for your domain.

When you create **Pro-Forms** with *s2Member*, you'll be supplied with *WordPress* shortcodes. You'll insert these shortcodes into **Posts** or **Pages** of your choosing. These **Posts** and **Pages** need to be displayed in SSL mode using links that start with (`https://`).

### SSL Compatibility

Most modern themes include full support for SSL as does *WordPress* itself. However there are still many themes and plugins that do **not** support SSL-enabled **Posts** and **Pages** properly. For this reason, you should be very careful when choosing *WordPress* themes and plugins to use with *s2Member Pro*. Otherwise, your visitors could see the infamous "Secure/Insecure" warnings in their browser.

With *s2Member* installed, you can add the [Custom Field](https://codex.wordpress.org/Custom_Fields#Usage) `s2member_force_ssl = yes` to any **Post** or **Page**. *s2Member* buffers output on those **Posts** or **Pages**, converting everything over to `https://` for you automatically. Forcing those specific **Posts** and **Pages** to be viewed over a secure SSL connection, assuming as your server supports the `https` protocol. Alternatively, you could force your entire site to be displayed via `https://` as detailed in the following *s2Member Knowledge Base* articles.

- [Introduction to TLS/SSL and Why You Need It on Your s2Member Site](https://s2member.com/kb-article/introduction-to-tlsssl-and-why-you-need-it-on-your-s2member-site/)
- [Implementing SSL (HTTPS) on an s2Member Site](https://s2member.com/kb-article/implementing-ssl-https-on-an-s2member-site/)
- [Forcing SSL](https://www.s2member.com/forums/topic/forcing-ssl/)

### Global Pro-Form Settings

The settings below are global to s2Member. They can be set under any of the payment gateways but apply to all payment gateways. In other words, if you change the settings under *PayPal Options* they also change under *Stripe Options*. You need only configure them once, even if using multiple **Payment Gateways**. For simplicity's sake, I show the dashboard location for *PayPal*.

#### Tax Rate Calculations (Pro-Form)

See: **WordPress Dashboard → s2Member (Pro) → PayPal Options → Tax Rate Calculations (Pro-Form)**

![global-tax-rate-calculation](https://cloud.githubusercontent.com/assets/9320495/15786555/44e8a202-298b-11e6-8aa0-3f5860179760.jpg)

These **Tax Rate Calculations** are used only for **s2Member Pro-Form** integrations, not for **PayPal Buttons** or any other *Button* transactions your site might conduct. 

The website owner is solely responsible for ensuring that the software is configured to charge all required taxes for all locations in which he does business. Your software (*s2Member Pro*) is solely responsible for calculating these **Tax Rates** for your transactions: the payment gateways do not do it for you. 

In the fields on this *s2Member* panel (**WordPress Dashboard → s2Member (Pro) → PayPal Options → Tax Rate Calculations (Pro-Form)**), you can set your tax rates. You can set a **Global Default Tax Rate** for all transactions. Alternatively, you can use a **Custom Tax Configuration File** for specific countries, states, provinces, and zip code ranges. **Tax Rate** calculations are fully compatible with international currencies and locations.

When you create a **PayPal Pro-Form** with *s2Member*, you'll be asked to supply a **Charge Amount**. Then, during checkout *s2Member* calculates **Tax**. *s2Member* adds the calculated **Tax Rate** to the **Charge Amount** in your  **PayPal Pro** shortcode. The **Tax Rate** will be displayed to a Customer during checkout after they've supplied a **Billing Address**. For example, if you create a **PayPal Pro-Form** that charges a Customer $24.95, and the **Tax Rate** is configured as 7.0%, *s2Member* will calculate the **Tax** as $1.75. A Customer will pay the **Total Amount** (**Charge** + **Tax** = $26.70).

**Tip**: If you configure **Tax**, you should include a note somewhere in the `desc=""` attribute of your shortcode. Something like `desc="$x.xx (plus x% tax)"`.

##### Global Default Tax Rate

This can be a flat tax (1.75), or a percentage (7.0%).

##### Custom Tax Configuration File

Here you can enter different **Tax Rates** by country, state/province, or zip code range. Use any *one* of the following formats on each line:

- **2-CHARACTER COUNTRY CODE** = Flat rate or percentage — low precedence
- **STATE OR PROVINCE/2-CHARACTER COUNTRY CODE** = Flat rate or percentage — higher precedence
- **ZIP CODE-ZIP CODE/2-CHARACTER COUNTRY CODE** = Flat rate or percentage — higher precedence (zip code range)
- **ZIP CODE/2-CHARACTER COUNTRY CODE** = Flat rate or percentage — highest precedence (specific zip code)

#### Automatic EOT Behavior

See: **WordPress Dashboard → s2Member (Pro) → PayPal Options → Automatic EOT Behavior**

**This information is REQUIRED.**

**EOT** = End Of Term.

By default, *s2Member* will demote a paid *Member* to a *Free Subscriber* whenever their *Subscription* term has ended, been canceled, refunded, charged back to you, etc. *s2Member* demotes them to a *Free Subscriber*, so they will no longer have *Member Level Access* to your site. However, in some cases, you may prefer to have Customer accounts deleted, instead of just being demoted.

This panel (**WordPress Dashboard → s2Member (Pro) → PayPal Options → Automatic EOT Behavior**) is where you choose which method works best for your site. If you don't want *s2Member* to take any action at all, you can disable *s2Member's* **EOT System** temporarily, or even completely. There are also a few other configurable options here, so please read carefully. These options are all critical.

**IPNs**: The *IPN* service of your payment gateway will notify *s2Member* whenever a Member's payments have been failing, or whenever a Member's *Subscription* has expired for any reason. The IPN service supports refunds & chargeback reversals as well. For example, if you issue a refund to an unhappy Customer through *PayPal*, *s2Member* will eventually be notified, and the account for that Customer will either be demoted to a Free Subscriber, or deleted automatically (based on your configuration). The communication from the payment gateway to *s2Member* is seamless.

**Some Hairy Details**: There might be times whenever you notice that a Member's Subscription was canceled through the payment gateway, but *s2Member* continues allowing the Member access to your site as a paid Member. Please don't be confused by this. in 99.9% of these cases the reason for this is legitimate. *s2Member* will only remove the Member’s Membership privileges when an EOT (End Of Term) processes, a refund occurs, a chargeback occurs, or when a cancellation occurs - which would later result in a delayed Auto-EOT by *s2Member*.

*s2Member* will not process an EOT until the Member has completely used up their paid time. In other words, if a Member signs up for a monthly Subscription on Jan 1st, and then cancels their Subscription on Jan 15th, they should still be allowed to access the site for another 15 days. Then on Feb 1st, the time they paid for has completely elapsed.

At that point, *s2Member* will remove their Membership privileges; by either demoting them to a *Free Subscriber*, or deleting their account from the system based on your configuration. *s2Member*also calculates one extra day (24 hours) into its equation, just to make sure it doesn't remove access sooner than a Member might expect.

![global-auto-eot-behvior1](https://cloud.githubusercontent.com/assets/9320495/15786577/5d483fa6-298b-11e6-9763-e29d5ee95307.jpg)

##### Enable s2Member’s Auto-EOT System? 

Choose:

- *Yes – Enable through WP-Cron*
- *Yes – I’ll run my own Cron job*
- *No*

The recommended setting is *Yes - enable through WP-Cron*.

##### Membership EOT Behavior (Demote or Delete)?

Choose *Demote* or *Delete*  whichever is appropriate for your membership site.

##### Membership EOTs also Remove all Custom Capabilities?

You can choose whether to remove **all** *Custom Capabilities* when a user is *Demoted* or allow them to carry-over the *Custom Capabilities* as a *Free Subscriber*.

**Note: If Refunds/Reversals** trigger an Immediate **EOT** *Custom Capabilities* will always be removed when a **Refund** or **Reversal** occurs. In other words, this setting is ignored for **Refunds/Reversals** (If they trigger an Immediate **EOT** based on your configuration). If you prefer to review all **Refunds/Reversals** for yourself, please choose that option.

![global-auto-eot-behvior2](https://cloud.githubusercontent.com/assets/9320495/15786584/65e10440-298b-11e6-9b82-b837565beaa5.jpg)

##### EOT Grace Time (in seconds): The default is 86400 seconds (one day).

*s2Member* applies a grace time to the calculated **EOT** to ensure that the Member's Subscription terminates as expected even though the Member may live in a time zone halfway across the world from your web server. The default grace time is 86400 seconds, one day. 

##### Refunds/Partial Refunds/Reversals (trigger Immediate EOT)?

**Note:***s2Member* is not equipped to detect partial refunds against multi-payment  *Subscriptions* reliably. Therefore, all refunds processed against *Subscriptions* (of any kind) are considered **Partial Refunds**. Full refunds (in the eyes of *s2Member*) occur only against *Buy Now* transactions where it is easy for *s2Member* to see that the refund amount is the same as the original *Buy Now* purchase price (a **Full Refund**).  This setting (no matter what you choose) will **not** impact *s2Member's* internal **API Notifications for Refund/Reversal** events. 

A **Full** or **Partial Refund** or a **Reversal Notification** will **always** be processed internally by *s2Member*, even if no action should be taken per your configuration here.

In this way, you’ll have the ability to listen for these events on your own (via **API Notifications**), if you prefer. For more information, see **WordPress Dashboard → s2Member® (Pro) → API Notifications → Refunds/Reversals**.

##### Fixed-Term Extensions (Auto-Extend)? 

This setting controls whether extensions of fixed-term memberships automatically extend the Member’s existing subscription. This setting will only affect **Buy Now** transactions for fixed-term lengths. By default, *s2Member* will automatically extend any existing **EOT Time** that a Member may have. For example, if I buy one year of access, and then I buy another year of access (before my first year is used up), I end up with everything I paid you for (now over one year of access) if this is set to *Yes*. If this were set to *No*, the **EOT Time** would be reset when I made the second purchase. This leaves me with only one year of access starting the date of my second purchase.

##### Enable Logging Routines?

Set this to *Yes* or *No* as appropriate. We highly recommend that you enable logging during your initial testing phase. Logs produce lots of useful details that can help in debugging. Logs can help you find issues in your configuration and problems during payment processing.

**Tip**: It is crucial to disable logging once you go live. Log files may contain personally identifiable information, credit card numbers, secret API credentials, passwords, and other sensitive information. **We suggest that logging be disabled on a live site (for security reasons)**.
