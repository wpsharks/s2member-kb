---
title: User Custom Fields via PHP Code
categories: tutorials
tags: registration-profile-fields,api-scripting,mu-plugins-hacks
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/169
---

Whenever you create a Custom Registration/Profile Field with s2Member, you are required to assign it a Unique ID. s2Member takes the Unique ID that you assign—replacing anything that is not `a-z0-9` with an `_` underscore. This sanitized Unique ID is used to reference the custom field in code.

See: **Dashboard → s2Member ⥱ General Options ⥱ Registration/Profile Fields & Options**

![](https://cloud.githubusercontent.com/assets/53005/25411283/e59368f4-29e9-11e7-951b-944b42dd2b4c.png)

---

## Using the `get_user_field()` Function

s2Member adds a new function to WordPress called `get_user_field()`. You can find the function source [here](https://github.com/websharks/s2member/blob/170221/src/includes/classes/utils-users.inc.php#L300-L319).

This function accepts two arguments:

- **`$unique_id`** Required. The Unique ID that you want the value for.
- **`$user_id`** Optional. Defaults to the current user ID; i.e., the ID of the user currently logged into the site.

### Example PHP Code

```php
<?php
$company = get_user_field('company');
// ↑ Pulls the value for a custom field with ID `company`, for the current user.

$user_id = 123; // A specific user ID.
$company = get_user_field('company', $user_id);
// ↑ Pulls the value for a custom field with ID `company`, for user ID 123.
```

### Return Values for `get_user_field()`

- **(mixed)** The value of the requested field, or false if the field does not exist.

---

## Using the `get_user_option()` Function in WordPress

This function is part of the WordPress core. See: [Function Reference/get user option « WordPress Codex](http://codex.wordpress.org/Function_Reference/get_user_option)

This function accepts two arguments:

- **`$option_name`** Required. Any WordPress user option name, or the Unique ID for a custom field generated with s2Member (optionally prefixed with `s2_`). The optional `s2_` prefix is suggested in order to avoid ambiguity.
- **`$user_id`** Optional. Defaults to the current user ID; i.e., the ID of the user currently logged into the site.

### Example PHP Code

```php
<?php
$company = get_user_option('company'); // An s2Member custom field with ID `company`.
$company = get_user_option('s2_company'); // This works for s2Member custom fields too; prefix is optional.
// ↑ Pulls the value for a custom field with ID `company`, for the current user.

$user_id = 123; // A specific user ID.
$company = get_user_option('company', $user_id); // An s2Member custom field with ID `company`.
$company = get_user_option('s2_company', $user_id); // This works for s2Member custom fields too; prefix is optional.
// ↑ Pulls the value for a custom field with ID `company`, for user ID 123.
```

---

**See also:** [`[s2Get /]` Shortcode Documentation](http://s2member.com/kb-article/s2get-shortcode-documentation/)
