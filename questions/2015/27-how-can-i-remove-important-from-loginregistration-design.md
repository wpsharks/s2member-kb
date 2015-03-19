---
title: How can I remove `!important` from Login/Registration Design?
categories: questions
tags: login-registration,mu-plugins-hacks
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/27
---

> How can I remove `!important` from Login/Registration Design?

s2Member applies styles to the Login/Registration page with an `!important` CSS declaration to prevent compatibility issues with the WordPress core. However, in some cases (e.g., if you are trying to override specific settings with your own custom CSS; beyond that provided by s2Member's UI) you may want to remove the `!important` keyword from s2Member's ruleset.

Please create this directory and file:
`/wp-content/mu-plugins/s2-lhs-not-important.php`

```php
<?php
add_filter('ws_plugin__s2member_login_header_styles_important', '__return_null');
```

This will remove all of the `!important` declarations automatically.