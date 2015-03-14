---
title: Building an API Notification Handler (Webhook)
categories: tutorials
tags: api-scripting, api-notifications, mu-plugins-hacks
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/155
---

## API / Notifications (Event-Driven)

If you've tinkered with the s2Member plugin for any length of time, you've probably seen that it comes with an advanced feature for site owners and developers; located in this section of your Dashboard with s2Member installed. See: **Dashboard ⥱ s2Member ⥱ API / Notifications**

## How are These Event-Driven Notifications Useful?

Event-driven Notifications can be sent via email to any number of recipients. They can _also_ be connected to 3rd-party services like InfusionSoft™, other CRMs, or to custom scripts (e.g., [WordPress MUST USE Plugins](http://codex.wordpress.org/Must_Use_Plugins)).

Given this flexibility, s2Member's Notifications make it possible for you to accomplish things that you might have otherwise found impossible to deal with. Custom scripts (e.g., [WordPress MUST USE Plugins](http://codex.wordpress.org/Must_Use_Plugins)) are what I will focus on this article. I will show how to construct a Webhook (aka: API Notification Handler) using a WordPress MU Plugin, and I'll show how to attach it to one of the many event-driven Notifications that are processed by the s2Member software.

![2015-03-13_18-33-05](https://cloud.githubusercontent.com/assets/1563559/6649973/bd02b238-c9af-11e4-8357-e3bc011cc855.png)

## Attaching a URL to an s2Member Notification

### Which Notification?

What event do we want to capture? s2Member’s event-driven Notifications come in many flavors. Do we want to know when a new paying customer signs up (even if they signed up under the terms of a free trial)? Or, when a new user registers period (even if it was a free registration)? Or, do we want to know when actual payments are made by customers (i.e., when the customer is actually charged)? 

There are other options too, but let’s go with s2Member’s Payment Notification in this example. It’s one of the most powerful Notifications, because with this Notification we can connect a script that receives payment details related to _any_ kind of charge associated with Membership Access.

From the documentation in the Dashboard, s2Member says:

> Payment Notifications might include a first Initial Payment that establishes a Subscription. But more importantly, this will be triggered on all future payments that are received for the lifetime of the Subscription. So, unlike the Signup Notification, Payment Notifications take place whenever actual payments are received, instead of just once after signup is completed.

> If a payment is required during signup (i.e., no Free Trial is being offered) a Signup Notification will be triggered and a Payment Notification will _also_ be triggered. In other words, a Payment Notification occurs anytime funds are received, no matter what.

> Payment Notifications are also triggered whenever a Buy Now purchase for Independent Custom Capabilities takes place.

Perfect. I’ll go with this Notification for the example.

### What Variables Do I Need?

The next step (as one who is writing a custom script that will connect to this API Notification), is to find out what variables (Replacement Codes) s2Member makes available when this event takes place. So I take a look in my Dashboard, and I find this documentation under **Dashboard ⥱ s2Member® ⥱ API / Notifications ⥱ Payment Notifications**

![2015-03-13_18-36-19](https://cloud.githubusercontent.com/assets/1563559/6649982/e90381b4-c9af-11e4-9512-7c2bb42c0f98.png)

For this example, I want to receive the `%%user_id%%` value, and I also want to receive the `%%item_number%%` value. So let’s now construct a URL which leads to an MU Plugin that I will script in the next step. Here is what I came up with (see screenshot below).

![2015-03-13_18-41-49](https://cloud.githubusercontent.com/assets/1563559/6650005/0bed8214-c9b1-11e4-8d86-6c3dd60815b4.png)

Now I just need to write the MU Plugin file, so that the URL I entered above will actually do something when s2Member’s Payment Notifications send variables to it.

## Scripting the MU Plugin File (aka: Webhook; aka: Notification Handler)

This script is sometimes referred to as a Notification Handler or Webhook. It will be designed to receive an HTTP request with the variables that I configured in the previous step. I'll write this script in PHP, and I'll write it as an MU Plugin file for WordPress.

### What is an MU Plugin for WordPress?

See: [http://codex.wordpress.org/Must_Use_Plugins](http://codex.wordpress.org/Must_Use_Plugins)

### Why use an MU Plugin for this Webhook?

It's not a requirement. I _could_ just write a vanilla PHP file that stands alone by itself without WordPress. However, if I'm building my site and my entire user base upon the WordPress framework, I really want to keep any custom code that I write in the context of WordPress. By writing this as an MU Plugin I’m maximizing my ability to integrate with the rest of my site. If I were to write a vanilla PHP script that was _not_ directly connected to the WordPress framework, any tasks that I need to perform within my custom script would be _much_ more difficult, if not impossible.

### MU Plugin that Serves as a Webhook (aka: Notification Handler)

This is just a basic example that is designed to work with the URL I formulated above.

```php
<?php
add_action('init', 's2_payment_notification');
function s2_payment_notification()
	{
		if(!empty($_GET['s2_payment_notification']) && $_GET['s2_payment_notification'] === 'yes') 
		// ↑ In my URL, I have `?s2_payment_notification=yes`, that's what I'm looking for here.
			{
				if(!empty($_GET['user_id']) && !empty($_GET['item_number']))
				// In my URL, I have `&user_id=%%user_id%%&item_number=%%item_number%%`, that's what I'm looking for here.
					{
						// Here I might perform any number of tasks related to this user.
					}
				exit; // We can exit here. There's no reason to continue loading WordPress in this case.
			}
	}
```

#### Another Variation with More Elaborate Examples

```php
<?php
add_action('init', 's2_payment_notification');
function s2_payment_notification()
{
	if(!empty($_GET['s2_payment_notification']) && $_GET['s2_payment_notification'] === 'yes')
		// ↑ In my URL, I have `?s2_payment_notification=yes`, that's what I'm looking for here.
	{
		if(!empty($_GET['user_id']) && !empty($_GET['item_number']))
		// In my URL, I have `&user_id=%%user_id%%&item_number=%%item_number%%`, that's what I'm looking for here.
		{
			$user_id     = (integer)$_GET['user_id']; // I'm expecting an integer in this value.
			$item_number = (string)$_GET['item_number']; // I'm expecting a string in this value.

			$user = new WP_User($user_id); // Get a WordPress User object instance so I can work with this customer.

			// Here I might perform any number of tasks related to this user. Such as creating a user option value in WordPress.
			update_user_option($user_id, 'my_custom_data_for_this_user', $item_number);

			// I could also collect details about this user, by accessing properties of my WP_User object instance.
			$first_name = $user->first_name;
			$last_name  = $user->last_name;
			$email      = $user->user_email;
			$username   = $user->user_login;

			// I can also pull s2Member option values related to this user.
			$s2member_subscr_id                = get_user_option('s2member_subscr_id', $user_id);
			$s2member_custom_fields            = get_user_option('s2member_custom_fields', $user_id);
			$s2member_custom                   = get_user_option('s2member_custom', $user_id);
			$s2member_registration_ip          = get_user_option('s2member_registration_ip', $user_id);
			$s2member_paid_registration_times  = get_user_option('s2member_paid_registration_times', $user_id);
			$s2member_first_payment_txn_id     = get_user_option('s2member_first_payment_txn_id', $user_id);
			$s2member_last_payment_time        = get_user_option('s2member_last_payment_time', $user_id);
			$s2member_auto_eot_time            = get_user_option('s2member_auto_eot_time', $user_id);
			$s2member_file_download_access_log = get_user_option('s2member_file_download_access_log', $user_id);

			// I could also log this transaction, by creating a log entry in a static text file on-site.
			file_put_contents(WP_CONTENT_DIR.'/plugins/s2member-logs/my.log', 'Payment Notification Received for User ID: '.$user_id."\n", FILE_APPEND);
		}
		exit; // We can exit here. There's no reason to continue loading WordPress in this case.
	}
}
```

## Additional Articles (Suggested Reading)

### In the WordPress Codex, these articles may offer you additional insight:

- [http://codex.wordpress.org/Must_Use_Plugins](http://codex.wordpress.org/Must_Use_Plugins)  
- [http://codex.wordpress.org/Class_Reference/WP_User](http://codex.wordpress.org/Class_Reference/WP_User) 
- [http://codex.wordpress.org/Function_Reference/get_user_option](http://codex.wordpress.org/Function_Reference/get_user_option) 
- [http://codex.wordpress.org/Function_Reference/update_user_option](http://codex.wordpress.org/Function_Reference/update_user_option)

### These additional articles in the s2Member KB/Codex could also be helpful:

- [Hacking s2Member Via Hooks/Filters](https://github.com/websharks/s2member-kb/issues/150) 
- [s2Member API Functions (from the s2Member Codex)](http://www.s2member.com/codex/stable/s2member/api_functions/package-summary/)
- [s2Member API Constants (from the s2Member Codex)](http://www.s2member.com/codex/stable/s2member/api_constants/package-summary/)
