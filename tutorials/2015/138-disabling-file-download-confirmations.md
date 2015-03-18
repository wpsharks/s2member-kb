---
title: Disabling File Download Confirmations
categories: tutorials
tags: download-options,api-scripting,mu-plugins-hacks
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/138
toc-enable: false
---

See: **Dashboard → s2Member → Download Options → Basic Download Restrictions**

s2Member will automatically detect links anywhere in your content and/or anywhere in your theme files that contain `s2member_file_download` or `s2member-files`. Whenever a logged-in user clicks a link that contains `s2member_file_download` or `s2member-files` the system will politely ask the user to confirm the download using a very intuitive JavaScript confirmation prompt, which contains specific details about your configured download limitations. This way your users will be aware of how many files they’ve downloaded in the current period; and they’ll be able to make a conscious decision about whether to proceed with a specific download or not.

## Suppressing JavaScript Confirmations

If you want to suppress this JavaScript confirmation prompt, you can add this to the end of your links:

```text
&s2member_skip_confirmation
```

Shortcode alternative: `[s2File skip_confirmation="yes" /]`

## Suppressing JavaScript Confirmations Globally

You can set this global JavaScript variable to a value of `true` to disable ALL confirmation prompts.

```js
var ws_plugin__s2member_skip_all_file_confirmations = true;
```

So for instance, you might have an MU plugin that does this for you. Please create this directory and file:
`/wp-content/mu-plugins/s2-no-download-confirmations.php`

```php
<?php
add_action('wp_head', function()
{
  echo '<script type="text/javascript">';
  echo 'var ws_plugin__s2member_skip_all_file_confirmations = true;';
  echo '</script>';
});
```

You won’t need to add `&s2member_skip_confirmation` onto the end of your links now. You’ve disabled these globally.
