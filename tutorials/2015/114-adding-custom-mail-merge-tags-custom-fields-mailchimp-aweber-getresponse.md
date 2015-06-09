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
    ));
    return $custom_fields;

    // Note that custom fields (aka: merge tags) will NOT work unless & until they are created by
    // a site owner working inside their MailChimp account. They must first add the custom fields
    // so they can be filled by the s2Member filter seen here.

    // See: <http://kb.mailchimp.com/merge-tags/using/getting-started-with-merge-tags>
}, 10, 2);
```

On the Mailchimp side, you should have the following MERGE fields configured as so.

![2015-06-09_03-17-00](https://cloud.githubusercontent.com/assets/1563559/8056574/099d679c-0e56-11e5-8c99-9d7f850b272f.png)

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
        'role'    => $args->role,
        'level'   => $args->level,
        'ccaps'   => $args->ccaps,
        'login'   => $args->login,
        'user_id' => $args->user_id,
    ));
    return $custom_fields;

    // Note that custom fields (as seen above) will NOT work unless & until they are created by
    // a site owner working inside their GetResponse account. They must first add the custom fields
    // so they can be filled by the s2Member filter seen here.

    // See: <http://support.getresponse.com/faq/what-is-a-custom-field>
}, 10, 2);
```
