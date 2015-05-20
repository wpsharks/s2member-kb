---
title: Creating a Free Membership with a Trial Period (Limited-Time Free Membership)
categories: tutorials
tags: pro-forms, 
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/212
---

s2Member Pro enables the s2Member Pro-Forms, which includes Free Registration Forms. Using these forms in combination with a Trial Period, you can offer a limited-time Free Membership. 

**Note:** These Free Registration forms _do not_ require the associated payment gateway to be configured, as the Free Registration forms do not make any contact with a payment gateway. If all you're going to use are the Free Registration forms on your site, you can skip the payment gateway configuration and ignore any associated warning messages.

## Step 1: Generate the Free Registration Pro-Form

Visit **Dashboard → s2Member → PayPal Pro-Forms → PayPal Pro / Free Registration Forms** to generate the Free Registration Pro-Form. (If you're not using the payment gateway features at all, it doesn't matter if you use the **Stripe Pro-Forms** or the **PayPal Pro-Forms** section to generate the Free Registration forms--they do the same thing.)

Copy the generated WordPress Shortcode at the bottom:

![2015-05-20_11-28-05](https://cloud.githubusercontent.com/assets/53005/7729635/de08e1d2-fee3-11e4-854f-7eecfd424be7.png)

## Step 2: Modify Shortcode to add a Trial Period (Limited-Time Access)

When you add the WordPress Shortcode you copied in the previous step to a WordPress Page on your site (e.g., the page where you want to put the Free Registration Pro-Form), you'll notice that the shortcode contains these two attributes: `tp="0" tt="D"`.

Those attribute define a Trial Period (`tp`) and a Trial Term (`tt`). For the Trial Term, possible values are: `D` = Days, `W` = Weeks, `M` = Months, `Y` = Years. The Trial Period is a whole number. (For more information on Shortcode Attributes, see **Dashboard → s2Member → PayPal Pro-Forms → Shortcode Attributes (Explained)**.)

For example, let's say you wanted to provide a Free Registration that lasted only 5 days. You would set those attributes to: `tp="5" tt="D"`. Or let's say you wanted the Free Membership to last only 2 months: `tp="2" tt="M"`.

Once you've modified the attributes, you're ready to go! When someone uses that Pro-Form to sign up for a free membership, their account will be limited to the trial period you defined.

Here's a full example Free Registration Pro-Form that provides a free 1-week membership:

```text
[s2Member-Pro-PayPal-Form register="1" level="0" ccaps="" desc="Signup now, it's Free!" tp="1" tt="W" captcha="clean" /]
```

## What happens when the Trial Period is over?

When the Trial Period on a Free Membership ends, what happens depends on your Automatic EOT Behavior configuration (see **Dashboard → s2Member → PayPal Options → Automatic EOT Behavior**).

By default, the Free Registration Pro-Form is configured to provide access to **Level 0 / Free Subscriber**. However, if you want Free Subscribers to be demoted to a lower level after their free membership expires (so that they can keep their account and so that you can, for example, up-sell them a paid membership), you _must_ use a level higher than **Level 0**, as there is no level lower than **Level 0** for s2Member to demote a Free Subscriber.

If you want to have free subscribers demoted (instead of having their account deleted; see the Automatic EOT Behavior configuration), then you need to change the `level="0"` attribute in the Pro-Form Shortcode to something higher, such as `level="1"`. 

Or, if you're using [Custom Capabilities](http://s2member.com/kb-article/video-custom-capabilities-for-wordpress/), you could set Free Subscribers to have a specific Custom Capability (e.g., `free`) and when their Trial Period is over, that Custom Capability will be stripped from their account (again, see the Automatic EOT Behavior configuration for more information).
