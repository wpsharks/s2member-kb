---
title: Forms for Level 0 (Free Registration) to Level x Access
categories: tutorials
tags: pro-forms, paypal, membership-levels, shortcodes
author: patdumond
github-issue: https://github.com/websharks/s2member-kb/issues/315
---

In this article, we will show you how to generate Pro-Forms for Membership-Level Access registration. Pro-Forms are an s2Member Pro Add-on feature and are not available with the free s2Member Framework. Pro-Forms are available for *Free Registration*, *PayPal Payments Pro*, *Stripe*, and *Authorize.net*.

The generation process is the same for each type of Pro-Form, but you need to generate each particular payment gateway’s Pro-Forms using the panels found on the s2Member Pro-Forms configuration for that gateway. For simplicity’s sake, we are using the PayPal Pro-Forms generators found here **WordPress Dashboard → s2Member (Pro) → PayPal Pro-Forms** in this article. Where differences between gateways exist, they are specified.

*This article is part of the [s2Member User's Guide](http://s2member.com/kb/kb-tag/s2member-users-guide/&sa=D&ust=1470254380914000&usg=AFQjCNHgE98nZQ3WeJbrmy8j0Xnjoka2Jg), a series of articles that cover the fundamentals of using s2Member.*

## Free Registration Forms

See **WordPress Dashboard → s2Member (Pro) → PayPal Pro-Forms → Free Registration Forms**

_Note: PayPal is NOT required to use the Free Registration forms. If you're not using PayPal, simply ignore the PayPal configuration and generate the Free Registration Pro-Forms; these will work without configuring PayPal._

![Free Registration Pro-Forms](https://cloud.githubusercontent.com/assets/9320495/18010070/fcf88bcc-6b7c-11e6-822d-d673742cfbcd.png)

These Forms are used to create registration forms for *Free Subscribers* (**s2Member Level 0**). Whenever a visitor registers without paying, they'll automatically become a Free Subscriber, at s2Member Level 0. This is true whether they use a Pro-Form, the WordPress default registration form, or a custom registration form of your own.

**Note**: Use of a *Free Registration Form* will override your *Open Registration* configuration (**WP Dashboard → s2Member (Pro) → General Options → Open Registration**. This makes it possible for you to integrate this *Free Registration Form* in creative ways (making it available only under circumstances of your choosing via a Page or Post) while still leaving *Open Registration* disabled on the rest of your website.

**Tip (optional)**: It is possible to change the `level="0"` Attribute to something other than the default Level #0 (Free Subscriber). For example, you can change it to `level="1"`. Or you can attach Custom Capabilities with the `ccaps=""` Attribute.  You can even limit this access to a certain timeframe with a trial period (`tp="30" tt="D"` = 30 Days). So this Form is very flexible. It can be used to allow free access to just about any aspect of your service. For more information on Attributes, please see **Dashboard → s2Member → PayPal Pro-Forms → Shortcode Attributes (Explained)**.

## Forms for s2Member Level 1-4 Access

- Level 1: **WordPress Dashboard → s2Member (Pro) → PayPal Pro-Forms → Forms for Level #1 Access**
- Level 2: **WordPress Dashboard → s2Member (Pro) → PayPal Pro-Forms → Forms for Level #2 Access**
- Level 3: **WordPress Dashboard → s2Member (Pro) → PayPal Pro-Forms → Forms for Level #3 Access**
- Level 4: **WordPress Dashboard → s2Member (Pro) → PayPal Pro-Forms → Forms for Level #4 Access**

**Tip**: There are separate Pro-Form Generators for **s2Member Levels 1 – 4**.  I will let you in on a "secret" though: they all work the same. All you need to do is to change the `level=”1”` to `level=”whatever you want”` in the beginning of the shortcode. However, unless you are generating a shortcode for a **Level #** above 4, it is best to use the appropriate Pro-Form Generator to avoid errors.

![level-x-access-pro-forms](https://cloud.githubusercontent.com/assets/9320495/18009947/6e891596-6b7c-11e6-83f5-f582c8053865.png)

To generate your shortcodes, all you do is customize the form fields provided for each Membership Level that you plan to offer. Then press the **Generate Form Code** button. Then you copy and paste the generated shortcode to a Post or Page created with WordPress. You must provide website visitors with a link to the Post or Page where the form is located. Our recommendation is to place a link on your *Membership Options Page* (s2Member redirects visitors here when they try to access restricted content). That way your visitors can get registered and check out with minimal confusion after redirection.

Member accounts will be activated instantly. When you, or a Member, cancels their Membership or fails to make payments on time, s2Member will automatically terminate their Membership privileges via the IPN service of the payment gateway.

**Note**: s2Member does not save the shortcodes generated here. When you come back to create a new shortcode, you’ll need to fill in all the Form fields again.
