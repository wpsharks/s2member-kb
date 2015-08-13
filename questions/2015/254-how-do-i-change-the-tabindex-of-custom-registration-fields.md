---
title: How do I change the tabindex of Custom Registration Fields?
categories: questions
tags:  mu-plugins-hacks, registration-profile-fields, login-registration, pro-forms
author: kristineds
github-issue: https://github.com/websharks/s2member-kb/issues/254
toc-enable: off
---

s2Member automatically assigns a `tabindex` value to each Custom Field and the default setting usually works fine, however some themes and/or custom integrations may interfere with the default setting and require that you take control of the `tabindex` value s2Member assigns to each Custom Field.

You might find that the tab order on your registration form is "off" simply due to the way the WordPress Core handles the `tabindex` on page templates. The `tabindex` of custom registration fields may be customized in either of the two ways detailed in this article.

## Using the Other Attributes option 

Whenever you generate a Custom Field with s2Member, you could use the Other Attributes configuration option to change the `tabindex` of your custom registration fields. Visit **WordPress Dashboard → s2Member → General Options → Registration/Profile Fields and Options → Add New Field**

![other attributes configuration](https://cloud.githubusercontent.com/assets/7514953/9223083/a25ef0a8-4129-11e5-9aaa-3c4cf644d8c3.png)

---

## Hooking into the Default Starting Value

You can use a hook that alters the starting `tabindex` value for your custom fields. In other words, you can customize the starting value that s2Member uses when it generates the custom fields on your form. It's also worth noting that you can set `tabindex="-1"` to exclude a field from the tabbed interaction entirely; i.e., to skip over that field.

That can be altered with this [MU-Plugin](http://codex.wordpress.org/Must_Use_Plugins). The default value for the standard WordPress registration form is `20`. Each custom field is incremented by a value of `10` as it is displayed.

Create this directory and file: `wp-content/mu-plugins/s2-hacks.php`

```
<?php
add_action('ws_plugin__s2member_during_custom_registration_fields_before', function($vars){
  $vars['__refs']['tabindex'] = 20; // Default value is 20.
});
```

---
#### See also:
- [How do I add custom fields like ‘address’ or ‘phone number’ to my Pro-Form?](http://s2member.com/kb-article/how-do-i-add-custom-fields-like-address-or-phone-number-to-my-pro-form/)
- [Can I create custom registration and/or user profile fields? Some required, some not?](http://s2member.com/kb-article/can-i-create-custom-registration-andor-user-profile-fields-some-required-some-not/)
- [How do I show different Custom Registration Fields for each Signup Form?](http://s2member.com/kb-article/how-do-i-show-different-custom-registration-fields-for-each-signup-form/)
- [Why are my Custom Registration Fields not appearing on the Pro-Form?](http://s2member.com/kb-article/why-are-my-custom-registration-fields-not-appearing-on-the-pro-form/)
- [How do I add fields that do not show on the Registration Page?](http://s2member.com/kb-article/how-do-i-add-fields-that-do-not-show-on-the-registration-page/)
