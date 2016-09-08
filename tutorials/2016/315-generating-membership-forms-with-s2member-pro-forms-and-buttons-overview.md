---
title: Generating Membership Forms with s2Member Pro-Forms and Buttons (Overview)
categories: tutorials
tags: pro-forms, paypal
author: patdumond
github-issue: https://github.com/websharks/s2member-kb/issues/315
---

In this article, you will be introduced to *s2Member’s* shortcode generators for **Pro-Forms** and **Buttons**. *s2Member* generates Pro-Form shortcodes according to the payment gateway you are using. **Pro-Forms are an s2Member Pro Addon feature and are not available with the free s2Member Framework**. Pro-Forms are available for *Free Registration*, *PayPal Payments Pro*, *Stripe*, and *Authorize.net*. Buttons for *ClickBank* are also a **s2Member Pro Addon** feature. Buttons for *PayPal* are available with the free *s2Member Framework* and, of course, work with the **s2Member Pro Addon** as well.

The generation process is the same for all Pro-Forms and Buttons (except for some variations in data-entry requirements), but you need to generate each particular payment gateway’s Pro-Forms and Buttons using the panels found on the *s2Member* Pro-Forms configuration for that gateway. For simplicity’s sake, we are (mostly) using the PayPal Pro-Form generators found here **WordPress Dashboard → s2Member (Pro) → PayPal Pro-Forms** in this article. Where differences between gateways exist, they are specified.

*This article is part of the [s2Member User's Guide](http://s2member.com/kb/kb-tag/s2member-users-guide/), a series of articles that cover the fundamentals of using s2Member.*

This topic has been broken up into several related articles:

- This overview article 
- [Forms for Level 0 (Free Registration) to Level x Access](https://github.com/websharks/s2member-kb/issues/316)
- [Forms for Modifying User Accounts](https://github.com/websharks/s2member-kb/issues/317) 
- [Forms for Buy Now Capabilities](https://github.com/websharks/s2member-kb/issues/318)
- [Forms and Links for Specific Post/Page Access](https://github.com/websharks/s2member-kb/issues/319) 
- [Generating Member Registration Access Links](https://github.com/websharks/s2member-kb/issues/320)
- [Configuring Custom Return URLs (Thank You Pages) Upon Success](https://github.com/websharks/s2member-kb/issues/321)

## PayPal Specifics: PayPal Pro Requirements

Pro-Forms require *PayPal Payments Pro*. However, there are some exceptions to that rule.

### Exceptions: PayPal Payments Pro is NOT Required if...

- You use *Free Registration* Pro-Forms. 
- You integrate with [Stripe](https://stripe.com&sa=D&ust=1470238793505000&usg=AFQjCNGZ359MUl4EsyW0gTaFm8P1KNdWWQ) instead. (*Stripe* has no monthly costs.) See this [KB article](https://s2member.com/kb-article/does-s2member-integrate-w-stripe-bitcoin/) for details.

### PayPal Payments Pro is *Absolutely* Required if...

- You want to accept on-site credit card payments via Pro-Forms and *PayPal*.
- You need *Cancellation*, *Billing Update*, or *Billing Modification* Pro-Forms. 
- You want to take full advantage of everything that Pro-Forms can do in conjunction with *PayPal* and to have all functions work as intended.

## Form Fields Common to Most Pro-Forms

Pro-Forms are generated using the configuration panels found on the Pro-Forms panels found under your particular payment gateway, for example, **WordPress Dashboard → s2Member (Pro) → PayPal Pro-Forms**. Fill in the fields on the generator form. Once you have filled in all the form fields, click the **Generate Form Code** button and then copy the generated shortcode to a **Post** or **Page** you created in *WordPress*.

![pro-form-generator-overview](https://cloud.githubusercontent.com/assets/9320495/17376886/8aed7a14-5985-11e6-9ca0-f81eaf5da034.jpg)

**Note**: Most rows have multiple data-entry boxes. For convenience-sake, the text that begins the row is shown below, followed by the data-entry requirements in bullets below.

- I'll offer the first
     - This field sets a *Trial Period* and is optional.     
     - Type in the number.     
     - Select desired period from the drop-down list: *Days*, *Weeks*, *Months*, *Years*.
     - Type in the price for your *Trial Period*.
- Then, I want to charge:
     - This field represents the amount you want to charge for your *Membership Plan*
     - Type in the price
     - Select the desired subscription type and payment frequency from the drop-down list. There are both recurring and one-time *Subscriptions*  **Buy Now** *Fixed-term Memberships*. 
- Description: Modify the *Description* text to make your *Membership* terms as clear as possible for your *Customers/Members*.
- Check out Page Style:
     - This field is optional. You can configure the *Checkout Page Style* from within your *PayPal Merchant Account*. If you create custom page styles, enter the name of the desired style here. 
     - Select the currency you want from the drop-down box. 
- Custom Capabilities: This is optional. Type in a comma-delimited list of *Custom Capabilities* (CCAP) you would like included with this Membership. You will then use the same CCAP code to set appropriate content restrictions for your website.