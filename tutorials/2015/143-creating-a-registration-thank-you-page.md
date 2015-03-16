---
title: Creating a Registration Thank-You Page
categories: tutorials
tags: login-registration
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/143
---

## Two Ways Users Can Register

A Registration Thank-You Page can be used to provide additional instructions to a new member—after they’ve completed registration. This Registration Thank-You Page can be shown to members after they complete registration and before they log in.

In this article I will discuss two ways that a user can register. The method you use (i.e., for registration) will determine how you create a custom Registration Thank-You Page page and implement it.

<div class="li-margins"></div>

- The first registration method uses the built-in WordPress registration page (i.e., `/wp-login.php?action=register`). This is commonly used by site owners running the free version of s2Member; i.e., site owners that currently do not have the power of s2Member Pro-Forms.

- The second registration method uses s2Member Pro-Forms. Pro-Forms are only available with [s2Member Pro](http://www.s2member.com/pro/). In the discussion below regarding Pro-Forms, we use the `success=""` shortcode attribute, which also happens to work with PayPal Buttons whenever you have s2Member Pro.

---

## Built-In WordPress Registration Form (`wp-login.php?action=register`)

Create the following directory and file:
`/wp-content/mu-plugins/reg-ty-page.php`

```php
<?php
add_action('ws_plugin__s2member_after_configure_user_registration', function($vars = array()) {
  if (!is_admin() && !empty($vars['processed']) && $vars['processed'] === 'yes')
  {
	 $_POST['redirect_to'] = $_REQUEST['redirect_to'] =
	 
	 	// Custom Thank-You Page URL.
	 	"http://example.com/thank-you/". // « change this value.
		
		// These will all be optional. Here as an example only.
		'?email='.urlencode($vars['email']). // Tack on the email address if you like.
		'&fname='.urlencode($vars['fname']). // Tack on the first name if you like.
		'&lname='.urlencode($vars['lname']). // Tack on the last name if you like.
		'&my_custom_field='.urlencode($vars['fields']['my_custom_field']). // A custom field maybe.
		'&username='.urlencode($vars['login']); // The user's login; i.e., their username.
  }
});
```

↑ Update `$_POST['redirect_to']` to point to a full URL that leads to your custom Thank You Page.

### Optional: Display Registration Information on Thank-You Page

For the next step, you’ll need to first install and activate the [ezPHP Plugin](http://wordpress.org/extend/plugins/ezphp/). This plugin allows you to run PHP code inside your WordPress posts and pages. Once the ezPHP plugin has been installed and activated you can edit your Thank-You Page and insert the following snippets of PHP wherever you want to show the email address, first name, last name, or username:

```php
Email: <?php echo esc_html($_REQUEST['email']); ?>
First Name: <?php echo esc_html($_REQUEST['fname']); ?>
Last Name: <?php echo esc_html($_REQUEST['lname']); ?>
Custom Reg Field: <?php echo esc_html($_REQUEST['my_custom_field']); ?>
Username: <?php echo esc_html($_REQUEST['username']); ?>
```

---

## s2Member Pro-Form Integration (Much Easier)

![](http://cdn.websharks-inc.com/s2member/uploads/logo-s2-icon-128.png){.alignright}

s2Member Pro makes redirecting to a custom Thank-You Page easy by providing the `success=""` shortcode attribute, which you can add to the shortcodes that power s2Member Pro-Forms (works w/ Stripe, PayPal Pro, Authorize.Net). The `success=""` attribute also happens to work with PayPal Buttons whenever you have s2Member Pro.

In addition, s2Member Pro provides Replacement Codes that you can use within your Thank-You Page URL (works with Pro-Forms only). These allow you to pass information from the registration form to your custom URL so that it's easier to customize your Thank-You Page with details relevant to the current user.

To redirect a Pro-Form (or PayPal Button) to a custom Thank-You Page after registration, simply add a `success=""` attribute with the full URL to your Thank-You Page. Here are some examples. You can learn more about this in your Dashboard. See: **Dashboard → [Your Payment Gateway] Forms → Custom Return URLs on Success**.

```text
[s2Member-Pro-Stripe-Form ... success="http://example.com/thank-you/" ... /]
[s2Member-Pro-PayPal-Form ... success="http://example.com/thank-you/" ... /]
[s2Member-Pro-Authnet-Form ... success="http://example.com/thank-you/" ... /]
[s2Member-PayPal-Button ... success="http://example.com/thank-you/" ... /]
```

_*Note:* The above shortcodes are abbreviated for clarity. The `...` would normally include other shortcode attributes that make up the full shortcode that is needed. Just add the `success=""` attribute somewhere in the list of attributes. Normally at the very end, but before the closing `/]` tag._

### Optional: Display Registration Information on Thank-You Page

Requires an s2Member Pro-Form. If you want to display information on the Thank-You Page, you’ll need to pass that information to the Thank-You Page in the URL that you added to the `success=""` attribute. For example, to pass the registration email address and the first name, you’ll need to modify the `success=""` attribute as follows:

```text
success="http://example.com/thank-you/?email=%%user_email%%&fname=%%user_first_name%%"
```

Then for the next step you’ll need to first install and activate the [ezPHP Plugin](http://wordpress.org/extend/plugins/ezphp/). This plugin allows you to run PHP code inside your WordPress posts and pages. Once the ezPHP plugin has been installed and activated, you can edit your Thank-You Page and insert the following snippets of PHP wherever you want to show the email address and first name:

```php
Email: <?php echo esc_html($_REQUEST['email']); ?>
First Name: <?php echo esc_html($_REQUEST['fname']); ?>
```

Please see: **Dashboard → s2Member → PayPal Pro Forms → Custom Return URLs Upon Success** for a complete list of replacement codes that can be used in the `success=""` attribute. For more details on shortcode attributes, please see: **Dashboard → s2Member → PayPal Pro Forms → Shortcode Attributes (Explained)**
