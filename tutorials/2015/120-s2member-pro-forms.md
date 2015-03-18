---
title: s2Member Pro-Forms
categories: tutorials
tags: shortcodes,pro-forms
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/120
---

## A Quick Overview (Pro-Forms vs. Buttons)

Among other things, [s2Member Pro](http://s2member.com/pro/) comes with “Pro-Forms”. These are shortcodes that generate Registration/Checkout Forms—and other kinds of forms too.

In contrast, the free version of s2Member does _not_ come with Pro-Forms. In the free version of s2Member you work “Payment Buttons” only. Payment Buttons lead visitors away from your site to complete checkout at PayPal.com, whereas Pro-Forms keep visitors on your site at all times. Pro-Forms also make other payment options available to your customers. With Pro-Forms you have support for on-site credit card processing—and PayPal Express Checkout too.

_**Tip:** One of the most compelling reasons to upgrade to s2Member Pro is so that you can take advantage of s2Member's integration with Stripe™—with is accomplished using s2Member Pro-Forms. See: [s2Member Pro Features](http://s2member.com/features/) for more information about Stripe™ and Bitcoin._

---

## Why Should I Use “Pro-Forms” Instead Of “Buttons” In the Free Version?

**There are a lot of reasons; here are a few:**

- One-step registration/checkout results in less confusion for customers and fewer support headaches.
- They increase conversion rates, because the registration/checkout process is so much easier.
- Easier for site owners to work with also; i.e., a lot more flexibility and more configurable options.
- You gain the ability to configure tax rates of your own.
- You can create, configure, and promote Pro Coupon Codes.
- You can sell Gift/Redemption Codes using Pro-Forms.
- You can customize the appearance of Pro-Forms.
- You can accept any major credit card, even for recurring payments.
- You can integrate with services like Stripe™, PayPal Pro, and Authorize.Net.

Increased conversion rates is at the top of the list though. In the free version of s2Member all customers use PayPal, when in fact there are many people that prefer to pay with a credit card on your site instead of being sent to PayPal. With s2Member Pro-Forms you’re keeping customers on your site throughout the entire checkout process. You can control the surrounding elements on the page, the flow of events, and do a better job at building confidence in your products/services. Customers can pay with any major credit card, or if they _prefer_ to pay with PayPal they can do that too!

So, Pro-Forms improve sales volume and they offer a lot of added flexibility. s2Member Pro-Form Shortcodes make this very easy. With Stripe, PayPal Pro, and/or Authorize.Net Pro-Forms (remember, Pro-Forms come with [s2Member Pro](http://s2member.com/pro/)) you can support on-site credit card processing for Visa, MasterCard, American Express and Discover.

If you decide to go with PayPal Pro you can also accept Maestro, Solo (from UK customers) and PayPal Express Checkout; i.e., for customers around the world that _prefer_ to pay with PayPal. If you integrate with Stripe™ you can accept all major credit cards and now Bitcoin too! This is becoming very popular.

---

## How Do I Implement s2Member Pro-Forms?

If you’ve tried the free version of s2Member you’ve probably used the shortcode `[s2Member-PayPal-Button ... /]`. With [s2Member Pro](http://s2member.com/pro/) you may continue to use these Shortcodes, but you can also generate Pro-Form Shortcodes like `[s2Member-Pro-Stripe-Form ... /]`, `[s2Member-Pro-PayPal-Form ... /]` or `[s2Member-Pro-Authnet-Form ... /]`.

So Pro-Forms are integrated with easy-to-use [WordPress Shortcodes](http://codex.wordpress.org/Shortcode_API) (you copy/paste these into a Post or Page within WordPress). s2Member Pro comes with Pro-Form Generators in your Dashboard; making these shortcodes easy to setup and customize. Plus there are _many_ additional shortcode attributes to help you handle any special scenarios you might have. Even Simple Conditional Tag shortcodes are possible!

---

### Generating A Pro-Form Shortcode

![](https://www.filepicker.io/api/file/RFycel8uTrlK2aZPlj9J#.png)

---

### Pasting It Into A WordPress Post or Page

![](https://www.filepicker.io/api/file/onOmdLTHScKV2E4vHFrw#.png)

---

### Voila! You Now Have On-Site Credit Card Processing

![](https://www.filepicker.io/api/file/AsE8hvunTmmWFZFi2Uh4#.png)

---

## Is It Possible To Customize Pro-Form Templates? {#-customizing-pro-forms}

Absolutely! However, this is usually _not_ necessary, because Pro-Forms inherit styles introduced by whatever WordPress theme you've selected for your site. Pro-Forms come fully functional. They work as-is in most WordPress themes. If you need to tweak their appearance, most site owners accomplish this through custom CSS alone; i.e., by editing their own `style.css` file. So modification of Pro-Form Templates is not necessary in most cases.

That being said, if you’d like to create custom Pro-Form Templates, please check your `/wp-content/plugins/s2member-pro/includes/templates/forms/` directory. You can take s2Member’s default Pro-Form templates and place some (or all of them) into your active WordPress theme directory. By placing custom templates into your active WordPress theme directory you can be sure they won’t get overwritten in a future upgrade of s2Member.

Please be sure these files exist in your active WordPress theme directory, and please do _not_ change the file names (s2Member has already established file names for each of its Pro-Forms). If done properly, s2Member Pro will automatically find the custom templates in your active WordPress theme directory, and they’ll be used instead of s2Member’s default templates; allowing you to customize them all you like. You can use custom HTML, JS, CSS, and even PHP and WordPress functionality if you like.

### Here Is A Quick Example

- Copy this file: `/wp-content/plugins/s2member-pro/includes/templates/forms/paypal-checkout-form.php`
- Paste it here: `/wp-content/themes/ACTIVE-THEME-DIRECTORY/paypal-checkout-form.php` (and modify)

  Note: `ACTIVE-THEME-DIRECTORY` might be `twentytwelve` or your own custom theme directory.

### Getting More Specific About Custom Pro-Form Templates

s2Member Pro also makes it possible for you to select specific custom templates from your `/wp-content` directory. When you create an s2Member Pro-Form, you’ll be using an s2Member Shortcode, where you might have something like `[s2Member-Pro-PayPal-Form ... /]`. In this Shortcode, you could add the `template=""` attribute to call upon a specific custom template file that exists in your `/wp-content` directory. If you call upon custom template files this way (i.e., with the `template=""` shortcode attribute) you can name your custom template files anything you like. This can become a more flexible approach for some site owners.

**Example:** `[s2Member-Pro-PayPal-Form ... template="/my-pro-forms/checkout-form.php" /]`

For additional details on this, please see: **Dashboard → s2Member → [Payment Gateway] Pro-Forms → Shortcode Attributes (Explained)**, where the `template=""` shortcode attribute has been documented, along with all the other shortcode attributes s2Member Pro makes available for you.

---

### Custom Pro-Form Templates that Collect Custom Data

In most cases it is enough to simply create Custom Registration/Profile Fields with s2Member (see: **Dashboard → General Options → Registration/Profile Fields**). s2Member Custom Registration/Profile Fields are considered point-and-click functionality. Plus, they integrate seamlessly with all aspects of s2Member.

Having said that, some site owners have asked if it’s possible to get even more creative inside a Pro-Form Template. This section was added to provide you with some pointers. I will explain how to create your own form input fields in a Pro-Form, how to have s2Member validate those form fields for you, and how to store your custom data once a Pro-Form is submitted (because most site owners want their data associated with the customer).

<div class="li-margins"></div>

1. Follow the instructions in this article to create a [Custom Pro-Form Template](#-customizing-pro-forms).
2. Open your Custom Pro-Form Template and add a couple of form input fields. In this example, I’m going to collect two additional form fields that are custom for my site: `primary_physician` and `insurance_provider`.

  ```html
  <label for="primary_physician">Primary Physician: *</label>
  <input type="text" name="primary_physician" id="primary_physician" aria-required="true" />

  <label for="insurance_provider">Insurance Provider: *</label>
  <input type="text" name="insurance_provider" id="insurance_provider" aria-required="true" />

  <!-- The aria-required attribute (combined with your <label>) allows s2Member to validate these fields via JavaScript. -->
  ```

  Each field needs a label element for itself with a `for=""` attribute matching the field’s ID, and text inside the `<label></label>` tags to be displayed when/if an error occurs. Also, each field needs an `id=""` and `name=""` attribute, together with `aria-required="true"` if you want it validated via s2Member’s JavaScript library.
3. Please create this directory and file: `/wp-content/mu-plugins/s2-store-custom-pro-form-fields.php`

  _See also: [Hacking s2Member w/ Hooks and Filters for WordPress](https://github.com/websharks/s2member-kb/issues/150) for additional tips and tricks._

  ```php
  <?php
  add_action('ws_plugin__s2member_during_configure_user_registration', function ($vars = array())
  {
	  $user = $vars['user']; // A WP_user object instance.
	  $_p   = stripslashes_deep($_POST); // $_POST vars via form submission.

	  if(!empty($_p['primary_physician']) && is_string($_p['primary_physician']))
		  update_user_option($user->ID, 'primary_physician', esc_html($_p['primary_physician']));

	  if(!empty($_p['insurance_provider']) && is_string($_p['insurance_provider']))
		  update_user_option($user->ID, 'insurance_provider', esc_html($_p['insurance_provider']));
  });
  ```

  See also: [update_user_option()](http://codex.wordpress.org/Function_Reference/update_user_option) and [get_user_option()](http://codex.wordpress.org/Function_Reference/get_user_option)

---

## What Kinds Of Pro-Forms Can I Generate w/ s2Member Pro?

### Pro-Forms Come In Many Flavors

#### Stripe™ Pro-Forms

- **One-Step Free Registration Forms** provide access to any Membership Level or Custom Capability package. Free Registration can also be set to self-expire any trial access granted by these forms.
- **One-Step Registration/Checkout Forms** provide access to any Membership Level and/or Custom Capability package that you configure.
- **One-Step Billing Modification Forms** make it possible for Users/Members to upgrade or downgrade their account with you.
- **One-Step Custom Capability “Buy Now” Forms** sell Independent Custom Capabilities to new and/or existing customers wanting more.
- **One-Step Billing Information Update Forms** let your customers update their billing information to prevent things like credit card expirations.
- **One-Step Billing Cancellation Forms** give your customers the ability to cancel any future recurring charges.
- **One-Step Specific Post/Page “Buy Now” Forms** sell Specific Posts or Pages to new and/or existing customers. Membership _not_ required for these.

---

#### PayPal® Pro-Forms

- **One-Step Free Registration Forms** provide access to any Membership Level or Custom Capability package. Free Registration can also be set to self-expire any trial access granted by these forms.
- **One-Step Registration/Checkout Forms** provide access to any Membership Level and/or Custom Capability package that you configure.
- **One-Step Billing Modification Forms** make it possible for Users/Members to upgrade or downgrade their account with you.
- **One-Step Custom Capability “Buy Now” Forms** sell Independent Custom Capabilities to new and/or existing customers wanting more.
- **One-Step Billing Information Update Forms** let your customers update their billing information to prevent things like credit card expirations.
- **One-Step Billing Cancellation Forms** give your customers the ability to cancel any future recurring charges.
- **One-Step Specific Post/Page “Buy Now” Forms** sell Specific Posts or Pages to new and/or existing customers. Membership _not_ required for these.

---

#### Authorize.Net® Pro-Forms

- **One-Step Free Registration Forms** provide access to any Membership Level or Custom Capability package. Free Registration can also be set to self-expire any trial access granted by these forms.
- **One-Step Registration/Checkout Forms** provide access to any Membership Level and/or Custom Capability package that you configure.
- **One-Step Billing Modification Forms** make it possible for Users/Members to upgrade or downgrade their account with you.
- **One-Step Custom Capability “Buy Now” Forms** sell Independent Custom Capabilities to new and/or existing customers wanting more.
- **One-Step Billing Information Update Forms** let your customers update their billing information to prevent things like credit card expirations.
- **One-Step Billing Cancellation Forms** give your customers the ability to cancel any future recurring charges.
- **One-Step Specific Post/Page “Buy Now” Forms** sell Specific Posts or Pages to new and/or existing customers. Membership _not_ required for these.

---

## Which Payment Gateways Work w/ s2Member Pro-Forms?

s2Member Pro-Forms will work with Stripe™, PayPal Pro, or Authorize.Net. For more information, see: [s2Member Pro Features](http://s2member.com/features/)
