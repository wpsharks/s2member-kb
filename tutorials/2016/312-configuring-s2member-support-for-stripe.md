---
title: Configuring s2Member Support for Stripe
categories: tutorials
tags: auto-return, pro-forms, stripe
author: patdumond
github-issue: https://github.com/websharks/s2member-kb/issues/312
---

This Knowledge Base Article covers setting up *s2Member* to work with *Stripe*. *Stripe* absolutely rocks! It is a developer-friendly way to accept payments online and in mobile apps. They process billions of dollars a year for thousands of companies of all sizes. It is easy to integrate and easy for customers to use.

*Stripe* charges no monthly fees. Their per-transaction fees are in line with *PayPal* and (after your first transaction, which can take up to fourteen days to process), *Stripe*  transfers received funds to your bank account within three business days. 

*s2Member Pro* has been integrated with *Stripe* for *Direct Payments* and also for *Subscriptions* (*Automated Recurring Billing*). To take advantage of this integration, you will need to have a *Stripe Merchant Account* (it is free). Once you have an account, all of the details below can be obtained from your *Stripe* account. If you need assistance, please check their [help section](http://www.s2member.com/r/stripe-help/).

*This article is part of the [s2Member User's Guide](http://s2member.com/kb/kb-tag/s2member-users-guide/), a series of articles that cover the fundamentals of using s2Member.*

### Stripe Account Details

See **WordPress Dashboard → s2Member (Pro) → Stripe Options → Account Details**
**This section is required (if you are using *Stripe*).**

![stripe-account-details-1](https://cloud.githubusercontent.com/assets/9320495/15786597/774754e6-298b-11e6-9617-4938d16369cc.jpg)

- **Stripe Secret API Key**: You'll find this in your *Stripe Merchant Account* under **Account Settings → API Keys**.
- **Stripe Publishable API Key**: You'll find this in your *Stripe Merchant Account* under **Account Settings → API Keys**.

#### Accept Bitcoin via Stripe

Works for *Buy Now* (non-recurring) transactions in US Dollars only. Other currency conversions are not supported by *Stripe* at this time. Turning this on requires that you enable *Bitcoin* transactions in your Stripe account. Click the link shown in the screenshot below in your **Stripe Account Details** panel to do this automatically.

![stripe-account-details-bitcoin-enabler](https://cloud.githubusercontent.com/assets/9320495/15786676/f3a9d40a-298b-11e6-8350-08b34c0249c8.jpg)

**Tip**: This setting for *Bitcoin* is a global flag that enables *Bitcoin* for all **Stripe Pro-Forms** that offer a *Buy Now* item. You can also enable or disable *Bitcoin* in specific **Stripe Pro-Forms**, overriding your setting here, by adding the shortcode attribute `accept="bitcoin"` (to enable *Bitcoin*) or `accept=""` (to disable *Bitcoin*) to any **Stripe Pro-Form**. For further details, please see **WordPress Dashboard → s2Member (Pro) → Stripe Pro-Forms → Shortcode Attributes (Explained)**.

- **Stripe Image Branding**: Here you can configure an image that *Stripe* will display above the credit card input fields. `HTTPS` is recommended here. The minimum size for this picture is 128px  by 128px. **Note**: If you leave this empty an account-level default value may or may not be displayed by *Stripe*. It's best to configure it here.

![stripe-account-details-2](https://cloud.githubusercontent.com/assets/9320495/15786688/fed68d28-298b-11e6-91cf-ed0a8b2bd138.jpg)

- **Stripe Statement Description**: This is an arbitrary string (15 characters max) to be displayed alongside your company name. The **Stripe Statement Description** appears on your Customer’s credit card statement. The **Stripe Statement Description** may **not** include these special characters: `<`, `>`, `"`,`'`. **Note**: If you leave this empty, *Stripe* uses an account-level default value (configured in *Stripe*) instead.

![stripe-account-details-3](https://cloud.githubusercontent.com/assets/9320495/15786708/12287f58-298c-11e6-938e-92dceffc8b5a.jpg)

### Stripe Webhook/IPN Integration

See **WordPress Dashboard → s2Member (Pro) → Stripe Options → Stripe Webhook/IPN Integration.**

**This section is required (if you are using *Stripe*)**. 

![stripe-webhook-ipn-integration](https://cloud.githubusercontent.com/assets/9320495/15786715/1c7fd6f4-298c-11e6-9b86-e6dfff0c37c7.jpg)

Log into your *Stripe Merchant Account* and navigate to **Account Settings → Webhooks**. Click on the **Add Endpoint** button.

![stripe-webhook-account-settings-webhooks](https://cloud.githubusercontent.com/assets/9320495/15786718/2291dca4-298c-11e6-91f3-cf28a23c86b6.jpg)

Copy the **Stripe Webhook URL** shown on the **s2Member Stripe Webhook/IPN Integration** panel to the **URL** field on the pop-up window at *Stripe*. Click the **Create Endpoint** button and then click the **Done** button on the **Endpoints** window.

**Note**: If your site is currently in *Test/Sandbox* mode and you entered **Test API Credentials** in the **Stripe Account Details** panel, please choose the *Test* option when creating your Webhook endpoint at *Stripe* (described above). Otherwise, choose *Live*.
