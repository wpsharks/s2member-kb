---
title: Controlling Nav Menu Visibility
categories: tutorials
tags: restriction-options
author: renzms
github-issue: https://github.com/websharks/s2member-kb/issues/257
---
s2Member's [Alternative View Protection](http://s2member.com/kb-article/will-s2member-protect-snippets-excerpts-feeds-searches-too/) lets you tell s2Member to automatically hide menu items for protected content that is not available to the current user. However, depending on the complexity of your site or the WordPress theme you're using, it may be necessary to control the menu visibility by editing your theme files directly.

This article will review how to use the s2Member Alternative View Protection feature to hide Nav Menu(s)/Nav Menu Item(s), how to extend the functionality using the [`wp_nav_menu()`](http://codex.wordpress.org/Function_Reference/wp_nav_menu) function, and how to do the opposite and show all Nav Menu items that were previously restricted or protected.

## Using s2Member's Alternative View Protection ##

With s2Member's Alt. View Restrictions, you can tell s2Member to protect some (or all) of your Nav Menu(s) with "Alternative Views".

See: **Dashboard → s2Member® → Restriction Options → Alternative View Protection**

![s2Member Alternative View Protection](https://cloud.githubusercontent.com/assets/13220018/10281422/f854d8d6-6ba6-11e5-8f0f-7db7a9836fad.png)

This feature works with menus that are generated using the built-in WordPress Menu system (**Dashboard → Appearance → Menus**), as s2Member is able to filter out any items that the current user does not have access to.

## Advanced Menu Control via Tweaking Theme Files ##

If your theme does not take full advantage of the WordPress Menu system and instead has its own system for generating menus, or has hard-coded menus, you will need to edit your theme files directly and modify the code accordingly.

A common place for menus is the `header.php` template file and a common function unsed for calling menus is `wp_nav_menu()`.

See: [http://codex.wordpress.org/Function_Reference/wp_nav_menu](http://codex.wordpress.org/Function_Reference/wp_nav_menu)

By editing the theme template files directly, you can get as elaborate as necessary. Here is an example where two separate Navigation Menus (one called `logged-in-users` and another called `logged-out-users`) shows the appropriate menu based on whether or not the visitor is logged in or logged out:

```php
<?php
if( is_user_logged_in() ) {
    wp_nav_menu( array( 'theme_location' => 'logged-users' ) );
} else {
    wp_nav_menu( array( 'theme_location' => 'not-logged-users' ) );
}
```

Please review the codebase for your theme to see exactly what needs to be changed. If you're not comfortable with PHP or with modifying your theme files, we recommend posting your question on the [WordPress.org Support Forum](http://wordpress.org/support/) or hiring a web developer.

## Removing Nav Menu Visibility Restrictions ##

Now that you know how to hide menu items, there may be a time where you would like to show your protected Nav Menu items to everyone. You may want to, for example, show an item on a menu but only protect the content on the page itself to invite guests to subscribe. 

If you want everyone to see all menu items, you can simply uncheck the Nav Menus option in Alternative View Protection so that s2Member does not hide any menu items.

![2](https://cloud.githubusercontent.com/assets/13220018/10281361/8c7fe196-6ba6-11e5-8354-5a282cdfba4a.png)
