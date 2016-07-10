---
title: Can I add custom mail merge fields?
categories: tutorials
tags: api-list-servers
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/114
---

This requires an MU plugin with a custom filter.

## For MailChimp

Please create this directory and file:
`/wp-content/mu-plugins/s2-hacks.php`

Read over the instructions in the code below, and adjust as necessary.

```php
<?php
add_filter('ws_plugin__s2member_mailchimp_merge_array', function ($custom_fields, $vars)
{
    $args = &$vars['args']; // stdClass object.
    # print_r($args); // for a full list of all properties.

    $custom_fields = array_merge($custom_fields, array(
        'ROLE'    => $args->role,
        'LEVEL'   => $args->level,
        'CCAPS'   => $args->ccaps,
        'LOGIN'   => $args->login,
        'USER_ID' => $args->user_id,
        
        // A Custom Registration/Profile Field in s2Member can be obtained like this.
        // Note that `my_custom_field_id` should be replaced with the Unique ID that you configured for a field in s2Member.
        // 'MY_CUSTOM_FIELD' => get_user_field('my_custom_field_id', $args->user_id),
    ));
    return $custom_fields;

    // Note that custom fields (aka: merge tags) will NOT work unless & until they are created by
    // a site owner working inside their MailChimp account. They must first add the custom fields
    // so they can be filled by the s2Member filter seen here.

    // See: <http://kb.mailchimp.com/merge-tags/using/getting-started-with-merge-tags>
}, 10, 2);
```

_**Tip:** On the Mailchimp side, you should have the following MERGE fields configured as so._

![2015-06-09_03-21-23](https://cloud.githubusercontent.com/assets/1563559/8056637/a2a59748-0e56-11e5-805b-565266059aae.png)

## For AWeber

Please create this directory and file:
`/wp-content/mu-plugins/s2-hacks.php`

Read over the instructions in the code below, and adjust as necessary.

```php
<?php
add_filter('ws_plugin__s2member_aweber_custom_fields_array', function ($custom_fields, $vars)
{
    $args = &$vars['args']; // stdClass object.
    # print_r($args); // for a full list of all properties.

    $custom_fields = array_merge($custom_fields, array(
        'role'    => $args->role,
        'level'   => $args->level,
        'ccaps'   => $args->ccaps,
        'login'   => $args->login,
        'user_id' => $args->user_id,
        
        // A Custom Registration/Profile Field in s2Member can be obtained like this.
        // Note that `my_custom_field_id` should be replaced with the Unique ID that you configured for a field in s2Member.
        // 'my_custom_field' => get_user_field('my_custom_field_id', $args->user_id),
    ));
    return $custom_fields;

    // Note that custom fields (as seen above) will NOT work unless & until they are created by
    // a site owner working inside their AWeber account. They must first add the custom fields
    // so they can be filled by the s2Member filter seen here.

    // See: <https://www.aweber.com/users/settings/custom_fields>
}, 10, 2);
```

## For GetResponse

Please create this directory and file:
`/wp-content/mu-plugins/s2-hacks.php`

Read over the instructions in the code below, and adjust as necessary.

```php
<?php
add_filter('ws_plugin__s2member_getresponse_customs_array', function ($custom_fields, $vars)
{
    $args = &$vars['args']; // stdClass object.
    # print_r($args); // for a full list of all properties.

    $custom_fields = array_merge($custom_fields, array(
        array('name' => 'role', 'content' => (string) $args->role),
        array('name' => 'level', 'content' => (string) $args->level),
        array('name' => 'ccaps', 'content' => (string) $args->ccaps),
        array('name' => 'login', 'content' => (string) $args->login),
        array('name' => 'user_id', 'content' => (string) $args->user_id),
        
        // A Custom Registration/Profile Field in s2Member can be obtained like this.
        // Note that `my_custom_field_id` should be replaced with the Unique ID that you configured for a field in s2Member.
        // array('name' => 'my_custom_field', 'content' => get_user_field('my_custom_field_id', $args->user_id)),
    ));
    foreach ($custom_fields as $_key => $_field) {
        if (!isset($_field['content'][0])) unset($custom_fields[$_key]);
    } // GetResponse will choke if you send them empty field content. Remove empty values here.
    
    return $custom_fields;

    // Note that custom fields (as seen above) will NOT work unless & until they are created by
    // a site owner working inside their GetResponse account. They must first add the custom fields
    // so they can be filled by the s2Member filter seen here.

    // See: <http://support.getresponse.com/faq/what-is-a-custom-field>
}, 10, 2);
```
