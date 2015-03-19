---
title: How can I modify the output of certain types of Custom Registration/Profile fields?
categories: questions
tags: mu-plugins-hacks,registration-profile-fields
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/28
---

> How can I modify the output of certain types of Custom Registration/Profile fields?

To start with, s2Member makes _many_ configurable options available in the UI, even down to specific HTML attributes, styles, or classes that you'd like to apply. So the best place to start working on something like this is in the s2Member UI.

See: **Dashboard ⥱ s2Member ⥱ General Options ⥱ Registration/Profile Fields**

Create or edit a field there, and you will see a lightbox window that opens with several additional config. options on a per-field basis.

---

If that's not enough, you can also dig into the PHP code and you'll find this filter exposed by s2Member: `ws_plugin__s2member_custom_field_gen`

Quick example to alter field type: `checkboxes`

Create this directory and file:
`/wp-content/mu-plugins/s2-hacks.php`

```php
<?php
add_filter('ws_plugin__s2member_custom_field_gen', function ($markup, $vars)
{
   extract($vars); // Extract variables passed by s2Member.

   if($field['type'] === 'checkboxes' && !empty($field['options'])
   {
      // Perform string manipulations on $markup.
      // Or, use the options and other $vars to generate your own $markup.
   }
  return $markup;
}, 10, 2);
```

Referencing [ws_plugin__s2member_custom_field_gen](https://github.com/websharks/s2member/blob/000000-dev/s2member/includes/classes/custom-reg-fields.inc.php#L269) in the s2Member source code.