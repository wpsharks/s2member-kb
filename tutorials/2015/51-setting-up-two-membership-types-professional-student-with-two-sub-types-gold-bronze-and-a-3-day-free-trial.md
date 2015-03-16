---
title: Setting up Two Membership Types (Professional / Student) with Two Sub-Types (Gold / Bronze) and a 3-Day Free Trial
categories: tutorials
tags: business-models, custom-capabilities, pro-forms, restriction-options
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/51
---

### Scenario

I need to setup a site with two types of memberships: Professional and Student, each with Gold and Bronze sub-types. I want to offer a free 3-day trial during which each account type will have full-access to all content normally granted to that membership option. After three days, they should be restricted from all content and will be required to upgrade to a paid membership to regain access.

#### Solution

This will require an advanced s2Member configuration that makes use of s2Member Pro Free Registration forms, s2Member Pro Billing Modification Forms, Custom Capabilities, the Login Welcome Form, and Simple/Shortcode Conditionals.

We'll use Level 1 access with two Custom Capabilities (`professional` and `student`) for the primary membership types and two more Custom Capabilities  (`gold` and `bronze`) for the secondary membership type. 

#### A Note on Cumulative Access

Note that s2Member Level access is cumulative, meaning that Level 2 users have access to everything offered to Level 1. For the purposes of this tutorial, we're going to assume that you want to separate this access--that content created for Professional members should not be accessed via Students, and content created for Students should not be accessed via Professionals. To make this happen, we use a single level for everyone (Level 1) and then use Custom Capabilities to control all access.

If you wanted to allow Professionals to access all content created for Students, you would simply not use the `professional` and `student` Custom Capabilities described below. Instead, you would use Level 1 for Students and Level 2 for Professionals. This would give members with Level 2 (i.e., Professionals) access to everything granted to Level 1 (i.e., Students).

### Step 1: Restricting the Content

All restricted content should require Level 1 access (regardless of membership type) and whatever combination of Custom Capabilities reflect the membership type.

For example, if you were creating a Page that contained content for Professional Bronze membership, you would add `professional,bronze` to the Custom Capabilities restriction.

![2015-01-20_18-44-08](https://cloud.githubusercontent.com/assets/53005/5828633/982143e8-a0d4-11e4-8df1-3baabb407c7f.png)

If you were creating content that should be accessible to anyone with a Professional membership (Bronze OR Gold), then you would simply add `professional` to the Custom Capabilities restriction. If you were creating content that should be accessible to anyone with a Bronze-type membership (Professional OR Student), then you would simply add `bronze` to the Custom Capability restriction.

### Step 2: Configuring the Sign-up Forms

We want to give our new signups a free 3-day trial. These signups will have access to all content granted by a particular membership option for 3 full days. After that period, their account will be automatically downgraded to a Level 0 (aka Free Subscriber) account. We will then show them an upgrade form whenever they login so that they can purchase paid access. 

#### Create Four Level 1 Free Registration Pro-Forms w/ 3-Day Trial Period

![2015-01-20_19-09-06](https://cloud.githubusercontent.com/assets/53005/5828886/f1dcabc2-a0d7-11e4-97b8-c9909044c4d6.png)

We will need Four separate shortcodes, each with the Custom Capabilities configured to reflect the various types of memberships:

- Professional Gold (Pro-Form Shortcode Attribute `ccaps="professional,gold"`)
- Professional Bronze (Pro-Form Shortcode Attribute `ccaps="professional,bronze"`)
- Student Gold (Pro-Form Shortcode Attribute `ccaps="student,gold"`)
- Student Bronze (Pro-Form Shortcode Attribute `ccaps="student,bronze"`)

You'll also need to make sure the form is configured to provide Level 1 access (`level="1"`) and a three-day Trial Period (`tp="3" tt="D"`).

We should end up with the following shortcodes:

```text
[s2Member-Pro-PayPal-Form register="1" level="1" ccaps="professional,gold" tp="3" tt="D" desc="Professional Gold" custom="example.com" captcha="clean" /]
[s2Member-Pro-PayPal-Form register="1" level="1" ccaps="professional,bronze" tp="3" tt="D" desc="Professional Bronze" custom="example.com" captcha="clean" /]
[s2Member-Pro-PayPal-Form register="1" level="1" ccaps="student,gold" tp="3" tt="D" desc="Student Gold" custom="example.com" captcha="clean" /]
[s2Member-Pro-PayPal-Form register="1" level="1" ccaps="student,bronze" tp="3" tt="D" desc="Student Bronze" custom="example.com" captcha="clean" /]
```

_Note that the `custom=""` attribute needs to match your website's domain._

You can then place these 4 Pro-Forms on separate signup pages for each membership type, or if you want to combine them into a single signup page, you can use Checkout Options (see  `Dashboard → s2Member (Pro) → PayPal Pro-Forms → Wrapping Multiple Shortcodes as "Checkout Options"`). (See also, [How do I display multiple checkout options?](https://github.com/websharks/s2member-kb/issues/39))

### Step 3: Add the Upgrade Form to the Login Welcome Page

After the three-day free trial period ends, the users account will automatically get demoted to Level 0 (Free Subscriber). Since they will no longer have Level 1 access, they will no longer be able to access any of the content that we restricted to Level 1. 

At this point, we want to start showing the user an Upgrade Form whenever they login so that they can choose to purchase a Paid Membership if they want to continue receiving access.

Whenever a user logs in, the first page they see is the Login Welcome Page (see `Dashboard → s2Member (Pro) → General Options → Login Welcome Page`), so we'll place the Upgrade Forms on that page.

#### Generate the Upgrade Forms

Visit `Dashboard → s2Member (Pro) → PayPal Pro-Forms → PayPal Pro Billing Modification Forms`. Here you will generate 4 separate upgrade forms, one for each membership type. When the user uses this form to purchase a membership, it will upgrade their existing account from Level 0 to Level 1, and add back in the appropriate Custom Capabilities.

![2015-01-20_19-27-34](https://cloud.githubusercontent.com/assets/53005/5829087/f078713c-a0da-11e4-9394-eb1168115bff.png)

#### Show the Upgrade Options on the Login Welcome Page

We only want these upgrade options to show for users with Level 0 access, i.e., users whose free 3-day trial has expired. We'll use a Simple/Shortcode Conditional (see `Dashboard → s2Member (Pro) → API / Scripting → Simple/Shortcode Condtionals`) to check the users level. 

We'll also wrap the Upgrade Form shortcodes as "Checkout Options" (see `Dashboard → s2Member (Pro) → PayPal Pro-Forms → Wrapping Multiple Shortcodes as "Checkout Options"`), so that we can cleanly present these to the user:

```text
[s2If current_user_is(s2member_level0)]
Your Free Trial has expired!
Upgrade today to continue receiving access.
     [s2Member-Pro-PayPal-Form]
          [s2Member-Pro-PayPal-Form modify="1" level="1" ccaps="professional,gold" desc="Professional Gold" ps="paypal" lc="" cc="USD" dg="0" ns="1" custom="example.com" ta="0" tp="0" tt="D" ra="0.01" rp="1" rt="M" rr="1" rrt="" rra="2" accept="paypal,visa,mastercard,amex,discover,maestro,solo" accept_via_paypal="paypal" coupon="" accept_coupons="0" default_country_code="" captcha="0" /]
          [s2Member-Pro-PayPal-Form modify="1" level="1" ccaps="professional,bronze" desc="Professional Bronze" ps="paypal" lc="" cc="USD" dg="0" ns="1" custom="example.com" ta="0" tp="0" tt="D" ra="0.01" rp="1" rt="M" rr="1" rrt="" rra="2" accept="paypal,visa,mastercard,amex,discover,maestro,solo" accept_via_paypal="paypal" coupon="" accept_coupons="0" default_country_code="" captcha="0" /]
          [s2Member-Pro-PayPal-Form modify="1" level="1" ccaps="student,gold" desc="Student Gold" ps="paypal" lc="" cc="USD" dg="0" ns="1" custom="example.com" ta="0" tp="0" tt="D" ra="0.01" rp="1" rt="M" rr="1" rrt="" rra="2" accept="paypal,visa,mastercard,amex,discover,maestro,solo" accept_via_paypal="paypal" coupon="" accept_coupons="0" default_country_code="" captcha="0" /]
          [s2Member-Pro-PayPal-Form modify="1" level="1" ccaps="student,bronze" desc="Student Bronze" ps="paypal" lc="" cc="USD" dg="0" ns="1" custom="example.com" ta="0" tp="0" tt="D" ra="0.01" rp="1" rt="M" rr="1" rrt="" rra="2" accept="paypal,visa,mastercard,amex,discover,maestro,solo" accept_via_paypal="paypal" coupon="" accept_coupons="0" default_country_code="" captcha="0" /]
     [/s2Member-Pro-PayPal-Form]
[/s2If]
```

![2015-01-20_19-42-39](https://cloud.githubusercontent.com/assets/53005/5829200/8f88f534-a0dc-11e4-867e-0ef40a7f315c.png)

### Summary

When a new user subscribes using one of the Free Signup Forms, they will be given Level 1 access with appropriate Custom Capabilities for their membership type. That will give them access to all content restricted to that membership type (e.g., Level 1 + `professional,gold` or Level 1 + `student,bronze`). 

After three days, their free trial will end and their account will be automatically demoted to Level 0 and their Custom Capabilities removed from their account. They will no longer be able to access any of the restricted content.

The next time the user logs into their account, the Login Welcome Page will check if their account is Level 0. If it is Level 0, the Login Welcome Page will display a message indicating their Free Trial has ended, along with a checkout form where they can choose a Membership Type and complete their payment.

Once their payment has been completed, their account will return to Level 1, along with whatever Custom Capabilities reflect the membership type they paid for (e.g., Level 1 + `professional,gold` or Level 1 + `student,bronze`).
