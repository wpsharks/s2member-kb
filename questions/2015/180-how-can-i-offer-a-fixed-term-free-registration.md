---
title: How can I offer a fixed-term Free Registration?
categories: questions
tags: pro-forms
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/180
---

A fixed-term free registration allows you to offer a free registration that will expire after a certain amount of time. However, since there is no payment associated with a free registration, you must use the Trial Period functionality to create a fixed-term free registration.

## Creating a Fixed-Term Free Registration

_**Note:** In the examples below, we're using a Stripe Pro-Form. If you're using PayPal instead of Stripe as a payment gateway, please replace any references to Stripe with PayPal._

### Generating the Free Registration Pro-Form

To generate the Free Registration Pro-Form, visit **WordPress Dashboard → s2Member → Stripe Pro-Forms → Stripe / Free Registration Forms**. Here's an example of what the shortcode will look like (note that your `custom=""` attribute should contain your domain):

```text
[s2Member-Pro-Stripe-Form register="1" level="0" ccaps="" desc="Signup now, it's Free!" custom="example.com" tp="0" tt="D" captcha="clean" /]
```

### Setting a Trial Period (i.e. Fixed-Term)

Now if we want to turn this into a Fixed-Term Free Registration Pro-Form, we simply need to set a Trial Period. We do this by modifying the `tp=""` and `tt=""` shortcode attributes.

- `tp="0"` Trial Period. Only valid w/ Membership Level Access.
- `tt="D"` Trial Term. Only valid w/ Membership Level Access. Possible values: `D` = Days, `W` = Weeks, `M` = Months, `Y` = Years.

_For more details about Shortcode Attributes, please see **WordPress Dashboard → s2Member → Stripe Pro-Forms → Stripe Shortcode Attributes (Explained)**._

If we want to provide a Free Registration that expires after 3 Days, we would set `tp="3" tt="D"`.

If we want to provide a Free Registration that expires after 2 Weeks, we would set `tp="2" tt="W"`.

If we want to provide a Free Registration that expires after 1 Year, we would set `tp="1" tt="Y"`.

### Should you use Level 0 or Level 1?

Now that you've configured the Pro-Form, the last and perhaps most important step is to decide what Level you will use for your free registration. 

While it might make sense to use the default of **Level 0 / Subscriber**, we recommend that you try to avoid doing so when creating a subscription that should expire. The reason for this is that if you start at **Level 0 / Subscriber**, there is no lower level to which expired accounts can be demoted.

If you plan to use an Automatic EOT Behavior configuration that says to Delete the account when it expires (see **WordPress Dashboard → s2Member → Stripe Options → Automatic EOT Behavior**), then you can leave the default and have new subscribers use **Level 0 / Subscriber**. 

However, if you want expired Free Registration accounts to simply be demoted to a lower level that prevents them from having access to content that you've restricted to **Level 1** (more common), then you'll need to make sure that Free Registrations start at **Level 1**, so that when the free account expires they can be demoted by the Automatic EOT System to **Level 0 / Subscriber**. 

To have Free Registrations start at **Level 1**, simply modify the `level=""` shortcode attribute to read `level="1"`.

### What happens when the Trial Period is over?

What happens when the Trial Period for a Free Registration ends all depends on how you have things set up (see the section above, _Should you use Level 0 or Level 1?_).

When someone signs up using a Free Registration form that includes a Trial Period, an EOT date/time will be set immediately on the users account (see **WordPress Dashboard → Users → Edit User → Automatic EOT Time**). 

![2015-04-01_17-22-48](https://cloud.githubusercontent.com/assets/53005/6952893/bd77cf80-d893-11e4-88b8-18a62b487d57.png)

Once that date/time as passed, s2Member will demote or delete that account according to your Automatic EOT Behavior configuration (**WordPress Dashboard → s2Member → Stripe Options → Automatic EOT Behavior**).
