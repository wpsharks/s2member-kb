---
title: How can I find out the next billing date?
categories: questions
tags: paypal, api-scripting, mu-plugins-hacks
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/69
toc-enable: false
---

> How can I find out the next billing date?
> I want to display the "Next Payment Date" to a customer.

This functionality is not built into the UI for the s2Member. However, s2Member Pro (when integrated with PayPal Pro) comes with the following API Functions that are not too difficult to work with, and they make this possible.

```php
<?php
s2member_pro_paypal_rbp_times_for_user($user_id);
s2member_pro_payflow_rbp_times_for_user($user_id); // Payflow Edition.
```

Both of these methods do the same thing. They contact your PayPal account and query the PayPal API to find out about payment times for a specific user ID in WordPress.

### Integrating These API Functions

Please create this directory and file:
`/wp-content/mu-plugins/s2-rbp-times.php`

```php
<?php
add_shortcode('s2RBPTimes', 's2_rbp_times');

function s2_rbp_times($attr)
{
	$user = wp_get_current_user();

	$defaults = array(
		'gateway' => 'paypal', // Or payflow
		'field'   => 'next_billing_time', // Or last_billing_time
		'format'  => DATE_RFC2822, // See http://php.net/manual/en/function.date.php
	);
	$attr     = array_merge($defaults, (array)$attr);
	$attr     = array_intersect_key($attr, $defaults);
	$times    = NULL; // Initialize.

	if($attr['gateway'] === 'paypal')
		$times = s2member_pro_paypal_rbp_times_for_user($user->ID);

	else if($attr['gateway'] === 'payflow')
		$times = s2member_pro_payflow_rbp_times_for_user($user->ID);

	if(isset($times, $times[$attr['field']]))
	{
		$time = $times[$attr['field']];
		return date($attr['format'], $time);
	}
	return ''; // Not possible.
}
```

### Example WordPress Shortcode Usage

Now pop this into your Post/Page editor in WordPress.

```
[s2RBPTimes gateway="paypal" field="next_billing_time" /]
```

Or, if you're using the Payflow Edition of PayPal.

```
[s2RBPTimes gateway="payflow" field="next_billing_time" /]
```

These show a user the Next Billing Date (and time). You can integrate them into other content within a Post/Page to achive something like this.

```
Next Billing Date: [s2RBPTimes gateway="paypal" field="next_billing_time" /]
```
