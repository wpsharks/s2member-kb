---
title: Protecting Non-WordPress Content
categories: tutorials
tags: restriction-options,api-scripting,mu-plugins-hacks
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/141
---

If you want to use s2Member to protect content that is being loaded outside of WordPress you can do so by including `wp-load.php` from the WordPress core files.

```php
<?php
require_once 'wp-load.php';
if(current_user_can('access_s2member_level1'))
{
	// User is allowed to view, so display something here.
}
else exit('Permission denied!');
```

This solution uses PHP code and that means the external pages that use this code will need to be PHP files. Files that end in `.htm` or `.html` will not be able to use this code unless you've specifically configured your web server to parse those file types with PHP.

See: [How To Parse HTML Files As PHP](http://www.velvetblues.com/web-development-blog/how-to-parse-html-files-as-php/) for more information.
