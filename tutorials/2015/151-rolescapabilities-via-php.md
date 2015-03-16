---
title: Roles/Capabilities via PHP
categories: tutorials
tags: api-scripting,mu-plugins-hacks,roles-capabilities
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/151
---

## Quick Example of a Role Change

```php
<?php
$user_id = 123;
$user = new WP_User($user_id);
$user->set_role("s2member_level1");
```

Where `s2member_level1` could be any Role that you've configured in your WordPress installation.

#### Here are the most common Roles

```text
subscriber
s2member_level1
s2member_level2
s2member_level3
s2member_level4

author
contributor
administrator
editor
```

## Adding/Removing Individual Capabilities

```php
<?php
$user_id = 123;
$user = new WP_User($user_id);
$user->add_cap('access_s2member_level0');
$user->add_cap('access_s2member_level1');
$user->add_cap('access_s2member_ccap_music');
$user->add_cap('access_s2member_ccap_videos');
$user->remove_cap('access_s2member_level2');
```

If you wanted to loop through all of your Users in a CRON job, or in some other custom coding project, you might do something like this.

Create this directory and file:
`/wp-content/mu-plugins/my-cron-job.php`

```php
<?php
add_action('init', function ()
{
	if(!empty($_GET['my_cron_job']) && $_GET['my_cron_job'] === 'secret-cron-job-key')
	{
		foreach(get_users() as $user)
		{
			$user         = new WP_User($user->ID);
			$_10_days_ago = strtotime('-10 days');
			if(s2member_registration_time($user->ID) <= $_10_days_ago)
			{
				# A Member for at least 10 days.
				# Promote them now to Level #2.
				if(!$user->has_cap("access_s2member_level2"))
					$user->set_role("s2member_level2");
			}
		}
		exit;
	}
});
```

Now create a CRON job that calls this URL periodically (once a day perhaps).

```text
http://example.com/?my_cron_job=secret-cron-job-key
```

Be very careful that you do _not_ modify the Administrator's Role on the site. If you do, you may lose access to your WordPress Dashboard. If this happens, you can set the Role for your account back to an administrator.

```php
<?php
$user = new WP_User('admin'); // Whatever your Username is.
$user->set_role('administrator');
```