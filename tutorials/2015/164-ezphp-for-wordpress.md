---
title: ezPHP for WordPress
categories: tutorials
tags: api-scripting,mu-plugins-hacks
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/164
---

## <i class="fa fa-cloud-download"></i> [Download ezPHP for WordPress](http://wordpress.org/extend/plugins/ezphp/)

A few people have asked me to write a _very_ simple version of the Exec-PHP plugin for WordPress. One without some of the extra code and no need for any admin control panel. So this PHP execution plugin ([ezPHP](http://wordpress.org/extend/plugins/ezphp/)) is extremely simple. One file, about 15-20 lines of code. Evaluates PHP tags in Posts (of any kind, including Pages) and also in text widgets.

---

## Introducing ezPHP for WordPress

ezPHP brings the power of `<?php ?>` tags into WordPress. Or, you can use `[php][/php]` shortcode tags (recommended for the WP Visual Editor; this is generally the best approach).

PHP tags can be extremely useful when there is logic that needs to be worked out before certain portions of your content are displayed under certain scenarios. It's also helpful when there are portions of your content that need to be more dynamic. Developers might use this to pull external files into WordPress (via `include` or `require`) making their work easier.

ezPHP can be [downloaded from the plugins repository at WordPress.org](http://wordpress.org/extend/plugins/ezphp/).

---

## Installation Instructions

![](http://cdn.websharks-inc.com/s2member/uploads/logo-329x171.png){.alignright}

-   Download [ezphp.zip](http://downloads.wordpress.org/plugin/ezphp.zip) and extract the `/ezphp` directory.
-   Upload the `/ezphp` folder to your `/wp-content/plugins/` directory.
-   Activate the plugin through the Plugins menu in WordPress.
-   Use PHP tags in your Posts/Pages/Widgets :-)

---

## Using ezPHP in WordPress

You can use regular `<?php ?>` tags. Or, you can use `[php][/php]` shortcode tags.

### Using `<?php ?>` Tags in a Post/Page/Widget

```html
<?php if(is_user_logged_in()): ?>
	Content for a user that is logged-in.
<?php else: // Otherwise show this.
	Content for everyone else.
<?php endif; ?>
```

### Using `[php][/php]` Shortcodes in a Post/Page/Widget

```text
[php]if(is_user_logged_in()):[/php]
	Content for a user that is logged-in.
[php]else: // Otherwise show this.[/php]
	Content for everyone else.
[php]endif;[/php]
```

---

### Quick Tip: Writing PHP Code Samples?

You can use `<!php !>` when writing code samples to avoid having certain PHP tags evaulated. When you write `<!php !>`, it is translated into `<?php ?>` in the final output; but never executed. Of course, it's _also_ possible to accomplish this with HTML entities; e.g. `&lt;?php ?&gt;`.

---

## ezPHP Configuration Options

ezPHP evaluates PHP tags in Posts (of any kind, including Pages) and also in text widgets. There is only _one_ configurable option. You can define this PHP constant inside your `/wp-config.php` file (optional):

```php
define('EZPHP_EXCLUDED_POST_TYPES', ''); // A comma-delimited list of Post Types to exclude.
```

For instance, if you don’t want PHP tags evaluated in Posts, only in Pages.

```php
define('EZPHP_EXCLUDED_POST_TYPES', 'post');
```
