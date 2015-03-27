---
title: How can I control access to the s2Member Post Restrictions Meta Box?
categories: questions
tags: mu-plugins-hacks
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/172
---

s2Member allows any WordPress user with a Role that allows permission to edit Posts/Pages to also have access to the s2Member Post/Page Restrictions Meta Box on the Post/Page editing page:

![2015-03-26_21-13-46](https://cloud.githubusercontent.com/assets/53005/6860327/171109f8-d3fd-11e4-9947-63aec95749e7.png)

If you want to customize this behavior and limit access to the s2Member Post/Page Restriction Meta Box, there is an s2Member filter that will allow you to limit access given your specific rules. You could create an [MU-Plugin](http://codex.wordpress.org/Must_Use_Plugins) with the following code:

```php
<?php
add_filter('ws_plugin__s2member_add_meta_boxes_excluded_types', function($excluded_post_types)
{
    if(!current_user_can('SOMETHING')) # If they are not allowed, exclude all post types.
            $excluded_post_types = array_keys(get_post_types());
    
    return $excluded_post_types;
});
```

In this example, you could change `SOMETHING` to any WordPress Capability (see [WordPress Codex](http://codex.wordpress.org/Function_Reference/current_user_can)). You could also customize this code to use a different conditional that checks for something else that lets you control access to the s2Member Post/Page Restrictions Meta Box.