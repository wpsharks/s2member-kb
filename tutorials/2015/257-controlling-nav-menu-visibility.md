---
title: Controlling Nav Menu Visibility
categories: tutorials
tags: restriction-options
author: renzms
github-issue: https://github.com/websharks/s2member-kb/issues/257
---

In [Alternative View Protection](http://s2member.com/kb-article/will-s2member-protect-snippets-excerpts-feeds-searches-too/) we gave a basic overview of its features and capabilities regarding hiding or protecting content from guests to your site(or from varying levels of your subscribers). A common question among users is, *"How do I hide Navigation Menus or Menu items using s2Member?"* 

This is possible with [s2Member’s Alternative View Protection](http://s2member.com/kb-article/will-s2member-protect-snippets-excerpts-feeds-searches-too/) as it supports stopping the display of protected content from your navigation menu automatically.

In this article we will discuss how to use this feature to hide Nav Menu(s)/Nav Menu Item(s), how to extend the functionality using the `wp_nav_menu()` function, and how to do the opposite by showing all Nav Menu items that were previously restricted or protected.

## Using s2Member's Alternative View Protection ##

With s2Member's Alt. View Restrictions, you can tell s2Member to protect some (or all) of your Nav Menu(s) with "Alternative Views". 

See: **Dashboard → s2Member® → Restriction Options → Alternative View Protection**

![1](https://cloud.githubusercontent.com/assets/13220018/10281422/f854d8d6-6ba6-11e5-8f0f-7db7a9836fad.png)

## Enhance Menu Functionality by Tweaking Theme Files ##

If you need functionality past that, you will need to edit your theme’s `header.php` file directly, and change the `wp_nav_menu()` function call there. 

See: http://codex.wordpress.org/Function_Reference/wp_nav_menu

Here is an example for two separate Navigation Menus, in your theme using `is_user_logged_in()` and `wp_nav_menu()`

```php
<?php
if( is_user_logged_in() ) {
    wp_nav_menu( array( 'theme_location' => 'logged-users' ) );
} else {
    wp_nav_menu( array( 'theme_location' => 'not-logged-users' ) );
}
```

Instead of `theme_location`, you can use the menu name directly, check the documentation for `wp_nav_menu()`. Please review the codebase for the theme being used to check what the menu names are.

## Removing Nav Menu Visibility Restrictions ##

Now that you know how to hide menu items meant for your subscribers, there may be a time where you would like to show your protected Nav Menu items to everyone. You may want to, for example, show an item on a menu but only protect the content on the page itself to invite guests to subscribe. 

If you want everyone to see all menu items, you can simply uncheck the Nav Menus option in Alternative View Protection so that s2Member does not hide any menu items.

![2](https://cloud.githubusercontent.com/assets/13220018/10281361/8c7fe196-6ba6-11e5-8354-5a282cdfba4a.png)