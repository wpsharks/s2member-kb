---
title: Pro Login Widget
categories: tutorials
tags: login-widgets
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/148
---

## s2Member® Pro Login Widget

Integrated specifically to meet the needs of s2Member installations; s2Member Pro's Login Widget is specifically designed to work with s2Member (this comes with any purchase of s2Member Pro). It can also be integrated via PHP; i.e., you can even embed it into a theme file or another plugin if you like.

[![](http://cdn.websharks-inc.com/s2member/uploads/pro-screen-pro-login-widget.jpg){.aligncenter}](http://cdn.websharks-inc.com/s2member/uploads/pro-screen-pro-login-widget.jpg)

## Configuring the Pro Login Widget in WordPress

- See: **Dashboard → Appearance → Widgets → s2Member Pro Login Widget**
- Drag n' drop the Pro Login Widget to a Sidebar of your choosing; i.e., one supported by your theme.
- Expand the Pro Login Widget panel in WordPress and fill in the optional configuration fields.

## Embedding the Pro Login Widget via PHP

#### Use API Function: `s2member_pro_login_widget($options, $args)`

The s2Member Pro Login Widget can be embedded directly into a theme/plugin file. The API Function `s2member_pro_login_widget()` will return the HTML output from the widget function call. Example usage: `<?php echo s2member_pro_login_widget(); ?>`.

<div class="li-margins"></div>

- The `$options` parameter (array) is completely optional (i.e., _not_ required). It can be passed in as an array of options; overriding some or all of these defaults:
  -   `'title' => 'Membership Login'` Title when _not_ logged in. Or, leave this blank if you'd prefer not to show a title.
  -   `'signup_url' => '%%automatic%%'` Full Signup URL. Or, use `%%automatic%%` for the Membership Options Page. If you leave this blank it will not be shown.
  -   `'login_redirect' => ''` Empty = Login Welcome Page, `%%previous%%` = Previous Page, `%%home%%` = Home Page. Or, use a full URL of your own.
  -   `'logged_out_code' => ''` HTML/PHP code to display when logged out. May also contain WP Shortcodes if you like.
  -   `'profile_title' => 'My Profile Summary'` Title when a User is logged in. Or you can leave this blank if you'd prefer not to show a title.
  -   `'display_gravatar' => '1'` Display Gravatar image when logged in? `1` = yes, `0` = no. Gravatars are based on email address.
  -   `'link_gravatar' => '1'` Link Gravatar image to Gravatar.com? `1` = yes, `0` = no. Allows Users to setup a Gravatar.
  -   `'display_name' => '1'` Display the current User's WordPress Display Name when logged in? `1` = yes, `0` = no.
  -   `'logged_in_code' => ''` HTML/PHP code to display when logged in. May also contain WP Shortcodes if you like.
  -   `'logout_redirect' => '%%home%%'` Empty = Login Screen, `%%previous%%` = Previous Page, `%%home%%` = Home Page. Or, use a full URL of your own.
  -   `'my_account_url' => '%%automatic%%'` Full URL of your own. Or, use `%%automatic%%` for the Login Welcome Page. Leave empty to not show this at all.
  -   `'my_profile_url' => '%%automatic%%'` Full URL of your own. Or, use `%%automatic%%` for a JavaScript popup. Leave empty to not show this at all.

<div class="li-margins"></div>

- The `$args` parameter (array) is also completely optional (i.e., _not_ required). It can be passed in as an array of options; overriding some or all of these defaults:
  -   `'before_widget' => ''` HTML code to display before the widget.
  -   `'before_title' => '<h3>'` HTML code to display before the title.
  -   `'after_title' => '</h3>'` HTML code to display after the title.
  -   `'after_widget' => ''` HTML code to display after the widget.

### Example PHP Code Using `s2member_pro_login_widget()`

```php
<?php echo s2member_pro_login_widget(); ?>
```

##### More Elaborate Example w/ Configuration Options/Args

```php
<?php
echo s2member_pro_login_widget(
	array(
		'title'            => 'Membership Login',
		'signup_url'       => '%%automatic%%',
		'login_redirect'   => '',
		'logged_out_code'  => '',
		'profile_title'    => 'My Profile Summary',
		'display_gravatar' => '1',
		'link_gravatar'    => '1',
		'display_name'     => '1',
		'logged_in_code'   => '',
		'logout_redirect'  => '%%home%%',
		'my_account_url'   => '%%automatic%%',
		'my_profile_url'   => '%%automatic%%',
	),
	array(
		'before_widget' => '',
		'before_title'  => '<h3>',
		'after_title'   => '</h3>',
		'after_widget'  => '',
	)
);
```
