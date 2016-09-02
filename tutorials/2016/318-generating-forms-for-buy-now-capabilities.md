---
title: Generating Forms for Buy Now Capabilities
categories: tutorials
tags: pro-forms, s2member, custom-capabilities
author: patdumond
github-issue: https://github.com/websharks/s2member-kb/issues/318
---

This article introduces Pro-Forms for selling *Independent Custom Capabilities*. These Independent Custom Capabilities (also called CCAPs) are a very advanced feature of s2Member. For further details on how they work see **WordPress Dashboard → s2Member (Pro) → API Scripting → Custom Capabilities** and the video [Custom Capabilities for WordPress](http://s2member.com/kb-article/video-custom-capabilities-for-wordpress/).

For further information, see these s2Member Knowledge Base Articles:

- [How Can I Sell Additional Custom Capabilities to Existing Members](http://s2member.com/kb-article/how-can-i-sell-additional-custom-capabilities-to-existing-members/)
- [Can I Use Custom Capabilities to Determine the Subscriber's MailChimp List?](http://s2member.com/kb-article/can-i-use-custom-capabilities-to-determine-the-subscribers-mailchimp-list/)

*This article is part of the [s2Member User's Guide](http://s2member.com/kb/kb-tag/s2member-users-guide/&sa=D&ust=1470238793494000&usg=AFQjCNG1q04lm4O1PV4kb07x1Gin-dmEew), a series of articles that cover the fundamentals of using s2Member*.

## Generating Forms for Buy Now Capabilities

See **WordPress Dashboard → s2Member (Pro) → PayPal Pro-Forms → Capability (Buy Now) Forms** 

![ccap-buy-now-pro-form](https://cloud.githubusercontent.com/assets/9320495/17522309/8a6ec784-5e24-11e6-87f4-84f667c47583.jpg)

With s2Member, you can sell one or more *Independent Custom Capabilities* using Buy Now functionality to **existing Members**, regardless of the Membership Level they have on your website. That is, you could sell the same Custom Capability to *Level 0 (Free Subscribers)* and *Level 4 Members* without affecting their recurring subscription in any way. This functionality gives you quite a bit of flexibility in deciding who can access what content on your website.

Independent Custom Capabilities do not rely on any specific Membership Level. That's why we call them **Independent** Custom Capabilities. They can be sold independently of the Member’s Membership Level Access and Subscription terms. However, if you intend to charge a recurring fee for CCAPs, please use a **Billing Modification Form**.

Independent Custom Capabilities can only be sold through Buy Now functionality. Buy Now involves a one-time payment for access which lasts until the Member’s Membership Level Subscription expires or is canceled. If they have a Lifetime account with your website, they will also have Lifetime access to the Independent Custom Capabilities.

### Capability (Buy Now) Form Fields

- **I want to charge**: Type in the price you want to charge one time for access as long as the Member’s Membership Level Access exists. 
- **Description**: Modify the *Description* text to describe the Independent Custom Capabilities you are selling as clearly as possible.  
- **Check out Page Style**:
    -  This is optional. You can configure [PayPal Custom Payments Page Styles](https://www.paypal.com/customize) from within your PayPal Merchant Account. If you create custom page styles, enter the name of the desired style here.
    - Select the currency you want from the drop-down box. 
- **Custom Capabilities**: This is **required** on this Pro-Form. Type in a comma-delimited list of Custom Capabilities (CCAP) you are selling with this Form. Then use the same CCAP code to set appropriate content restrictions for your website.

Once you have filled in all the form fields, click the **Generate Form Code** button and then copy the generated shortcode to a Post or Page you create in WordPress.