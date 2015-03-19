---
title: Showing Membership Options Page Variables with PHP
categories: tutorials
tags: s2mop,mu-plugins-hacks,membership-options-page
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/4
---

For this trick you'll need to install something like the [ezPHP](http://wordpress.org/plugins/ezphp/) plugin to enable PHP code inside your Membership Options Page. Then, you can use the following PHP code on the Membership Options Page to show a message that states what type of Level, Custom Capability, or Specific Post/Page is required to access the content that caused the redirect to the Membership Options Page.

```php
<?php
if(!empty($_REQUEST["_s2member_vars"]))
    @list($restriction_type, $requirement_type, $requirement_type_value, $seeking_type, $seeking_type_value, $seeking_uri)
            = explode("..", stripslashes((string)$_REQUEST["_s2member_vars"]));

if (!empty($requirement_type)) {
	switch($requirement_type) {
		case 'level':
			$type = 'Level';
			break;

		case 'ccap':
			$type = 'Custom Capability';
			break;

		case 'sp':
			$type = 'Specific Post/Page';
			break;
	}
	echo 'This content requires ' . esc_html($type) . ': ' . esc_html($requirement_type_value);
}
?>
```

**See also:** [`[s2MOP /]` Shortcode Documentation](http://s2member.com/kb-article/s2mop-shortcode/) for an even easier way to do this!