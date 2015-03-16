---
title: Quick Translation—Changing Words/Phrases
categories: tutorials
tags: translation, mu-plugins-hacks
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/147
---

Some site owners don’t realize what “translation support” really means when it comes to WordPress and s2Member. The fact that s2Member supports translation indicates that s2Member can be translated into an entirely different language. **However, this _also_ makes it possible for tidbits of information to be modified dynamically (e.g., you can change words/phrases easily).**

So maybe I don't want to translate s2Member into an entirely different language. Maybe I just want to change some of it’s words/phrases a bit. As an example, let’s say that I want to change the phrase _“Password (type this twice please)"_, which appears in s2Member Pro-Forms. This phrase is part of the default template set that comes with s2Member Pro. Using a custom template file would accomplish what I need (i.e., I can change quite a bit by using a custom Pro-Form template), but if the only purpose of this custom template is just to change that specific phrase, it seems like too much work. Right? There must be an easier way!

## Translating Words/Phrases (Example)

In this example, I'm going to change every instance of the phrase _“Password (type this twice please)”_. Instead, I want it to read _“Password (enter twice to confirm)”_. I'm also going to change instances of _“Submit Form”_ to just _“Submit”_.

**Please create this directory and file:** `/wp-content/mu-plugins/s2member-o.php`

_**Note:** this is called a MUST USE plugin, see: [MU Plugins @ WordPress.org](http://codex.wordpress.org/Must_Use_Plugins)_

_**See also:** [Hacking s2Member® Plugin w/ Hooks/Filters for WordPress](https://github.com/websharks/s2member-kb/issues/150)_

_**Note Also:** The name of this hack file (`s2member-o.php`) is very important. It allows translations in normal s2Member functionality, and it also supports translations in s2Member-Only Mode—for JavaScript/CSS files. See this related article about [s2Member-Only Mode](https://github.com/websharks/s2member-kb/issues/150)._

```php
<?php
add_filter('gettext_with_context', function ($translated, $original, $context, $text_domain)
	{
		if($context === 's2member-front' && $text_domain=== 's2member')
			{
				if($original === 'Password (type this twice please)')
					$translated = 'Password (enter twice to confirm)';

				else if($original === 'Submit Form')
					$translated = 'Submit';
			}
		return $translated; // Return final translation.
	}, 10, 4);
```

## How Do I Know What Can Be Changed?

Most of what s2Member displays on your site is already configurable in the Dashboard. So changing words/phrases that are already configurable in the UI does _not_ require this approach. However, if you find that portions of the s2Member codebase need to be tweaked, you can use the example above as a guideline.

Throughout s2Member's source code you will see text wrapped inside the `_x()` PHP function call. This is a WordPress translation. Any text that s2Member wraps with this function will ultimately pass through the `gettext_with_context` filter in WordPress—making it possible for you to filter the text and modify it dynamically.

### Inspecting s2Member’s Source Code

Inside: `/s2member-pro/includes/templates/forms/paypal-checkout-form.php` I find this code fragment. Indicating that I can translate this text.

```php
_x('Password (type this twice please)', 's2member-front', 's2member')
```

Inside: `/s2member-pro/includes/templates/forms/paypal-checkout-form.php` I find this code fragment. Indicating that I can translate this text.

```php
_x('Submit Form', 's2member-front', 's2member')
```

So searching the s2Member codebase for instances of `_x` will reveal the portions of s2Member that are translatable. **TIP:** There is also a [master POT translation file](http://plugins.svn.wordpress.org/s2member/trunk/includes/translations/s2member.pot) for s2Member that lists every translatable string in both s2Member and s2Member Pro.
