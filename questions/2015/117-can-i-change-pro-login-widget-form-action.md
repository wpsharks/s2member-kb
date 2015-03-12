---
title: Can I change Pro Login Widget form action?
categories: questions
tags: pro-login-widget, mu-plugins-hacks
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/117
---

Yes. Please create this directory and file. Adjust as necessary.
`/wp-content/mu-plugins/s2-hacks.php`

```php
<?php
add_filter('site_url', function($url, $path, $scheme){
    if(trim($path, '/') === 'wp-login.php' && $scheme === 'login_post')
        return 'http://mysite.com/my-login-handler.php'; // Custom form action.
    return $url;
}, 10, 3);
```

See also: [Related WordPress source code](https://core.trac.wordpress.org/browser/tags/4.1.1/src/wp-includes/link-template.php#L2692)