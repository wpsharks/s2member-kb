---
title: Where is the s2Member data stored in the WordPress database?
categories: questions
tags: mu-plugins-hacks, api-scripting
author: raamdev
github-issue:
github-issue: https://github.com/websharks/s2member-kb/issues/242
---

The s2Member plugin uses the WordPress database to store all data; there are no s2Member-specific database tables. For the highest level of compatibility and to keep your database as clean as possible, s2Member uses existing WordPress tables, e.g., `wp_options`, `wp_usermeta`, and `wp_postmeta`.

We do not recommend modifying information in the database directly, however the following information is intended for developers who may need to know how and where s2Member stores information for the purposes of extending s2Member in a custom integration.

_**Note:** We highly recommend [backing up your WordPress site and database](https://codex.wordpress.org/WordPress_Backups) before making any changes to your site._

---

## Plugin Options and Configuration

All s2Member plugin options (even Pro options) are stored in the `ws_plugin__s2member_options` meta key in the `wp_options` table. This is a serialized associative array.

```php
<?php
$options = get_options('ws_plugin__s2member_options');
print_r($options); // An associative array with MANY array keys.
```

For a list of all possible option keys in this array, please see:

- s2Member Framework default options array in [this file](https://github.com/websharks/s2member/blob/dev/src/includes/syscon.inc.php).
- s2Member Pro default options array in [this file](https://github.com/websharks/s2member-pro/blob/dev/s2member-pro/src/includes/syscon.inc.php)

---

## User Data and Custom Fields

All s2Member users are WordPress users with additional s2Member-specific data attached to them. All s2Member user-specific details are stored in the `wp_usermeta` table with keys that begin with: `s2member_`. For instance, `s2member_subscr_id` (Paid Subscr. ID), `s2member_subscr_gateway` (Paid Subscr. Gateway ID), and many others.

```php
<?php
$user_id = 123;
$subscr_id = get_user_option('s2member_subscr_id', $user_id);
$subscr_gateway = get_user_option('s2member_subscr_gateway', $user_id);
```

User-specific option keys include, but are not limited to:

- `s2member_custom`
- `s2member_subscr_id`
- `s2member_subscr_baid`
- `s2member_subscr_cid`
- `s2member_subscr_gateway`
- `s2member_custom_fields`
- `s2member_registration_ip`
- `s2member_ipn_signup_vars`
- `s2member_paid_registration_times`
- `s2member_access_cap_times`
- `s2member_coupon_codes`
- `s2member_sp_references`
- `s2member_last_status_scan`
- `s2member_first_payment_txn_id`
- `s2member_last_payment_time`
- `s2member_auto_eot_time`
- `s2member_last_auto_eot_time`
- `s2member_login_counter`
- `s2member_file_download_access_arc`
- `s2member_file_download_access_log`
- `s2member_notes`
- `s2m_gcs_[post ID]_[MD5 hash]_[MD5 hash]` (stores Gift/Redemption Codes purchased by a user)

---

## Post/Page Level Restrictions

The Membership Level Restrictions configured from the meta box on each Post/Page are stored in the global Restriction Options settings; i.e., as a part of `ws_plugin__s2member_options` in the `wp_options` table. You can actually go back to `s2Member → Restriction Options` and see them there also.

**Note:** the `ws_plugin__s2member_options` meta value is a serialized array of options and the Post/Page Restriction options are stored as a comma-delimited list of Post/Page IDs under the associative array keys: `levelN_posts` and `levelN_pages`; where `N` represents the Membership Levels they are configured for; i.e., requires at least a certain Membership Level.

```php
<?php
$options = get_option('ws_plugin__s2member_options');
echo $options['level1_posts']; // e.g., 1,2,3,4,5
echo $options['level1_pages']; // e.g., 6,7,8,9,10
```

---

## Post/Page Custom Capability Restrictions

These are stored in the `wp_postmeta` table for each post where you apply them. They are stored with a postmeta key of `s2member_ccaps_req` and are represented by a numerically indexed array of Custom Capability slugs that a site owner decided to require for a given Post/Page.

```php
<?php
$post_id = 123;
$ccaps = get_postmeta($post_id, 's2member_ccaps_req', true);
print_r($ccaps); // array('videos', 'pro', 'unlimited')
```
