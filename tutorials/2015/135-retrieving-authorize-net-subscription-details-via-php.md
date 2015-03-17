---
title: Authorize.Net Subscription Details via PHP
categories: tutorials
tags: authorize.net,api-scripting,mu-plugins-hacks
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/135
toc-enable: false
---

If you need to retrieve details about an Authorize.Net subscription using PHP you can use the `c_ws_plugin__s2member_pro_authnet_utilities::authnet_arb_response()` utility function that is provided by s2Member. This will make a request to the Authorize.Net servers.

The following snippet of PHP code demonstrates how to retrieve information about the current user's Authorize.Net subscription. It's a very basic example that takes advantage of s2Member's existing integration with the Authorize.Net API.

_For more information about the underlying API call, see: [ARBGetSubscriptionStatusRequest](http://www.authorize.net/support/ARB_guide.pdf#page=21)_

```php
<?php
// Get the ID of the user currently logged in.
$user_id = get_current_user_id();

// Get the Authorize.Net Subscription ID from the 'Paid Subcr. ID' field on the users account.
$user_subscr_id = get_user_option('s2member_subscr_id', $user_id);

// Build an array with the Authorize.Net request details.
$authnet = array('x_subscription_id' => $user_subscr_id, 'x_method' => 'status');

// Send a request to Authorize.Net to get the details about the subscription.
$authnet = c_ws_plugin__s2member_pro_authnet_utilities::authnet_arb_response($authnet);

// Print everything from the response. This array contains ALL details related to their Authorize.Net Recurring Billing Profile.
print_r($authnet);
?>
```

The code example above does not include any logic for verifying that the current user actually has an Authorize.Net subscription associated with their account. If you implement this example you’ll want to make sure that the current user has an s2Member Role (s2Member Level 0-4+), that they used the Authorize.Net payment gateway, and that `$user_subscr_id` actually contains a value.

## A More Complete Example w/ Conditionals

```php
<?php
if(($user = wp_get_current_user()) && $user->has_cap('access_s2member_level1'))
	if(($user_subscr_id = get_user_option('s2member_subscr_id', $user->ID)))
		if(get_user_option('s2member_subscr_gateway', $user->ID) === 'authnet')
		{
			$authnet = array('x_subscription_id' => $user_subscr_id, 'x_method' => 'status');
			$authnet = c_ws_plugin__s2member_pro_authnet_utilities::authnet_arb_response($authnet);
			print_r($authnet);
		}
```
