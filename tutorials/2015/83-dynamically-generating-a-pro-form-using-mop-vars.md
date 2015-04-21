---
title: Dynamically Generating a Pro-Form Using MOP Vars
categories: tutorials
tags: mu-plugins-hacks,s2mop,pro-forms
author: brucewsinc
github-issue: https://github.com/websharks/s2member-kb/issues/83
toc-enable: false
---

[Membership Options Variables (MOP Vars)](http://s2member.com/kb-article/s2mop-shortcode/#toc-512d8de7) provide site owners with a way to determine what a potential customer was attempting to access before they were redirected to your Membership Options Page. The information provided by MOP Vars can be extremely useful when you want to present offers (or checkout forms) that are tailored to a specific type of request—for a specific type of content.

See also: **Dashboard → s2Member → API / Scripting → Membership Options Page / Variables**

![](https://cloud.githubusercontent.com/assets/1568616/6052572/675fefaa-aca2-11e4-92d2-a81eb1e36c7e.png)

## Example: Auto-Generating Pro-Forms That Sell Custom Capabilities

**NOTE:** This is very advanced functionality and requires experience working with PHP code.

**Prerequisite:** Please install the [ezPHP](https://wordpress.org/plugins/ezphp/) plugin for WordPress so you can use PHP code in Posts/Pages.

Now, you can auto-generate Pro-Forms that sell the _exact_ set of Custom Capabilities that a customer needs in order to access the content they requested. This is accomplished by reading `_s2member_vars` (MOP Vars), breaking them apart, checking for CCAPs being required, and then constructing a Pro-Form that sells those Custom Capabilities.

```php
<?php
$price = '6.99'; // I'll assume every purchase is the same price in this example.
$shortcode = '[s2Member-Pro-PayPal-Form ... ra="%%price%%" ccaps="%%ccaps%%" .../]';
// ↑ Note: this shortcode is abbreviated for clarity. Replace `...` with the other shortcode attributes you need.

if(!empty($_REQUEST["_s2member_vars"])) {
	@list($restriction_type, $requirement_type, $requirement_type_value, $seeking_type, $seeking_type_value, $seeking_uri)
    	= explode("..", stripslashes((string)$_REQUEST["_s2member_vars"]));

	if (!empty($requirement_type_value) && $requirement_type === 'ccap')
		$shortcode = str_replace('%%ccaps%%', $requirement_type_value, str_replace('%%price%%', $price, $shortcode));
	else $shortcode = '';

	echo $shortcode; // Output the shortcode and let WordPress and s2Member do their thing!
}
?>
```

After updating this example to reflect your specific site configuration (i.e., you need to update the `$shortcode` value), you would add this code your Membership Options Page (remember, you'll need to install the [ezPHP](http://wordpress.org/plugins/ezphp/) plugin to be able to use PHP code inside a WordPress Post/Page).
