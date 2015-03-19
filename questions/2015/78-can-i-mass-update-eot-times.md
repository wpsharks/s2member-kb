---
title: Can I mass-update EOT Times?
categories: questions
tags: eot-time, import-export-tools, mu-plugins-hacks
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/78
---

> Is there an automatic solution to extend the EOT Time for every single member at once (even though they all have different EOT dates)? Thank you!

## Two Ways to Extend the EOT Time

s2Member stores the EOT Time in a user option field within WordPress. So the answer to your question would be yes. There are two ways to accomplish this.

### 1. Doing a Mass-Update with s2Member's Advanced Import/Export Functionality

Using [s2Member's Advanced Import/Export Tools](https://github.com/websharks/s2member-kb/issues/121) you can pull an export of existing users. Open the CSV export file. Edit the `meta_key__wp_s2member_auto_eot_time` data column. This data column will contain a [UNIX Timestamp](http://www.unixtimestamp.com/) that you can modify using tools provided by CSV editors such as [Excel](http://products.office.com/en-us/excel), [OpenOffice](https://www.openoffice.org/), or [Numbers](https://www.apple.com/mac/numbers/) on a Mac. When you're done editing, use the modified CSV file; importing that back into WordPress with s2Member's Advanced Import tool.

### 2. Writing a Custom Script (MU Plugin)

This technique requires a bit of scripting. Here's a quick example.

Create this directory and file:
`/wp-content/mu-plugins/s2-extend-eot.php`

```php
<?php
add_action('init', function ()
{
	if(empty($_GET['s2_extend_eot'])
	   || $_GET['s2_extend_eot'] !== '[secret key]')
		return; // Nothing to do here.

	$days_to_add = 90; // Extend by 90 days.

	foreach(get_users() as $user)
	{
		if(($eot_time = get_user_option('s2member_auto_eot_time', $user->ID)))
			update_user_option($user->ID, 's2member_auto_eot_time', $eot_time + ($days_to_add * DAY_IN_SECONDS));
	}
	exit('All EOT Times updated.');
});
```

Now you can visit the following URL exactly _one_ time to perform the update.

```text
http://example.com/?s2_extend_eot=[secret key]
```

_Don't forget to replace `[secret key]` with a secret of your choosing. Also, you will want to change `$days_to_add` to the actual number of days that you want to add to each EOT Time._