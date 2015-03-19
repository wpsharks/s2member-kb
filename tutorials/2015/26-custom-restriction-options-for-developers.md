---
title: Custom Restriction Options (for Developers)
categories: tutorials, videos
tags: restriction-options,mu-plugins-hacks
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/26
toc-enable: false
---

https://www.youtube.com/watch?v=gpkM147RAgY

---

The s2Member UI in the WordPress Dashboard provides site owners with many ways to protect their content within WordPress. That's a great place to start with s2Member, and it's certainly very easy to work with from a client perspective. However, there is more than one way to protect your content with s2Member, and from a developer's perspective, protecting content using PHP conditionals could be simpler, and provide you with the added flexibility that is needed to meet client demands.

In this video tutorial, lead developer Jason Caldwell provides an overview of the Restriction Options that are available in s2Member. He also dives into the code and offers examples of how to protect content (in code) that might make your life a little easier on some projects that involve s2Member.

---

## Links/Concepts Referenced in the Video

- [WordPress Conditional Tags](http://codex.wordpress.org/Conditional_Tags)
- [WordPress MU Plugins](http://codex.wordpress.org/Must_Use_Plugins)
- [s2Member Simple Shortcode Conditionals](http://s2member.com/kb-article/s2if-simple-shortcode-conditionals/)
- [s2Member Roles/Capabilities](http://s2member.com/kb-article/s2member-rolescapabilities/)
- [s2Member Roles/Capabilities via PHP](http://s2member.com/kb-article/rolescapabilities-via-php/)
- Code sample used in the video w/ a little cleanup:
  `/wp-content/mu-plugins/s2-hacks.php`
	```php
	<?php
	add_action('ws_plugin__s2member_after_security_gate', 'my_custom_security_gate');

	function my_custom_security_gate()
	{
		if(is_admin())
			return;

		global $post;

		if(is_singular() && $post->post_type === 'post')
		{
			if(!current_user_can('access_s2member_level1'))
			{
				wp_redirect('/membership-options/');
				exit;
			}
		}
		if(is_singular() && has_term('members-only', 'post_tag'))
		{
			if(!current_user_can('access_s2member_ccap_members'))
			{
				wp_redirect('/membership-options/');
				exit;
			}
		}
		if(is_singular() && has_term('videos', 'post_tag'))
		{
			if(!current_user_can('access_s2member_ccap_videos'))
			{
				wp_redirect('/membership-options-videos/');
				exit;
			}
		}
	}
	```
