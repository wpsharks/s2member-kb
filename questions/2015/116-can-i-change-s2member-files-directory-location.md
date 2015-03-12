---
title: Can I change the s2member-files directory location?
categories: questions
tags: file-downloads, mu-plugins-hacks
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/116
---

> Can I change the s2member-files directory location?

Yes. By default, all protected files must live inside `/wp-content/plugins/s2member-files`. However, you can change this to a directory of your choosing using an `s2-hacks.php` file.

Please create this directory and file:
`/wp-content/mu-plugins/s2-hacks.php`

```php
<?php
add_filter('ws_plugin__s2member_files_dir', function(){
    return '/path/to/my/protected/files/dir'; // No trailing slash.
});
```