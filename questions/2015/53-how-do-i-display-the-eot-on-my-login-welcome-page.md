---
title: How do I display the EOT on my Login Welcome Page?
categories: questions
tags: login-welcome-page, mu-plugins-hacks
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/53
---

To display the EOT on the Login Welcome Page, you will first need to install a plugin that allows you to run PHP code inside your WordPress Pages. We recommend [ezPHP](http://wordpress.org/plugins/ezphp/).

_**Important Note:** When including PHP inside your WordPress Post/Page, it's very important that you only use the Text mode in the Post/Page Editor. If you use the Visual mode, the PHP code will likely become corrupt and will not work as expected._

![2015-01-21_17-23-29](https://cloud.githubusercontent.com/assets/53005/5846531/41a299ae-a192-11e4-97d1-5e7cf23cef41.png)

After you've installed a plugin such as [ezPHP](http://wordpress.org/plugins/ezphp/), you can add the following PHP code wherever you want to show the EOT for the user:

```php
<?php
if(($s2member_auto_eot_time = get_user_field('s2member_auto_eot_time'))) {
        // See <http://php.net/manual/en/function.date.php> for formatting options.
	echo 'Your membership expires on: '.esc_html(date('F j, Y', $s2member_auto_eot_time));
}
?>
```

You can change the "Your membership expires on: " portion to whatever is applicable for your scenario. You can also change the `F j, Y` portion of the code to display a different date format (`F j, Y` shows something like `January 21st, 2015`). See the [PHP `date()`](http://php.net/manual/en/function.date.php) formatting options.