---
title: How do I control access to the s2Member Plugin Options?
categories: questions
tags: mu-plugins-hacks
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/173
---

s2Member allows any user with the `create_users` WordPress Capability (which, by default, is only WordPress Administrators; see [WordPress Codex: Roles and Capabilities](https://codex.wordpress.org/Roles_and_Capabilities)) to access any of the s2Member plugin options. 

If you want more control over who can manage the s2Member Plugin Options, you can create an [MU-Plugin](http://codex.wordpress.org/Must_Use_Plugins) that uses a filter to prevent the s2Member menu options from being displayed.

```php
<?php
if(!current_user_can('SOMETHING'))
       add_filter('ws_plugin__s2member_during_add_admin_options_create_menu_items', '__return_false');
```

In this example, you could change `SOMETHING` to any WordPress Capability (see [WordPress Codex](http://codex.wordpress.org/Function_Reference/current_user_can)). You could also customize this code to use a different conditional that checks for something else that lets you control access to who can manage the s2Member Plugin Options.