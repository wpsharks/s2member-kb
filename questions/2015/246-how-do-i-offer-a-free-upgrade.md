---
title: How do I offer a free upgrade?
categories: questions
tags: pro-forms, billing-modification, billing
author: raamdev
github-issue:
github-issue: https://github.com/websharks/s2member-kb/issues/246
---

Using the Billing Modification Forms, you can generate an Upgrade Form that will modify a users account to upgrade or downgrade their account, and/or add or remove Custom Capabilities from their account. You can charge for this upgrade, offer a [Pro Coupon Code](http://s2member.com/kb-article/how-can-i-give-a-coupon-code-to-existing-users/) to discount the upgrade, or even offer the upgrade for free entirely, without the need to enter a coupon code.

This article explains how to generate a Free Upgrade form, which will allow existing users to upgrade their Level and/or add Custom Capabilities to their account without being charged at all.

## Configuring and Generating the Upgrade Form

The first step will be to generate a Billing Modification Form with the necessary upgrade details. See **Dashboard → s2Member → [Payment Gateway] Pro-Forms → [Payment Gateway] Billing Modification Forms**. From here you can specify the Level and/or Custom Capabilities that should be added to the users account when they use this form to upgrade. Since this will be a free upgrade form, you'll want to change the Trial Amount and the Charge amount to `$0.00`; this makes the upgrade free.

![2015-07-31_13-00-44](https://cloud.githubusercontent.com/assets/53005/9014010/9616cda2-378d-11e5-8ac9-0200e665178e.png)

If you only want to add Custom Capabilities and don't want to modify the users' Level, you can simply set the Modification to "Upgrade to" the Level of the user. So for Level 1 users, you would simply set Modification to "Upgrade to Level 1" and then add your Custom Capabilities. That will have the effect of only adding Custom Capabilities and not changing the users Level.

If you're using several different levels of membership and you only want to use a single Upgrade page, you can use shortcode conditionals to show different forms for different level users. See **Dashboard → s2Member → API / Scripting → Simple/Shortcode Conditionals**. 

Once you've configured the generator and clicked the "Generate Form Code" button, copy the resulting shortcode onto your Upgrade page. The shortcode should look something like this:

> [s2Member-Pro-PayPal-Form modify="1" level="4" ccaps="" desc="Free Level 4 Upgrade!" ps="paypal" lc="" cc="USD" dg="0" ns="1" ta="0" tp="0" tt="D" ra="0" rp="1" rt="M" rr="1" rrt="" rra="2" accept="paypal" accept_via_paypal="paypal" coupon="" accept_coupons="0" default_country_code="" captcha="0" /]

You can review a description of each of the shortcode attributes in **Dashboard → s2Member → [Payment Gateway] Pro-Forms → Shortcode Attributes (Explained)**.

## Using the Upgrade Form

The upgrade form will only work correctly if the user is logged in when visiting the page, so we recommend restricting the page to at least Level 0. Or, you could use a shortcode conditional to check if the person visiting the page is logged in and show an appropriate message if they're not.

Once a logged-in visitor visits the upgrade page, they will see a form like the one below. Their existing account details will already be filled in and all they need to do is click the "Submit Form" button to have their account upgraded.

![2015-07-31_13-11-34](https://cloud.githubusercontent.com/assets/53005/9014161/97e83bd8-378e-11e5-89df-c82353cf5cf7.png)

Once the form is submitted and their account successfully upgraded, the will see a message indicating as much:

![2015-07-31_13-08-11](https://cloud.githubusercontent.com/assets/53005/9013963/4f8127c0-378d-11e5-9a51-7c0928172df3.png)

If you'd rather have the form redirect the user to a special page that explains how their account has been upgraded, you can use the `success=""` shortcode attribute to specify a custom URL where the user should be redirected to after their account has been successfully upgraded. 

See **Dashboard → s2Member → [Payment Gateway] Pro-Forms → Shortcode Attributes (Explained)** for further information about the `success=""` shortcode attribute.

## Building Your Own Upgrade Form

If you want full control over the upgrade process, you can build your own form and combine it with the examples here: [Roles/Capabilities via PHP](http://s2member.com/kb-article/rolescapabilities-via-php/)