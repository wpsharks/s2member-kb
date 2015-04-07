---
title: Google Analytics eCommerce Tracking
categories: tutorials
tags: api-tracking
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/146
---

Many site owners (almost every site owner in fact) uses Google® Analytics to track visitors and page views, among other things. This is an extremely useful tool, particularly when it comes to ecommerce sites. While a default JavaScript snippet provided by Google Analytics does the job for most sites, it’s often useful to track individual sales too; so they show up in your Analytics reports at Google.

## Prerequisites (Google Analtyics 101)

<div class="li-margins"></div>

- In this article I will assume that you’ve already integrated the most basic component of Google Analytics into your site. I’m talking about the default JavaScript code snippet they provide (using the [Asynchronous Syntax](https://developers.google.com/analytics/devguides/collection/gajs/)). I will assume that you’ve already integrated that, and that it’s already being loaded up on every page of your site. Many site owners integrate this with a WordPress theme customization panel, or by adding it directly into a WordPress template file—popping the JavaScript into a `header.php` or `footer.php` file.
- I will also assume that you’ve read [this article](https://developers.google.com/analytics/devguides/collection/gajs/gaTrackingEcommerce) at Google.com, and that you’ve enabled ECommerce Tracking for your website. Before Google Analytics can report ecommerce activity for your website **you must enable ECommerce Tracking** on the profile settings page for your website—inside your Google Analytics account.

## Tracking ECommerce Transactions with s2Member

#### See: **Dashboard → s2Member → API/Tracking**

The code snippet (below) should be pasted into the field for **Signup Tracking Codes** and into the field for **Modification Tracking Codes** too. This example is ready-to-go for both Signup Tracking Codes and Modification Tracking Codes. If you would like to track other types of transactions you will need to adapt this example for other scenarios and use the percent `%%` Replacement Codes that s2Member documents in your Dashboard. Please see: **Dashboard → s2Member® → API/Tracking**.

```html
<script type="text/javascript">
	var _gaq = _gaq || [];
	
	_gaq.push(['_addTrans',
	  '%%subscr_id%%', // transaction ID - required
	  '%%cv0%%', // affiliation or store name
	  '%%initial%%' // total - required
	]);
	
	_gaq.push(['_addItem',
	  '%%subscr_id%%', // transaction ID - required
	  '%%item_number%%', // SKU/code - required
	  '%%cv0%%', // product name
	  '%%item_number%%', // category or variation
	  '%%initial%%', // unit price - required
	  '1' // quantity - required
	]);
	
	_gaq.push(['_trackTrans']); // Submits transaction to the Analytics servers.
</script>
```

## UPDATE: Google Analytics Universal Platform

**UPDATE:** If your Google Analytics account was migrated to the new Universal platform and you are using the new Universal platform tracking code on your site; the above example will _not_ function properly. Here is an updated example that assumes you are using the Universal platform tracking code.

```html
<script type="text/javascript">
	ga('require', 'ecommerce', 'ecommerce.js'); // Load the ecommerce plug-in.
	
	ga('send', 'event', 'Sales', 'sale-%%item_number%%', 'Signup Sale (%%item_number%% / %%subscr_id%%)', parseInt('%%initial%%'), {'nonInteraction': 1});
	
	ga('ecommerce:addTransaction', {
	  'id': '%%subscr_id%%', // Transaction ID. Required
	  'affiliation': '%%cv0%%', // Affiliation or store name
	  'revenue': '%%initial%%', // Grand Total
	  'shipping': '0', // Shipping
	  'tax': '0' // Tax
	});
	
	ga('ecommerce:addItem', {
	  'id': '%%subscr_id%%', // Transaction ID. Required
	  'name': '%%cv0%%', // Product name. Required
	  'sku': '%%item_number%%', // SKU/code
	  'category': '%%item_number%%', // Category or variation
	  'price': '%%initial%%', // Unit price
	  'quantity': '1' // Quantity
	});
	
	ga('ecommerce:send'); // Send transaction and item data to Google Analytics.
</script>
```

**See also:** [Official Instructions for ECommerce Tracking](http://s2member.com/r/universal-ga-ecommerce-tracking/)
