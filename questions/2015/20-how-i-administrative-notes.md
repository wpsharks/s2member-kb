---
title: How can I search the Administrative Notes field?
categories: questions
tags: 
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/20
---

> It seems that many of the fields created by s2member are not searchable using the "search users" box at the top right. This is particularly troublesome when a user's subscription expires and their Paid Subscr. ID is deleted. It does get added automatically to the "administrative notes" box, but since I can't search this in wordpress, it makes it troublesome!

s2Member can be told to search the admin notes field. That functionality is disabled by default though, because on sites with a LOT of users it can be slow for WordPress to search all notes in addition to other fields that it searches already.

If you want to enable that functionality however, please create the following directory and file:

`/wp-content/mu-plugins/s2-hacks.php`

```
<?php
add_filter('ws_plugin__s2member_users_list_search_admin_notes', '__return_true');
```