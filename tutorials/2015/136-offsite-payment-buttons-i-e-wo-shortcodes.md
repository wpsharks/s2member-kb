---
title: Offsite Payment Buttons (i.e., w/o Shortcodes)
categories: tutorials
tags: clickbank,paypal,api-scripting,mu-plugins-hacks
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/136
---

## Why Offsite Payment Buttons?

An example use case would be if you have a membership site powered by WordPress + s2Member, but you actually market this site elsewhere; i.e., on a different site altogether; one that is not running WordPress or s2Member. In a case like this you have a few choices, but here are the ones that we commonly recommend.

1. Use an Offsite Payment Button via Redirections (as seen below).
2. Or, use s2Member Pro-Forms, where you simply link to the site that contains your s2Member Pro-Form, which facilitates checkout; i.e., you link to the site that powers your membership and checkout process.

Let's stay focused on option 1 in this article. If you're not using s2Member Pro or you just prefer to use Payment Buttons instead of Pro-Forms—for whatever crazy reason, you can build a redirection script as seen below.

What it boils down to is that you generate a shortcode with s2Member (like always), but you change the `output="anchor"` to `output="url"`. Running this in PHP gives you a URL at runtime that you can then redirect a visitor to. In this way, you can use this technique in offsite button endeavors :-)

## Example Code for PayPal Buttons

Create this directory and file:
`wp-content/mu-plugins/s2-paypal-redirect.php`

```php
<?php
add_action('wp_loaded', function()
{
	if(isset($_REQUEST['paypal']) && $_REQUEST['paypal'] === 'redirect')
	// A URL leading to this site with: `/?paypal=redirect` ↑
	{
		$paypal_checkout = do_shortcode('[s2Member-PayPal-Button ... output="url" /]');
		// The Shortcode above has been abbreviated here for clarity ↑
		// You will need to generate your own full PayPal Button Shortcode and set output="url" as seen above.
		wp_redirect($paypal_checkout); exit;
	}
});
```

With this in place, you can lead a visitor to checkout at PayPal by creating a link. And, you can link to this from anywhere, making it a neat solution when you want to start the checkout process from an offsite location.

```text
http://example.com/?paypal=redirect
```

## Example Code for ClickBank Buttons

Create this directory and file:
`wp-content/mu-plugins/s2-clickbank-redirect.php`

```php
<?php
add_action('wp_loaded', function()
{
	if(isset($_REQUEST['clickbank']) && $_REQUEST['clickbank'] === 'redirect')
	// A URL leading to this site with: `/?clickbank=redirect` ↑
	{
		$clickbank_checkout = do_shortcode('[s2Member-Pro-ClickBank-Button ... output="url" /]');
		// The Shortcode above has been abbreviated here for clarity ↑
		// You will need to generate your own full ClickBank Button Shortcode and set output="url" as seen above.
		wp_redirect($clickbank_checkout); exit;
	}
});
```

With this in place, you can lead a visitor to checkout at ClickBank by creating a link. And, you can link to this from anywhere, making it a neat solution when you want to start the checkout process from an offsite location.

```text
http://example.com/?clickbank=redirect
```