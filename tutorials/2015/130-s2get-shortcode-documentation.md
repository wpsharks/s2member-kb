---
title: '[s2Get /] Shortcode Documentation'
categories: tutorials
tags: api-scripting,shortcodes,s2get
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/130
---

s2Member comes with the `[s2Get /]` shortcode and also with an API Function `get_user_field()` for use in PHP template files. Both of these do much the same thing, so I’m going to discuss them both together.

The `[s2Get /]` shortcode is actually powered by `get_user_field()`. Both of these tools are used to retrieve details about a specific user. For instance, you might need to display a user’s first or last name, their email address, or another custom field that you’ve added with s2Member. Both `[s2Get /]` and `get_user_field()` are great for this! _The `[s2Get /]` shortcode can also be used to retrieve site-specific configuration details too; see example of `[s2Get constant="" /]` at the bottom of this article._

---

## A Few Examples Using `<?php get_user_field(); ?>`

```php
<?php
$user_login = get_user_field('user_login'); # Username for the current User.
$user_email = get_user_field('user_email'); # Email Address for the current User.
$first_name = get_user_field('first_name'); # First Name for the current User.
$last_name = get_user_field('last_name'); # Last Name for the current User.
$full_name = get_user_field('full_name'); # First and Last Name for the current User.
$display_name = get_user_field('display_name'); # Display Name for the current User.
?>
```

## Shortcode Equivalents; Using `[s2Get /]` in the WordPress Editor

```
[s2Get user_field="user_login" /] # Username for the current User.
[s2Get user_field="user_email" /] # Email Address for the current User.
[s2Get user_field="first_name" /] # First Name for the current User.
[s2Get user_field="last_name" /] # Last Name for the current User.
[s2Get user_field="full_name" /] # First and Last Name for the current User.
[s2Get user_field="display_name" /] # Display Name for the current User.
```

## More Examples with s2Member-Specific Data

```php
<?php
$s2member_custom = get_user_field('s2member_custom'); # Custom String value for the current User.
$s2member_subscr_id = get_user_field('s2member_subscr_id'); # Paid Subscr. ID for the current User.
$s2member_subscr_or_wp_id = get_user_field('s2member_subscr_or_wp_id'); # Paid Subscr. ID, else WordPress® User ID.
$s2member_subscr_gateway = get_user_field('s2member_subscr_gateway'); # Paid Subscr. Gateway Code for the current User.
$s2member_registration_ip = get_user_field('s2member_registration_ip'); # IP the current User had during registration.
$s2member_custom_fields = get_user_field('s2member_custom_fields'); # Associative array of all Custom Registration/Profile Fields.
$s2member_file_download_access_log = get_user_field('s2member_file_download_access_log'); # Associative array of all File Downloads by the current User, in the current Period (Period is based on a specific User'sallowed_days, configured in your Basic Download Restrictions, at the User's current Membership Level).
$s2member_file_download_access_arc = get_user_field('s2member_file_download_access_arc'); # Associative array of all File Downloads by the current User, in previous Periods (Periods are based on a specific User'sallowed_days, configured in your Basic Download Restrictions, at the User's Membership Levels in the past).
$s2member_auto_eot_time = get_user_field('s2member_auto_eot_time'); # Auto EOT-Time for the current User (when applicable).
$s2member_last_payment_time = get_user_field('s2member_last_payment_time'); # Timestamp. Last time an actual payment was received by s2Member.
$s2member_paid_registration_times = get_user_field('s2member_paid_registration_times'); # Timestamps. Associative array of all Paid Registration Times.
$s2member_access_role = get_user_field('s2member_access_role'); # A WordPress® Role ID (i.e. s2member_level[0-9]+, administrator, editor, author, contributor, subscriber).
$s2member_access_level = get_user_field('s2member_access_level'); # An s2Member Membership Access Level number.
$s2member_access_label = get_user_field('s2member_access_label'); # An s2Member Membership Access Label (i.e. Bronze, Gold, Silver, Platinum, or whatever is configured).
$s2member_access_ccaps = get_user_field('s2member_access_ccaps'); # An array of Custom Capabilities the current User has (i.e. music,videos).
$s2member_login_counter = get_user_field('s2member_login_counter'); # Number of times the User has logged into your site.
?>
```

## Practical Shortcode Equivalents Using `[s2Get /]`

```
[s2Get user_field="s2member_custom" /] # Custom String value for the current User.
[s2Get user_field="s2member_subscr_id" /] # Paid Subscr. ID for the current User.
[s2Get user_field="s2member_subscr_or_wp_id" /] # Paid Subscr. ID, else WordPress® User ID.
[s2Get user_field="s2member_subscr_gateway" /] # Paid Subscr. Gateway Code for the current User.
[s2Get user_field="s2member_registration_ip" /] # IP Address the current User had during registration.
[s2Get user_field="s2member_access_role" /] # A WordPress® Role ID (i.e. s2member_level[0-9]+, administrator, editor, author, contributor, subscriber).
[s2Get user_field="s2member_access_level" /] # An s2Member Membership Access Level number.
[s2Get user_field="s2member_access_label" /] # An s2Member Membership Access Label (i.e. Bronze, Gold, Silver, Platinum, or whatever is configured).
[s2Get user_field="s2member_login_counter" /] # Number of times the User has logged into your site.
```

## Pulling Data For Custom Registration/Profile Fields

```php
<?php
$my_field_data = get_user_field('my_field_id'); # The Unique Field ID you configured with s2Member.
?>
```

```
[s2Get user_field="my_field_id" /]
```

## Pulling Data for a Specific User by their User ID

```php
<?php
$user_login = get_user_field('user_login', 123); # Username for the User with ID #123.
$user_email = get_user_field('user_email', 123); # Email Address for the User with ID #123.
$first_name = get_user_field('first_name', 123); # First Name for the User with ID #123.
$last_name = get_user_field('last_name', 123); # Last Name for the User with ID #123.
$full_name = get_user_field('full_name', 123); # First and Last Name for the User with ID #123.
$display_name = get_user_field('display_name', 123); # Display Name for the User with ID #123.
?>
```

## Shortcode Equivalents Using `[s2Get /]`

```
[s2Get user_field="user_login" user_id="123" /] # Username for the User with ID #123.
[s2Get user_field="user_email" user_id="123" /] # Email Address for the User with ID #123.
[s2Get user_field="first_name" user_id="123" /] # First Name for the User with ID #123.
[s2Get user_field="last_name" user_id="123" /] # Last Name for the User with ID #123.
[s2Get user_field="full_name" user_id="123" /] # First and Last Name for the User with ID #123.
[s2Get user_field="display_name" user_id="123" /] # Display Name for the User with ID #123.
```

## Finding a User by their Username

```php
<?php
$user = new WP_User('johndoe22');
$user_id = $user->ID;
?>
```

## Finding a Username with a User ID

```php
<?php
$user = new WP_User(123);
$user_login = $user->user_login;
# Or you could just use this alternate method.
$user_login = get_user_field('user_login', 123);
?>
```

## Using `[s2Get constant="" /]` to Retrieve API Constants

```
[s2Get constant="S2MEMBER_LEVEL1_LABEL" /] # Membership Level 1 label.
[s2Get constant="S2MEMBER_LOGIN_PAGE_URL" /] # Login Welcome Page URL.
```

See also: **s2Member ⥱ API / Scripting ⥱ s2Member PHP/API Constants**
