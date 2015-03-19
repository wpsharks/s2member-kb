---
title: Restricting Content After the <!--more--> Tag
categories: tutorials
tags: restriction-options,mu-plugins-hacks,shortcodes,s2if
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/1
toc-enable: false
---

## Using [Simple Shortcode Conditionals](http://s2member.com/kb-article/s2if-simple-shortcode-conditionals/)

```wpsc
Intro content goes here--everyone will see this.

<!!--more-->

[s2If current_user_can(access_s2member_level1)]
    Some content for Members who are logged in with an s2Member Level >= 1.
    [else]
    	Some public content. You could put a notice here that says something like 
		"This content requires a membership. Please signup here (link)."
[/s2If]
```

See also: [s2Member Simple Shortcode Conditionals](http://s2member.com/kb-article/s2if-simple-shortcode-conditionals/)

---

## Taking it A Step Further

**Ninja Tip:** Working example of programmatic protection of content below the `<!--more-->` tag in WordPress.

Create this directory and file:
`/wp-content/mu-plugins/s2if-more-filter.php`

```php
<?php
function s2if_more_filter($content) {
    $members_only_message = "This content requires a membership. Please signup here (link).";
    $s2if_start = '[s2If !current_user_can(access_s2member_level1)]';
    $s2if_message = $members_only_message . ' [else]';
    $s2if_end = '[/s2If]';
    
    $pos1 = strpos($content, '<span id="more-');
    $pos2 = strpos($content, '</span>', $pos1);
    $before_more_tag = substr($content, 0, $pos2);
    $after_more_tag = substr($content, $pos2);
    
    $content = $before_more_tag . $s2if_start . $s2if_message . $after_more_tag . $s2if_end;
    return $content;
}
add_filter('the_content', 's2if_more_filter', 10, 1);
```
