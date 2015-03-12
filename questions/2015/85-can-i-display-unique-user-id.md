---
title: Can I display a unique User ID?
categories: questions
tags: api-scripting
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/85
---

> Is there a unique ID for each user? If so, how can I display this on-site?

Yes. Using an s2Member shortcode you can do this inside a Post/Page.

```
[s2Get user_field="ID" /]
```

See also: <http://codex.wordpress.org/Function_Reference/get_current_user_id>
If you install a plugin like [ezPHP](https://wordpress.org/plugins/ezphp/), you can use PHP code to get the user's ID.

```php
<?php echo esc_html(get_current_user_id()); ?>
```