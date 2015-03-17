---
title: Levels w/o Incremental Access
categories: tutorials
tags: roles-capabilities,shortcodes,restriction-options,api-scripting,mu-plugins-hacks
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/134
---

Sometimes you might find it helpful to break away from Membership Levels altogether. If you want more flexibility we suggest that you go with [Custom Capabilities](https://www.youtube.com/watch?v=_F91xzrmq-Q) (highly recommended).

However, you can also get creative with Membership Levels when it comes to the way that you protect portions of your content. This is accomplished by using the `current_user_is()` function—with Simple Shortcode Conditionals or in PHP Conditional Tags.

## Understanding Roles/Capabilities in s2Member

As a quick primer, please see: [s2Member Roles/Capabilities](https://github.com/websharks/s2member-kb/issues/122)

## Difference Between `current_user_can()` and `current_user_is()`

The `current_user_can()` function can test for a specific Role, but in practice it is almost always used to test for a specific Capability. So while you can do things like `if(current_user_can('s2member_level1'))`, that is a bit confusing to read in code. This is why s2Member adds a new function to the WordPress arsenal. If you want to check for a specific Role you can use `if(current_user_is('s2member_level1'))`. In this way you are checking if the current user is actually at this specific Role—not if they have access to a specific Capability; which might be true given the incremental nature of s2Member Roles (i.e., Membership Levels). Whenever you use `current_user_is()` you're getting more specific—which can help in many cases.

## Simple Shortcode Conditionals that Check for A Specific Role

In a WordPress Post or Page use Simple Shortcode Conditionals that check the user's Membership Level. This will determine if you will show or hide the content. See also: [Simple Shortcode Conditionals](https://github.com/websharks/s2member-kb/issues/119)

```text
[s2If current_user_is(s2member_level2)]
	Some premium content for Level 2 Members.
[/s2If]

[s2If current_user_is(s2member_level1)]
	Some premium content for Level 1 Members.
[/s2If]

[s2If current_user_is(s2member_level0)]
	Some content for Free Subscribers.
[/s2If]
```

## PHP Conditional Tags that Check for A Specific Role

In a theme or plugin file you can use PHP Conditional Tags. These Conditional Tags check the user's Membership Level. This will determine if you will show or hide the content. If you install the [ezPHP](https://wordpress.org/plugins/ezphp/) plugin for WordPress you can use PHP tags in a Post or Page also.

```html
<?php if(current_user_is('s2member_level2')): ?>
	Some premium content for Level 2 Members.
<?php elseif(current_user_is('s2member_level1')): ?>
	Some premium content for Level 1 Members.
<?php elseif(current_user_is('subscriber')): ?>
	Some content for Free Subscribers.
<?php else: // Anyone else. ?>
	Some content for anyone else.
<?php endif; ?>
```

## Custom Capabilities (advanced, but ideal when you want to be specific)

Custom Capabilities allow for even more flexibility, particularly when your goal is to break away from the incremental nature of Membership Levels and gain more flexibility in the way you protect portions of your site.

https://www.youtube.com/watch?v=_F91xzrmq-Q

### Example Shortcode Conditional to Check for a Custom Capability

```text
[s2If current_user_can(access_s2member_ccap_music)]
	Some content for users who can access CCAP: music
	[else]
		Content for anyone else.
[/s2If]
```

### Example PHP Conditional to Check for a Custom Capability

```html
<?php if(current_user_can('access_s2member_ccap_music')): ?>
	Some content for users who can access CCAP: music
<?php else: // Anyone else. ?>
	Content for anyone else.
<?php endif; ?>
```
