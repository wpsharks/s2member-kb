---
title: s2Member-Only Mode
categories: tutorials
tags: api-scripting, mu-plugins-hacks
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/144
---

**s2Member-Only Mode**, is a mode in which s2Member loads WordPress from a special file located here in the s2Member Framework: `/wp-content/plugins/s2member/s2member-o.php`; as opposed to using the default WordPress loaders: `/index.php` and/or `/wp-load.php`.

This special file (`/wp-content/plugins/s2member/s2member-o.php`) loads WordPress with _only_ the s2Member plugin; thereby excluding all other active plugins (including any [MUST USE Plugins](http://codex.wordpress.org/Must_Use_Plugins)—they are excluded too); and also your theme is excluded. We load _only_ s2Member in this mode. This technique reduces latency in scenarios where _only_ the s2Member plugin needs to be running in WordPress.

In the current release, s2Member-Only Mode is used for JavaScript/CSS files loaded by s2Member. For example, when s2Member loads it’s dynamic JavaScript or CSS files; we can eliminate latency caused by loading several plugins in an effort to further streamline page speed—with respect to JS/CSS files.

### **Developers:** Impact on s2 Hack Files

If you're [hacking s2Member](https://github.com/websharks/s2member-kb/issues/150) with Hooks/Filters, you are probably using an MU Plugin file with the name: `s2-hacks.php`. That’s perfectly fine for 99% of all hacks. In fact, 99% of the time, the name of your MU Plugin file is not even relevant (i.e., you can name it `s2.php`, `my-s2-hacks.php`, `some-hacks-of-mine.php`, or whatever you like best—as long as it ends with `.php`).

However, in s2Member-Only mode (as detailed above) all MU Plugin files are excluded. So what if you want to hack s2Member in ways that might affect the way s2Member functions in s2Member-Only Mode? The solution is to give your hack file one of the following special names.

#### Special MU Plugin File Names That _Are_ Loaded (Even in s2Member-Only Mode)

```text
s2member-o-hacks.php
s2-o-hacks.php

s2member-o.php
s2-o.php

s2member-a-hacks.php
s2-a-hacks.php

s2member-a.php
s2-a.php
```

You can choose from any of these you like best. Each of them work the same way. They affect WordPress as an [MU Plugin](http://codex.wordpress.org/Must_Use_Plugins), and they are _also_ loaded in s2Member-Only mode (simply because they have one of these special names); i.e., s2Member-Only Mode will load hack files with these special names.

### When should I care about s2Member-Only Mode?

Not often, and you may never need to. However, [translations](https://github.com/websharks/s2member-kb/issues/147) are a good example—they should be applied to all instances of s2Member (even in s2Member-Only Mode). Hacks that modify Hooks/Filters associated specifically with JS/CSS files are another example.

### When _not_ to use one of these special MU Plugin file names?

You should _not_ use these special names if your hack includes dependencies that might not exist in s2Member-Only mode. For instance, if your hack depends on functions provided by your theme, or from another plugin you're running in concert with s2Member; you should _not_ attempt to use that functionality in s2Member-Only Mode, because it will not exist in this mode. In s2Member-Only mode, only WordPress and s2Member are running.

### How can I tell if s2Member is in s2Member-Only Mode?

If you are coding a hack file that needs to detect when s2Member is loaded in s2Member-Only Mode, you can add this check to your custom code.

```php
<?php
if(defined('WS_PLUGIN__S2MEMBER_ONLY'))
	{
		 // Code that runs in s2Member-Only mode.
	}
```

Some site owners will create an MU Plugin specifically for s2Member-Only Mode, where they wrap their custom code with this check. That way it only runs in s2Member-Only Mode (or vice-versa). It’s not common for developers to do this, but it is helpful in a few unique circumstances.

```php
<?php
if(!defined('WS_PLUGIN__S2MEMBER_ONLY'))
	{
		 // Code that runs when NOT in s2Member-Only mode.
	}
```