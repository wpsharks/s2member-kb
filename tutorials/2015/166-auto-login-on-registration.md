---
title: Auto-Login on Registration
categories: tutorials
tags: login-registration,mu-plugins-hacks
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/166
toc-enable: false

---

## Brief History Behind This

There have been numerous attempts at this throughout the s2Member forums and elsewhere. Some have worked, some have caused problems. For instance, there was a version of this hack circulating the s2Member forums which is now known to cause numerous problems, such as preventing s2Member’s post-processing routines from completing, or disabling the `success=""` shortcode attribute that’s possible with shortcodes produced by s2Member Pro. 

<i class="fa fa-exclamation-triangle"></i> _**WARNING:** Please ignore any other hacks you might have seen that do not reference this KB article specifically. Please use the MU plugin posted below for the best compatibility; i.e., to avoid accidentally using a hack from the past that did not work._

---

## MU Plugin for Auto-Login on Registration

I’m posting this here as a resource for those of you that would like to implement such a thing on your site. The purpose of this [MU plugin](http://codex.wordpress.org/Must_Use_Plugins) is to automatically log a new user (or even a paying customer) into their account immediately upon completing registration or checkout. In other words, we log them into the site automatically (i.e., they won’t need to enter their username/password when they register initially).

The following MU Plugin is compatible with both s2Member and with s2Member Pro. It works for _any_ user registration that occurs within WordPress (so long as s2Member is installed on the site). It also works with s2Member Pro Forms, where a new user/member/customer is creating a username on your site; either during a Free Registration, or during checkout for Membership Access.

In addition, this does _not_ cause a problem with the `success=""` shortcode attribute in s2Member Pro.

---

### Simple Installation Instructions

Please create this directory and file:
`/wp-content/mu-plugins/s2-auto-login.php`

```php
<?php
add_action('ws_plugin__s2member_during_configure_user_registration', 's2_auto_login_after_registration');
  function s2_auto_login_after_registration($vars = array())
	  {
		  if(is_admin()) return; // Not when an Admin is creating accounts.

		  wp_set_auth_cookie($vars['user_id'], FALSE, FALSE); // Log the user in.

		  if(did_action('login_form_register')) // For `/wp-login.php?action=register` compatibility.
			  c_ws_plugin__s2member_login_redirects::login_redirect($vars['login'], $vars['user']);

		  $GLOBALS['_s2_auto_login_after_registration_vars'] = $vars; // For Pro Form compatibility.
		  add_action('template_redirect', '_s2_auto_login_after_registration', 1);
	  }
  function _s2_auto_login_after_registration() // Pro Form redirection handler.
	  {
		  $vars = $GLOBALS['_s2_auto_login_after_registration_vars'];
		  c_ws_plugin__s2member_login_redirects::login_redirect($vars['login'], $vars['user']);
	  }
```

## Forcing A Specific `redirect_to` Upon Login

This line is added to the plugin, as seen in full below.

```php
$_REQUEST['redirect_to'] = $_GET['redirect_to'] = 'http://example.com/my-thank-you-page/';
```

```php
<?php
add_action('ws_plugin__s2member_during_configure_user_registration', 's2_auto_login_after_registration');
  function s2_auto_login_after_registration($vars = array())
	  {
		  if(is_admin()) return; // Not when an Admin is creating accounts.

		  wp_set_auth_cookie($vars['user_id'], FALSE, FALSE); // Log the user in.
		  
		  $_REQUEST['redirect_to'] = $_GET['redirect_to'] = 'http://example.com/my-thank-you-page/';

		  if(did_action('login_form_register')) // For `/wp-login.php?action=register` compatibility.
			  c_ws_plugin__s2member_login_redirects::login_redirect($vars['login'], $vars['user']);

		  $GLOBALS['_s2_auto_login_after_registration_vars'] = $vars; // For Pro Form compatibility.
		  add_action('template_redirect', '_s2_auto_login_after_registration', 1);
	  }
  function _s2_auto_login_after_registration() // Pro Form redirection handler.
	  {
		  $vars = $GLOBALS['_s2_auto_login_after_registration_vars'];
		  c_ws_plugin__s2member_login_redirects::login_redirect($vars['login'], $vars['user']);
	  }
```
