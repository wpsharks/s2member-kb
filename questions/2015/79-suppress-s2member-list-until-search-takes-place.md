---
title: Suppress `[s2Member-List /]` until search takes place?
categories: questions
tags: s2member-list, shortcodes, mu-plugins-hacks
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/79
---

> I'm using `[s2Member-List-Search-Box /]` together with `[s2Member-List /]`. After I press search it displays search results. Is there a way to suppress the list unless and until a search is performed?

Yes, you could use a conditional for this.

1. Install the ezPHP plugin for WordPress. See: https://wordpress.org/plugins/ezphp/
2. Use the Text tab in your WordPress editor and add the following conditional PHP tags.

```html
[s2Member-List-Search-Box /]

<?php if(!empty($_REQUEST['s2-s'])): ?>
	[s2Member-List enable_list_search="yes" /]
<?php endif; ?>
```
