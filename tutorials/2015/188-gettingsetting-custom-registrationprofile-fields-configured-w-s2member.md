---
title: Getting/Setting Custom Registration/Profile Fields Configured w/ s2Member
categories: tutorials
tags: mu-plugins-hacks,api-scripting,login-registration,registration-profile-fields
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/188
---

In this article I'll explain how to get/set Custom Registration/Profile fields through PHP code. Therefore, this tutorial will be targeted at WordPress theme/plugin developers that would like to integrate with s2Member.

_**Note:** With s2Member you can configure Custom Registration/Profile Fields in the Dashboard. See: **Dashboard → s2Member → General Options → Registration/Profile Fields & Options**_

_There is also an [`[s2Get /]` shortcode](http://s2member.com/kb-article/s2get-shortcode-documentation/) that can be used to obtain Custom Registration/Profile Field values and present them in a WordPress Post/Page._

---

## Getting Custom Registration/Profile Fields via PHP

```php
<?php
$user_id = get_current_user_id();
$custom_fields = get_user_option('s2member_custom_fields', $user_id);

print_r($custom_fields);
/*
Array
(
    [company] => Acme Incorporated
    [phone_number] => 1-555-555-5555
    [favorite_color] => beige
    [favorite_actor] => Keanu Reeves
)
*/
?>
```

---

## Setting Custom Registration/Profile Fields via PHP

```php
<?php
$user_id = get_current_user_id();
$custom_fields = get_user_option('s2member_custom_fields', $user_id);

$custom_fields['company'] = 'Biteme International';
$custom_fields['phone_number'] = '1-800-PHP-CODE';
update_user_option($user_id, 's2member_custom_fields', $custom_fields);
?>
```