---
title: Why Am I Getting a "Missing First Name" Error?
categories: Questions
tags: error-messages, pro-forms
author: patdumond
github-issue: https://github.com/websharks/s2member/issues/681
---

s2Member uses customizable templates to create Pro-Forms. When using a custom template for a Pro-Form, you need to be sure that the type of template you use matches the type of shortcode you use. Use paid templates for paid shortcodes and vice-versa.

Using a template file that was meant for a free registration form on a Pro-Form for paid subscriptions, or vice-versa, will lead to an unanticipated error in the program flow. One of the symptoms is a misleading error message: *Missing First Name*. You'll be scratching your head wondering how the first name could be missing when you just typed it in and hit "Submit". 

## Error: Missing First Name
To see this problem in action, create a test form using a paid registration shortcode with a free registration template.

The shortcode: 
![shortcode-free-registration-template-paid-shortcode-450px-width](https://cloud.githubusercontent.com/assets/9320495/14154757/3d6de3c0-f68c-11e5-8425-84cc4d7e39fb.png)

The form produced by this shortcode looks fine:

![unfilled-form-free-registration-template-paid-shortcode-450px-width](https://cloud.githubusercontent.com/assets/9320495/14154766/46e93be8-f68c-11e5-84f1-56c9cd83254c.png)

### The Infamous *Missing First Name* Error Message
Go to your form, enter some test data and hit the **Submit** button and you will see this error message:

![error-message-missing-first-name-450px-width](https://cloud.githubusercontent.com/assets/9320495/14154770/51f5b0c0-f68c-11e5-91a5-779722bb185d.png)

## Free Registration Form Template(s)
Pro-Form templates for free registration will have the following naming convention: `[payment-gateway]-registration-form.php` For example, `paypal-registration-form.php`. 

## Paid Registration Form Template(s)
Pro-Form templates for paid registration will have the following naming convention: `[payment-gateway]-checkout-form.php` or `[payment-gateway]-sp-checkout-form.php`. For example, `paypal-checkout-form.php`.


## Recap: Template Type Must Match Shortcode Type

Bottom line, when customizing s2Member you must always choose your tools carefully. Write down what it is you hope to accomplish: 

>Custom registration form for level 1 members paying by PayPal. Form is customized with a message saying "Joining us is a great decision!"

Make sure you choose the right template file for the task at hand. You'll avoid a lot of head-scratching!

## More on Pro-Forms
- [Can I customize Pro-Forms](http://s2member.com/kb-article/can-i-customize-pro-forms/)
- [How can I style Pro Forms w/ custom CSS?](http://s2member.com/kb-article/how-can-i-style-pro-forms-w-custom-css/)
- [s2Member Pro-Forms](http://s2member.com/kb-article/s2member-pro-forms/)
- [How can I change the order of Pro-Form fields?](http://s2member.com/kb-article/how-can-i-change-the-order-of-the-pro-form-fields/)
- [Why does "Card Start Date or Issue Number" always show on my Pro-Form?](http://s2member.com/kb-article/why-does-card-start-date-or-issue-number-always-show-on-my-pro-form/)
- [Dynamically Generating a Pro-Form Using MOP Vars](http://s2member.com/kb-article/dynamically-generating-a-pro-form-using-mop-vars/)
- [How do I get rid of the "Create Profile" section on my Pro Form?](http://s2member.com/kb-article/how-do-i-get-rid-of-the-create-profile-section-on-my-pro-form/)
- [Why am I seeing the Pro-Form Billing Address section when I'm only accepting PayPal?](http://s2member.com/kb-article/why-am-i-seeing-the-pro-form-billing-address-section-when-im-only-accepting-paypal/)
- [ My Pro Form looks nothing like examples I've seen, why?](http://s2member.com/kb-article/my-pro-form-looks-nothing-like-examples-ive-seen-why/)
