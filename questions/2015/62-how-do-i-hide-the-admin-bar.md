---
title: How do I hide the Admin Bar?
categories: questions
tags: mu-plugins-hacks, admin-bar
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/62
---

> When my users login they see the WordPress Admin Bar across the top of the page, the one that says, "Howdy, [username]". How would I remove that so they don't see the Admin Bar?

**Answer:** You can add the following snippet of PHP code to your theme's `functions.php` file. This code will check if the current user has access to manage options on your site (i.e., someone like the Administrator) and if they don't have those permissions, it will disable the Admin Bar:

```php
<?php
if (!current_user_can('manage_options'))
    show_admin_bar(FALSE);
```

If you simply want to disable the Admin Bar for all users, you can add the following PHP code to your theme's `functions.php` file:

```php
<?php
add_filter('show_admin_bar', '__return_false');
```

For more information, see the WordPress Codex page for [`show_admin_bar()`](http://codex.wordpress.org/Function_Reference/show_admin_bar).