---
title: How can I hide specific fields on the [s2Member-Profile /] form?
categories: questions
tags: member-profile-modifications, mu-plugins-hacks
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/46
toc-enable: off
---

You can hide fields on the `[s2Member-Profile /]` form by adding a line to your theme's `functions.php` file, or to a [Must-Use Plugin](http://codex.wordpress.org/Must_Use_Plugins):

e.g., `/wp-content/mu-plugins/s2-hide-profile-fields.php`

```php
<?php
add_filter('ws_plugin__s2member_during_profile_during_fields_display_email', '__return_false');
```

You can change `ws_plugin__s2member_during_profile_during_fields_display_email` to any of the following tags to hide the corresponding field. You can also hide multiple fields by repeating the `add_filter()` line, passing in the tag for each field you want to hide:

- **Username:** `ws_plugin__s2member_during_profile_during_fields_display_username`
- **Email:** `ws_plugin__s2member_during_profile_during_fields_display_email`
- **First Name:** `ws_plugin__s2member_during_profile_during_fields_display_first_name`
- **Last Name:** `ws_plugin__s2member_during_profile_during_fields_display_last_name`
- **Display Name:** `ws_plugin__s2member_during_profile_during_fields_display_display_name`
- **Custom Fields:** `ws_plugin__s2member_during_profile_during_fields_display_custom_fields`
- **Password:** `ws_plugin__s2member_during_profile_during_fields_display_password`

### How Can I Hide Specific Custom Fields?

If you want to hide specific Custom Fields on the form (instead of hiding the entire Custom Field section), you can use the following code inside a [Must-Use Plugin](http://codex.wordpress.org/Must_Use_Plugins). 

Please create this file and directory: `wp-content/mu-plugins/s2member-hide-custom-fields-profile.php`

```php
<?php
add_filter('ws_plugin__s2member_during_profile_during_fields_during_custom_fields_display', '__s2member_hide_specific_custom_fields', 10, 2);

function __s2member_hide_specific_custom_fields($boolean, $vars) {
	$fields_to_hide = array('custom_field1', 'custom_field2');
	if(in_array($vars['field_var'], $fields_to_hide))
		return FALSE;
	else
		return TRUE;
}
```

You can then replace `custom_field1` and `custom_field2` in the code with the Unique ID for each Custom Field that you want to hide from the s2Member Profile output.
