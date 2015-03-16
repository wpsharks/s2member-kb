---
title: Security Badges
categories: tutorials
tags: security-badge
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/145
---

<div class="pull-right l-margin b-margin">
	[s2Member-Security-Badge v="1" /]
</div>

An s2Member® Security Badge (optional), can be used to express your site’s concern for security. Demonstrating to all Users/Members that your site (and the s2Member software) take security seriously. From your WordPress Dashboard, please see: **s2Member® → General Optionals → Security Badge**.

## Instructions: Qualifying Your Site

To qualify your site you will need to enable s2Member’s Security Badge Status API & generate a Security Encryption Key in your Dashboard—with s2Member installed as an active plugin. Also, there are a few additional requirements set forth below. Some of these requirements pertain to WordPress security in general, and some of these requirements are s2Member-specific. What we want to see is that you’ve made an effort to tighten security on your installation of WordPress by following these guidelines. Your site and your users will be safer as a result :-) **NOTE:** Once you’ve completed the steps below it can still take up to 60 minutes for your s2Member Security Badge image to show a green status for the first time.

<div class="li-margins"></div>

- ### Is your s2Member Badge Status API enabled?

  Please see: **Dashboard → s2Member® → General Options → Security Badge → Badge Status API**

- ### Does your `/wp-config.php` file have all of these configuration values filled in properly (e.g., have you setup your WordPress Security Keys)?

  *See: [http://codex.wordpress.org/Editing_wp-config.php#Security_Keys](http://codex.wordpress.org/Editing_wp-config.php#Security_Keys)

  _**IMPORTANT NOTE:** Each of these MUST be at least 60 characters and must NOT contain the default: `unique phrase` values that come with WordPress. We suggest using the [super easy Security Key Generator](https://api.wordpress.org/secret-key/1.1/salt/)._

- ### Have you created a Security Encryption Key for your s2Member installation?

  Please see: **Dashboard → s2Member® → General Options → Security Encryption Key**

  _**IMPORTANT NOTE:** This MUST be at least 60 characters in length._

- ### Does your `/wp-config.php` file have both of these configuration values?

  These configuration values MUST be filled in: `DB_USER` & `DB_PASSWORD`. See: [http://codex.wordpress.org/Editing_wp-config.php#Set_Database_Name](http://codex.wordpress.org/Editing_wp-config.php#Set_Database_Name)

  _**IMPORTANT NOTE:** These values must NOT be exactly the same._

- ### Have you configured your s2Member Unique IP Restriction Options yet?

  Please see: **Dashboard → s2Member® → Restriction Options → Unique IP Restrictions**
  
  _**IMPORTANT NOTE:** This must NOT be set to a value of: infinite._

- ### Have you configured your s2Member® Brute Force IP Restrictions yet?

  Please see: **Dashboard → s2Member® → Restriction Options → Brute Force IP Restrictions**
  
  _**IMPORTANT NOTE:** This must NOT be set to a value of: infinite._

- ### Have you disabled debug logging in your s2Member® configuration yet?

  Please see: **Dashboard → s2Member® → Log Files (Debug) → Logging Configuration**
  
	_**IMPORTANT NOTE:** All logging MUST be disabled to prevent log files that may contain sensitive data. In addition, any existing log files from previous debugging efforts MUST be deleted before your s2Member Security Badge will go green. See: **Dashboard → s2Member® → Log Files (Debug)** for further details. The only way to bypass this requirement is to set a custom location for your s2Member log files. If you'd like to do this, please create this directory and file: `/wp-content/mu-plugins/s2-logs-dir.php`_

	```php
	<?php
	add_filter('ws_plugin__s2member_logs_dir', function($dir){
	  return ($dir = '/absolute/path/to/my/custom/logs/dir');
	  // Ideally a location outside of the HTTP space (more secure).
	  // Something like: /var/logs/s2member
	});
	```

## Test Your Own Badge Status

**Look at your installation here:** `www.yoursite.com/?s2member_s_badge_status=1`. If you visit this link on your WordPress installation you should get a plain text file that contains only a single value of: `1` (indicating your site is in the green with s2Member). If you don’t, one of the above is the likely cause. Please go back over your configuration. **IMPORTANT:** Once this shows a value of `1` it can still take up to 60 minutes for your s2Member Security Badge image to show a green status for the first time.

## s2Member® Security Badge Variations

There are a few different Security Badge variations. Which variation you decide to go with is completely up to you. You can adjust the variation that you display on-site by modifying the Shortcode Attribute: `v="1|2|3"`. For further details on this Shortcode, please see: **Dashboard → s2Member® → General Options → Security Badge**

<div class="li-margins"></div>

<table>
	<tbody>
		<tr>
			<td class="text-center">`[s2Member-Security-Badge v="1" /]`<br />[s2Member-Security-Badge v="1" /]</td>
			<td class="text-center">`[s2Member-Security-Badge v="2" /]`<br />[s2Member-Security-Badge v="2" /]</td>
			<td class="text-center">`[s2Member-Security-Badge v="3" /]`<br />[s2Member-Security-Badge v="3" /]</td>
		</tr>
	</tbody>
</table>
