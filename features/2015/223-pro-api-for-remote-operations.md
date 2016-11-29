---
title: Pro API for Remote Operations
categories: features
tags: api-scripting
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/223
---

With s2Member Pro installed, you have access to the s2Member Pro API For Remote Operations. This is made available for developers that wish to create User/Member accounts dynamically through custom scripts of their own. 

## Requires a Secret API Key

s2Member's Remote Operations API requires a secret API Key in order to POST authenticated requests to your installation of s2Member. You can have s2Member generate this key for you, or you can enter a key of your own.

See: **WP Dashboard → s2Member → API / Scripting → Pro API For Remote Operations**

<img src="https://cloud.githubusercontent.com/assets/53005/8049221/6e85cebe-0e2a-11e5-8f01-1363dd29d0ec.png" width="650" />

## Supported Remote Operations

The s2Member Pro API supports the following operations:

- `auth_check_user`
- `get_user`
- `create_user`
- `modify_user`
- `delete_user`

## Example PHP Scripts for Each Operation

### `auth_check_user` (authenticate existing Users/Members)

```php
<?php
$op["op"] = "auth_check_user"; // The Remote Operation.

$op["api_key"] = "296c096b6ac5c87d36b606842c76d6c2"; // Check your Dashboard for this value.
    // See: `s2Member ⥱ API / Scripting ⥱ Remote Operations API ⥱ API Key`

$op["data"] = array(
    "user_login" => "johndoe22", // Required. Username to query the database for.
    "user_pass" => "xxxxxxxxxxxxxxxx", // Required password for authentication.
    "user_ip" => "xxx.xxx.xxx.xxx" // Optional (but highly recommended) user IP address.
    // ↑ You should pass this to avoid invalid brute-force login protection attempts by s2Member.
    //    In short, s2Member should know what underlying IP address is attempting authentication.
);
$post_data = stream_context_create(array('http' => array('method' => 'POST', 'header' => 'Content-type: application/x-www-form-urlencoded', 'content' => 's2member_pro_remote_op='.urlencode(json_encode($op)))));
$result    = json_decode(trim(file_get_contents('https://jason.wpsharks.net/?s2member_pro_remote_op=1', false, $post_data)), true);

if ($result && empty($result['error']) && !empty($result['ID'])) {
    echo 'Successfully authenticated (i.e., username/password is valid) for user ID: '.$result['ID'];
} elseif (!empty($result['error'])) {
    echo 'API error reads: '.$result['error'];
}
```

### `get_user` (retrieve data about existing Users/Members)

```php
<?php
$op["op"] = "get_user"; // The Remote Operation.

$op["api_key"] = "296c096b6ac5c87d36b606842c76d6c2"; // Check your Dashboard for this value.
    // See: `s2Member ⥱ API / Scripting ⥱ Remote Operations API ⥱ API Key`

$op["data"] = array(
    "user_id" => "123", // A User ID to query the database for.
    "user_login" => "johndoe22", // OR, a Username to query the database for.
    "user_email" => "johndoe22@example.com" // OR, an email address to query the database for.
);
$post_data = stream_context_create(array('http' => array('method' => 'POST', 'header' => 'Content-type: application/x-www-form-urlencoded', 'content' => 's2member_pro_remote_op='.urlencode(json_encode($op)))));
$result    = json_decode(trim(file_get_contents('https://jason.wpsharks.net/?s2member_pro_remote_op=1', false, $post_data)), true);

if ($result && empty($result['error'])) {
    print_r($result);  // Print full array.
} elseif (!empty($result['error'])) {
    echo 'API error reads: '.$result['error'];
}
```

### `create_user` (or update existing Users/Members)

```php
<?php
$op["op"] = "create_user"; // The Remote Operation.

$op["api_key"] = "296c096b6ac5c87d36b606842c76d6c2"; // Check your Dashboard for this value.
    // See: `s2Member ⥱ API / Scripting ⥱ Remote Operations API ⥱ API Key`

$op["data"] = array(
    "user_login" => "johndoe22", // Required. A unique Username. Lowercase alphanumerics/underscores.
    "user_email" => "johndoe22@example.com", // Required. A valid/unique Email Address for the new User.

    // These additional details are 100% completely optional.

    "modify_if_login_exists" => "1", // Optional. Update/modify if ``user_login`` value already exists in the database?
        // A non-zero value tells s2Member to update/modify an existing account with the details you provide, if this Username already exists.

    "user_pass" => "456DkaIjsd!", // Optional. Plain text Password. If empty, this will be auto-generated.

    "first_name" => "John", // Optional. First Name for the new User.
    "last_name" => "Doe", // Optional. Last Name for the new User.

    "s2member_level" => "2", // Optional. Defaults to Level #0 (a Free Subscriber).
    "s2member_ccaps" => "music,videos", // Optional. Comma-delimited list of Custom Capabilities.

    "s2member_registration_ip" => "123.456.789.100", // Optional. User's IP Address. If empty, s2Member will fill this upon first login.

    "s2member_subscr_gateway" => "paypal", // Optional. User's Paid Subscr. Gateway Code. One of: (paypal|alipay|authnet|ccbill|clickbank|google).
    "s2member_subscr_id" => "I-DJASODJF8933J", // Optional. User's Paid Subscr. ID. For PayPal®, use their Subscription ID, or Recurring Profile ID.

    "s2member_custom" => "s2member.dev", // Optional. If provided, should always start with your installation domain name (i.e., $_SERVER["HTTP_HOST"]).

    "s2member_auto_eot_time" => "2030-12-25", // Optional. Can be any value that PHP's ``strtotime()`` function will understand (i.e., YYYY-MM-DD).

    "custom_fields" => array("my_field_id" => "Some value."), // Optional. An array of Custom Registration/Profile Field ID's, with associative values.

    "s2member_notes" => "Administrative notation. Created this User via API call.", // Optional. Administrative notations.

    "opt_in" => "1", // Optional. A non-zero value tells s2Member to attempt to process any List Servers you've configured in the Dashboard area.
        // This may result in your mailing list provider sending the User/Member a subscription confirmation email (i.e., ... please confirm your subscription).

    "notification" => "1", // Optional. A non-zero value tells s2Member to email the new User/Member their Username/Password.
        // The "notification" parameter also tells s2Member to notify the site Administrator about this new account.
);
$post_data = stream_context_create(array('http' => array('method' => 'POST', 'header' => 'Content-type: application/x-www-form-urlencoded', 'content' => 's2member_pro_remote_op='.urlencode(json_encode($op)))));
$result    = json_decode(trim(file_get_contents('https://jason.wpsharks.net/?s2member_pro_remote_op=1', false, $post_data)), true);

if ($result && empty($result['error']) && !empty($result['ID'])) {
    echo 'Success. New user created with ID: '.$result['ID'];
} elseif (!empty($result['error'])) {
    echo 'API error reads: '.$result['error'];
}
```

### `modify_user` (updates existing Users/Members)

```php
<?php
$op["op"] = "modify_user"; // The Remote Operation.

$op["api_key"] = "296c096b6ac5c87d36b606842c76d6c2"; // Check your Dashboard for this value.
    // See: `s2Member ⥱ API / Scripting ⥱ Remote Operations API ⥱ API Key`

$op["data"] = array(
    // You must supply one of these values.
    "user_id" => "123", // A WordPress® User ID.
    "user_login" => "johndoe22", // A Username instead of the WordPress® User ID.

    // These additional details are 100% completely optional.

    "user_email" => "johndoe22@example.com", // Optional—if updating. A valid/unique Email Address for this User.
    "user_pass" => "456DkaIjsd!", // Optional. Plain text Password—if updating.

    "first_name" => "John", // Optional—if updating. First Name for this User.
    "last_name" => "Doe", // Optional—if updating. Last Name for this User.
    "display_name" => "Doe", // Optional—if updating. Display Name for this User.

    "s2member_level" => "2", // Optional —if updating.
    "s2member_ccaps" => "music,videos", // Optional—if updating.
    // Any Custom Capabilities you supply here will be added to any that a User already has.
    // If you want to remove all Custom Capabilities, start your list with "-all". Ex: "-all,music,videos" (removes all, then adds: music,videos).
    // If you simply want to remove all Custom Capabilities, set this to "-all" (removes all Custom Capabilities, adds none).

    "s2member_originating_blog" => "123", // Optional—if updating a User/Member that exists in a Multisite Network installation.
        // This should ONLY be supplied if you are running a Multisite Network, and you want to change the Originating Blog ID.

    "s2member_registration_ip" => "123.456.789.100", // Optional—if updating. User's original IP Address during registration.

    "s2member_subscr_gateway" => "paypal", // Optional—if updating. User's Paid Subscr. Gateway Code. One of: (paypal|alipay|authnet|ccbill|clickbank|google).
    "s2member_subscr_id" => "I-DJASODJF8933J", // Optional—if updating. User's Paid Subscr. ID. For PayPal®, use their Subscription ID, or Recurring Profile ID.

    "s2member_custom" => "s2member.dev", // Optional—if updating. This should always start with your installation domain (i.e., $_SERVER["HTTP_HOST"]).

    "s2member_auto_eot_time" => "2030-12-25", // Optional—if updating. Can be any value that PHP's ``strtotime()`` function will understand (i.e., YYYY-MM-DD).

    "custom_fields" => array("my_field_id" => "Some value."), // Optional—if updating. An array of Custom Registration/Profile Field ID's, with associative values.

    "s2member_notes" => "Modified this User via API call.", // Optional—if updating. A new administrative notation added to the User's account.

    "reset_ip_restrictions" => "1", // Deletes/resets any existing IP Restrictions that s2Member has logged on this account.
        // If the current User/Member is banned, because they've used too many IPs in the last X days (as configured in the Dashboard area);
        // this will remove that ban—because it's deleting and resetting all IP Restrictions (i.e., IP log files) for this User's acccount in WordPress®.

    "reset_file_download_access_log" => "1", // Deletes/resets any existing logs associated with past File Download Access.
        // You would ONLY pass this in if you wanted to give this User/Member a fresh start with their access to File Downloads.
        // This resets the User/Member stats collected and compared against your Basic File Download Restrictions.
        // See also: `Dashboard ⥱ s2Member® ⥱ Download Options ⥱ Basic Download Restrictions`

    // WARNING: Setting either of these two additional values (depending on your underlying mailing list solution);
    // may result in the User/Member being sent an email subscription confirmation—possibly sent by your mailing list provider.

    "auto_opt_out_transition" => "1", // Optional—if updating Membership Level. A non-zero value tells s2Member to attempt to process any List Server Transitions you've configured in the Dashboard area.
        // If List Server Transitions are enabled, this will attempt to remove the User from a previous mailing (from a previous Membership Level) and add them to a new mailing list (for the new Level).
        // If you set a non-zero value here, but the "s2member_level" does not change during modification—nothing happens.

    "opt_in" => "1", // Optional. A non-zero value tells s2Member to attempt to process List Servers that you've configured in the Dashboard area.
        // This forces an attempt to process List Servers at the current Membership Level. So this works even if Transitions are disabled in the Dashboard area.
        // However, please note... this does NOT transition a User/Member from one list to another. It simply adds them to the mailing list they should be on.
        // If they are already subscribed to your mailing list, setting this to a non-zero value does nothing—harmless.
);
$post_data = stream_context_create(array('http' => array('method' => 'POST', 'header' => 'Content-type: application/x-www-form-urlencoded', 'content' => 's2member_pro_remote_op='.urlencode(json_encode($op)))));
$result    = json_decode(trim(file_get_contents('https://jason.wpsharks.net/?s2member_pro_remote_op=1', false, $post_data)), true);

if ($result && empty($result['error']) && !empty($result['ID'])) {
    echo 'Success. Modified user ID: '.$result['ID'];
} elseif (!empty($result['error'])) {
    echo 'API error reads: '.$result['error'];
}
```

### `delete_user` (deletes existing Users/Members)

```php
<?php
$op["op"] = "delete_user"; // The Remote Operation you're calling upon.

$op["api_key"] = "296c096b6ac5c87d36b606842c76d6c2"; // Check your Dashboard for this value.
    // See: `s2Member ⥱ API / Scripting ⥱ Remote Operations API ⥱ API Key`

$op["data"] = array(
    // You must supply one of these values.
    "user_id" => "123", // A WordPress® User ID.
    "user_login" => "johndoe22", // A Username instead of the WordPress® User ID.
);
$post_data = stream_context_create(array('http' => array('method' => 'POST', 'header' => 'Content-type: application/x-www-form-urlencoded', 'content' => 's2member_pro_remote_op='.urlencode(json_encode($op)))));
$result    = json_decode(trim(file_get_contents('https://jason.wpsharks.net/?s2member_pro_remote_op=1', false, $post_data)), true);

if ($result && empty($result['error']) && !empty($result['ID'])) {
    echo 'Success. Deleted user ID: '.$result['ID'];
} elseif (!empty($result['error'])) {
    echo 'API error reads: '.$result['error'];
}
```
