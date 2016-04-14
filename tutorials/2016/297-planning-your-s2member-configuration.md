---
title: Planning Your s2Member Configuration
categories: tutorials
tags: s2member-users-guide, membership-levels, login-welcome-page, membership-options-page, restriction-options, pro-forms, login-registration
author: patdumond
github-issue: https://github.com/websharks/s2member-kb/issues/297
---

This KBA covers planning your _s2Member_ configuration. _S2Member_ is a complex, highly-configurable _WordPress_ plugin and it is imperative that you have a plan in place before you begin working with _s2Member_. You can use _s2Member_ to implement countless varieties of membership sites, but you have to know what you want to do so you can choose the right _s2Member_ settings and shortcodes to fulfill your vision.

*This article is part of the [s2Member User's Guide](http://s2member.com/kb/kb-tag/s2member-users-guide/), a series of articles that cover the fundamentals of using s2Member.*

## Have a Plan

If you are planning to install _s2Member_ then you probably have content on your website that you only want Members to see. A key part of your plan for setting up *s2Member* is to know **what content you want to protect and who you want to have access to this content.** This guide can’t help you there except to tell you to have a plan: don’t try to make it up as you go along.

Before you can envision how your new membership site will work, you need to understand how _s2Member_ directs Visitors when they come to your site. When a Visitor comes to your site and does not log in, they can only see the parts of your site that you have not restricted in any way with _s2Member_. With the default settings they will not even see restricted content in your menus or in archive, search, or RSS feeds.

So if you want Visitors to see any part of your restricted content, you’ll have to plan for that. You’ll also have to plan how people will learn about your restricted content: will you have a landing page or will you clear the settings that hide restricted content from menus and feeds? Or both?

The basic flow in _s2Member_ is simple: if a Visitor or Member attempts to access content that is restricted above their Membership Level, they are redirected to your _Membership Options Page_. The _Membership Options Page_ will normally contain links to pages where you have set up payment **Buttons** or **Pro-Forms** for your membership plan or plans. The next section describes how user registration flows in _s2Member_.

## How User Registration Flows in _s2Member_

### s2Member (Free Version) / PayPal Button

Website Visitors will go to your _Membership Options Page_ (which you will need to configure on the _s2Member General Options_ panel). (See: **WordPress Dashboard → s2Member® → General Options → Membership Options Page**). On your _Membership Options Page_ (which you create in **WordPress Dashboard → Pages → Add Page**), you'll insert the _PayPal Subscription Buttons_ that you generate using the _PayPal Buttons_ panel. (See: **WordPress Dashboard → s2Member® → PayPal Buttons**).

![paypal-button](https://cloud.githubusercontent.com/assets/9320495/14330430/8ad5f3be-fc0e-11e5-8916-f35deea72bc0.jpg)

A website visitor will click on a _PayPal Subscription Button_ on your _Membership Options Page_. They will be transferred over to _PayPal_ to agree to your Membership terms and pricing. You can customize the Checkout Page Style, Pricing, Payment Periods, and more; when you generate your _PayPal Buttons_ using the _PayPal Buttons_ panel. (See: **WordPress Dashboard → s2Member® → PayPal Buttons**).

![paypal-button-checkout](https://cloud.githubusercontent.com/assets/9320495/14330442/94542dfc-fc0e-11e5-85fe-6225653d0613.jpg)

Once your new _Member_ has completed the subscription payment process at _PayPal_, they'll be returned to your site. _s2Member_ will activate their account instantly, and they can then register: creating a **Username** and entering other profile details. (Note: they'll be allowed to register, even if you've set _Anyone Can Register_ to *Off* in your **WordPress General Settings**. _s2Member_ identifies the Member as having paid for membership access through _PayPal_).

![paypal-button-registration-page](https://cloud.githubusercontent.com/assets/9320495/14330453/9c95c020-fc0e-11e5-921a-08fa2992dddb.jpg)

_s2Member_ will also send the Member an email at their _PayPal_ email address with instructions on how to register their **Username**, just in case they missed the instructions after checkout. This occurs behind-the-scenes, where _PayPal_  and  _s2Member_  communicate with each other through the PayPal IPN service.

Once a Member has completed checkout, registered, and created a **Password**, they will be able to log in. The first Page they will see after logging in will be your _Login Welcome Page_ (which you will need to configure on the _s2Member General Options_ panel). (See: **WordPress Dashboard → s2Member® → General Options → Login Welcome Page**). Your _Login Welcome Page_ can contain whatever you like. You'll need to design this **Page** in **WordPress Dashboard → Pages → Add Page**.

### s2Member (Pro) / Pro-Forms

#### Payment Gateways

The free version of _s2Member_ supports _PayPal Website Payments Standard_ using _PayPal Buttons_. This payment gateway is enabled in both _s2Member_ and _s2Member Pro_.

_s2Member Pro_ supports several additional payment gateways. These gateways are:

- _Stripe + Bitcoin_ (_w/Pro-Forms_) - Supports _Buy Now_ & _Recurring Subscriptions_ 
- _Authorize.net_ (_w/Pro-Forms_) - Supports _Buy Now_ & _Recurring Subscriptions_
- _ClickBank_ (_w/Buttons_) - Supports _Buy Now_ & _Recurring Subscriptions_ 
- _PayPal Website Payments Pro_ (_w/Pro-Forms_) - Supports _Buy Now_ & _Recurring Subscriptions_

To enable any (or all) of these payment gateways, please see **WordPress Dashboard → s2Member® → Other Payment Gateways**.

**Note: For the remainder of this tutorial, we will assume you are using  _PayPal Website Payments Pro with Pro-Forms_.**.

#### Registration Process Using PayPal Pro-Forms

Website Visitors will go to your _Membership Options Page_ (which you will need to configure on the _s2Member General Options_ panel). (See: **WordPress Dashboard → s2Member® → General Options → Membership Options Page**). On your _Membership Options Page_ (which you create in **WordPress Dashboard → Pages → Add Page**), you'll insert links to Pages containing the _PayPal Pro Forms_ that you generate using the _PayPal Pro-Forms_ panel. (See: **WordPress Dashboard → s2Member® → PayPal Pro-Forms**). Each Page can contain only one **Pro-Form**, but you can wrap within a single **Pro-Form**. (See: [How do I display multiple checkout options?](http://s2member.com/kb-article/how-do-i-display-multiple-checkout-options) in the s2Member Knowledge Base.)

Your Visitor will click on a link to a membership offering on your _Membership Options Page_. The Page this URL links to should contain a _PayPal_ (or other payment gateway)  **Pro-Form**.

![proform-sales-form](https://cloud.githubusercontent.com/assets/9320495/14330463/a75f1f06-fc0e-11e5-94b2-f6ab54037a97.jpg)

The User will complete the profile information on the **Pro-Form**. This _must_ include the following:

- First Name
- Last Name 
- Email Address 
- Username (lower case alphanumeric only) 
- Billing Method

Additional fields you can use:

- Password and Password Confirm 
- ReCaptcha 
- [Custom Registration Fields](http://s2member.com/kb-article/can-i-create-custom-registration-andor-user-profile-fields-some-required-some-not)

![proform-registration-profile-fields](https://cloud.githubusercontent.com/assets/9320495/14330469/afa6fc74-fc0e-11e5-8b65-e05e8358221e.jpg)

They will then choose a payment method and complete the required payment information. If they select _PayPal_ as their Billing Method, they will be taken to _PayPal_ to complete the payment. If they use a credit card, the transaction will take place completely on your website.

### Login Welcome Page

The _Login Welcome Page_ (or LWP) is a _WordPress_ Page you create just as you would create any other **Page** in _WordPress_. The LWP is a _Page_, not a _Post_. It is the first Page Members will see after logging into your site.

You should create at least an empty LWP before you start configuring anything else in _s2Member_. We recommend you call it _My Login Welcome Page_, but you can call it _Fred_ if you want -- just remember what you titled it.

After you've created this LWP, you configure it on this panel: **WordPress Dashboard → s2Member® → General Options → Login Welcome Page**. Configuring the LWP and the rest of your **General Options** will be covered in detail in a later KBA in this series.

Once you have all of your **s2Member → General Options** configured, and once you have a basic understanding of how I works, go back and customize the title and content for the LWP. You'll want to be creative with your _Login Welcome Page_. However, you should configure your **WordPress Dashboard → s2Member → General Options** first, and test things out. That way you'll understand why the LWP is important and how it works.

For more details, see this _s2Member_ KB article, [Customizing Your Login Welcome Page](http://s2member.com/kb-article/customizing-your-login-welcome-page).

## Membership Options Page

The _Membership Options Page_ (or MOP) is a _WordPress_ Page you create just as you would create any other **Page** in WordPress. The MOP is a _Page_, not a _Post_.

Your _Membership Options Page_ should detail all of the features that come with Membership to your site, and provide a **Payment Button** (or **Pro-Form**; if you're running _s2Member Pro_) for each Level of access you plan to offer. The MOP is the **Page** that visitors will see should they attempt to access an area of your site restricted above their current level of access. The redirection is handled seamlessly by _s2Member_.

You should create at least an empty MOP before you start configuring anything else in _s2Member_ other than your basic _Login Welcome Page_. We recommend you call it _My Membership Options Page_, but you can call it _Barney_ if you want -- just remember what you titled it.

After you've created your MOP, you configure it on this panel: **WordPress Dashboard → s2Member® → General Options → Membership Options Page**.

**Tip**: If you allow _Open Registration_ (i.e., _Free Subscribers_), you might want to place a link on your _Membership Options Page_ that points directly to your _Free Registration Form_, instead of routing a Visitor through your _Payment Gateway_  first. It's a matter of preference, though.

**Always Public**: _This Page must be public at all times_. Access cannot be restricted to the _Membership Options Page_. Note: for technical reasons, your _Membership Options Page_ cannot be set to your _Front Page_ (i.e., your _Home Page_); or your _Posts Page_ (i.e., your main _Blog_ Page). Please create a separate (dedicated) **Page **in _WordPress_, and then designate it as your _Membership Options Page_.

![membership-options-page](https://cloud.githubusercontent.com/assets/9320495/14330479/bd87ef74-fc0e-11e5-997a-25e3da4ffbbb.jpg)