---
title: Forms for Modifying User Accounts
categories: tutorials
tags: pro-forms, s2member, paypal, shortcodes, billing, billing-cancellation, billing-modification, billing-update
author: patdumond
github-issue: https://github.com/websharks/s2member-kb/issues/317
---

In this article, we will show you how to generate Pro-Forms for modifying user accounts: *Billing Modification*, *Billing Update*, and *Billing Cancellation* Pro-Forms. Pro-Forms are an *s2Member Pro Add-on* feature and are not available with the free *s2Member Framework*. These Pro-Forms are available for *PayPal Payments Pro*, *Stripe*, and *Authorize.net*.

The generation process is the same for each type of Pro-Form, but you need to generate each particular payment gateway’s Pro-Forms using the panels found on the s2Member Pro-Forms configuration for that gateway. For simplicity’s sake, we are using the PayPal Pro-Forms generators found here **WordPress Dashboard → s2Member (Pro) → PayPal Pro-Forms** in this article. Where differences between gateways exist, they are specified.

*This article is part of the [s2Member User's Guide](http://s2member.com/kb/kb-tag/s2member-users-guide/&sa=D&ust=1470254380914000&usg=AFQjCNHgE98nZQ3WeJbrmy8j0Xnjoka2Jg), a series of articles that cover the fundamentals of using s2Member.*

## Billing Modification Forms

See **WordPress Dashboard → s2Member (Pro) → PayPal Pro-Forms → Billing Modification Forms**

Billing Modification Forms can be used to allow your Members to *Upgrade* or *Downgrade* their Membership Level. Configure the updated Level, pricing, terms and other fields. Then, make the new Billing Modification Form available to Members logged in to their existing account with you. For example, you might want to insert a *Level #2 Upgrade* link into your *Login Welcome Page*. This link would upsell existing Level #1 Members to a more expensive plan that you offer.

### Account Modification Process

A Member clicks a link to a Post or Page containing a Billing Modification Form. The Member fills in their billing information. After a successful form submission and payment, s2Member updates the status of their account to the new Level, pricing, and terms you configured.

If the Member already has an existing **paid**  Subscription with you, that paid Subscription will be canceled automatically behind-the-scenes.  A new paid Subscription will be created to replace the old one. Again, the new paid Subscription is based on the Level, pricing, and terms that you specify in the Pro-Form Generator. If you need to give Members some sort of grace period when they upgrade to a more expensive plan, please feel free to handle this through the application of free days or discounted pricing.

**Integrating Conditionals**: Since each Billing Modification Form is configured for a particular s2Member Level, you may want to create multiple Billing Modification Forms, one for each combination you intend to make available. s2Member's [Simple Shortcode Conditionals](http://s2member.com/kb-article/s2if-simple-shortcode-conditionals/) can help you display the proper Form to each Member, based on the status of their existing account. 

**Independent Custom Capabilities**: If you just want to sell an existing Member **new** Custom Capabilities, without affecting their paid Subscription, please see the Pro-Form Generator** panel titled "Capability (Buy Now) Forms". Independent Capability Forms facilitate **Buy Now** functionality, specifically for Custom Capabilities, without affecting the Member's primary Subscription or Membership Level Access.

![billing-modification-pro-form](https://cloud.githubusercontent.com/assets/9320495/17380517/87788cc4-5995-11e6-821a-5cf73a28efac.jpg)

### Billing Modification Form Fields

Note: Some rows have multiple data-entry boxes. For convenience sake, the text that begins the row is shown below, followed by the data-entry requirements in bullets below.

- **Modification**: Select the appropriate modification (_Upgrade_ or _Downgrade_) from the drop-down box. 
- **I’ll offer the first**
     - Type in the number 
     - Select desired period from the drop-down list: *Days*, *Weeks*, *Months*, *Years*.
     - Type in the price 
- **Then, I want to charge**:
     - Type in the price     
     - Select the desired subscription type and payment frequency from the drop-down list. There are both recurring and one-time Subscriptions and Buy Now
Fixed-term Memberships. 
- **Description**: Modify the *Description* text to make your Membership terms as clear as possible for your Members.
- **Check out Page Style**:
     -  This is optional. You can configure [PayPal Custom Payments Page Styles](https://www.paypal.com/customize) from within your PayPal Merchant Account. If you create custom page styles, enter the name of the desired style here.
     - Select the currency you want from the drop-down box. 
- **Custom Capabilities**: This is optional. Type in a comma-delimited list of Custom Capabilities (CCAP) you would like included with this Membership. You’ll then use the same CCAP code to set appropriate content restrictions for your website.

Once you’ve filled in all the form fields, click the **Generate Form Code** button and then copy the generated shortcode to a Post or Page you created in WordPress.

## Billing Update Forms

See **WordPress Dashboard → s2Member (Pro) → PayPal Pro-Forms → Billing Update Forms**

*Billing Update* Forms are used to provide an easy way for your Members to update their billing information without modifying their existing paid Subscription in any way. If a Member’s credit card is expiring, for example, they can use a Billing Update Form to enter new payment information before their next Subscription Payment comes due.

![billing-update-pro-form](https://cloud.githubusercontent.com/assets/9320495/17380530/a06cbb38-5995-11e6-8875-1ebf63cd9ffd.jpg)

This is a very simple Pro-Form Generator with no options or fields to modify. Just copy the shortcode to a Post or Page you created in WordPress.

## Billing Cancellation Forms

See **WordPress Dashboard → s2Member (Pro) → PayPal Pro-Forms → Billing Cancellation Forms**

*PayPal*, *Stripe*, and *Authorize.net* all have *Recurring Billing* policies that require site owners to provide an easy way for Customers to cancel Recurring Subscriptions they have purchased. For further details and legalities, visit the website of the payment gateway you use.

![billing-cancellation-pro-form](https://cloud.githubusercontent.com/assets/9320495/17380665/3ef8f1ae-5996-11e6-98c8-ad602ab8715a.jpg)

This is a very simple Pro-Form Generator with no options or fields to modify. Just copy the shortcode to a Post or Page you created in WordPress.