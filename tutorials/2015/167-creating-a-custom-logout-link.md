---
title: Creating a Custom Logout Link
categories: tutorials
tags: login-registration,mu-plugins-hacks
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/167
toc-enable: false
---

You can use the [`wp_logout_url()`](https://codex.wordpress.org/Function_Reference/wp_logout_url) function to create a **logout** link of your own, and optionally have this link automatically redirect a user back to a custom URL after being logged out of the site.

## Quick Example in PHP Code

```html
<a href="<?php echo esc_attr(wp_logout_url('http://example.com/goodbye/')); ?>">logout</a>
```

- See also: [ezPHP for WordPress](http://s2member.com/kb-article/ezphp-for-wordpress/)
- See also: [`wp_logout_url()` in the WordPress Codex](https://codex.wordpress.org/Function_Reference/wp_logout_url)