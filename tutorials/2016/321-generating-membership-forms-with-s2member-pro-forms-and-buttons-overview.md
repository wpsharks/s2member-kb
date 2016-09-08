---
title: Generating Membership Forms with s2Member Pro-Forms and Buttons (Overview)
categories: tutorials
tags: pro-forms, paypal, auto-return
author: patdumond
github-issue: https://github.com/websharks/s2member-kb/issues/321
---

Custom Return URLs are another advanced feature of s2Member. You can create custom pages to direct your Members upon return from the payment gateway following a successful checkout. You can add a special attribute to any Pro-Form Shortcode (`success="/my-thank-you-page/"` where `my-thank-you-page` is the Slug to your thank you page). This feature makes it possible to integrate Pro-Forms in very creative ways and verify (validate) Replacement Code variables.

*This article is part of the [s2Member User's Guide](http://s2member.com/kb/kb-tag/s2member-users-guide), a series of articles that cover the fundamentals of using s2Member.*

For more information on creating a registration thank you page, please see the s2Member Knowledge Base article, [Creating a Registration Thank You Page](https://s2member.com/kb-article/creating-a-registration-thank-you-page/).

## Configuring Custom Return URLs Upon Success

See **WordPress Dashboard → s2Member (Pro) → PayPal Pro-Forms → Custom Return URLs Upon Success**

A Custom Return URL is optional. If you only need to obtain details for the purpose of tracking sales, you should just use the simpler **API Tracking** methods provided by s2Member (see **WordPress Dashboard → s2Member (Pro) → API / Tracking**). If you do not use the `success=""` attribute in your Shortcode, s2Member returns your new Member to your website gracefully.

![s2Member - Custom Return URLs Upon Success](https://cloud.githubusercontent.com/assets/53005/18335869/a151fff0-7550-11e6-99e4-c453e594dfff.png)

Each Pro-Form listed on this configuration panel has its set of available Replacement Codes site owners, and developers can use in Pages created for Custom Return URLs. The lists below explain each of these Replacement Codes. Please check the configuration panel for the specific type of Pro-Form you used for checkout to ensure the Replacement Code you want to use is available for that checkout form.

### Basic Replacement Codes

- `%%role%%` = The Role ID of the Member who registered. For example, `administrator`, `subscriber`, or `s2member_level[0-9]`.                                
- `%%ccaps%%` = Custom Capabilities in comma-delimited format. For example,  `music`,`videos`,`free_gift. 
- `%%auto_eot_time%%` = Auto-EOT Time, if applicable, in `unix_timestamp` format. For example, `1299925670`. 
- `%%user_first_name%%` = The First Name of the Member who registered. 
- `%%user_last_name%%` = The Last Name of the Member who registered. 
- `%%user_full_name%%` = The Full Name (First & Last) of the Member who registered. 
- `%%user_email%%` = The Email Address of the Member who registered. 
- `%%user_login%%` = The Username the Member set during registration. 
- `%%user_pass%%` = The Password set or generated during registration. 
- `%%user_ip%%` = The IP Address of the Member who registered, via `$_SERVER["REMOTE_ADDR"]`. 
- `%%user_id%%` = A unique WordPress User ID generated during registration. 
- `%%s_response%%` = The response message that would have been displayed to the Customer had they not been redirected to your Custom Return URL upon success. This may contain some basic HTML. For instance, it might contain a link to the login page. You do not have to use this. You can generate a custom response if you like.

     This value is encrypted. Use [s2member_decrypt()](http://www.s2member.com/codex/stable/s2member/api_functions/package-functions/%23src_doc_s2member_decrypt()) to decrypt the value. (Use this value to display this default message to the Member on the custom thank you page.)

### Custom Registration/Profile Field Replacement Codes 

See **WordPress Dashboard → s2Member (Pro) → General Options → Registration/Profile Fields & Options**

The format for the Replacement Code for a Custom Registration/Profile Field you created is two percent signs (`%%`) followed by the ID of the Custom Registration/Profile Field followed by two more percent signs (`%%`).

For example, `%%date_of_birth%%` is a valid Replacement Code if you have a Custom Registration/Profile Field with the ID `date_of_birth`. `%%street_address%%` is valid if you have a Custom Registration/Profile Field with the ID `street_address`. 

### Custom Value Replacement Codes

Replacement Codes associated with the `custom` attribute in your Pro-Form shortcode.

- `%%cv0%%` = The domain of your site passed through the `custom` attribute in your shortcode. 
- `%%cv1%%` = If you need to track additional custom variables you can delimit them with pipes (`|`) into the `custom` attribute. For example,  `custom="yourdomain.com|cv1|cv2|cv3"`. Replace `cvx` with text of your own in the `custom` attribute. You can have an unlimited number of custom variables. This is for advanced webmasters, but the functionality has been made available for those who need it.

### Replacement Codes Related to Membership Sales, Signups, and Modifications

- `%%subscr_id%%` = The Subscription ID which remains constant throughout any and all future payments. Note: If you are selling Lifetime or Fixed Term (non-recurring) access, the `%%subscr_id%%` is set to the Transaction ID for the purchase. 
- `%%subscr_baid%%` = This is the Subscription's Billing Agreement ID which remains constant throughout any and all future payments. It is applicable only with PayPal Pro (Payflow Edition) and only for Express Checkout transactions that require a Billing Agreement. In all other cases the `%%subscr_baid%%` is set to the `%%subscr_id%%` value. 
- `%%currency%%` = Three-character currency code (uppercase). For example, `USD`. - `%%currency_symbol%%` = Currency code symbol. For example, `$`. 
- `%%initial%%` = The Initial Fee charged during signup. If you offered a Free Trial, this equals 0. This value always equals the amount of money the Customer spent on this particular purchase. 
- `%%regular%%` = The Regular Amount of the Subscription. If you offer something free, this equals 0. This value represents how much the Subscription costs after the Initial Period expires. If you did not provide an Initial Period at a different price, `%%initial%%` and `%%regular%%` are the same. 
- `%%recurring%%` = This is the amount charged on a recurring basis or 0 if non-recurring. 
- `%%item_number%%` = The Item Number (colon separated level:custom_capabilities:fixed term) for the Membership Subscription. 
- `%%item_name%%` = The Item Name (as provided by the desc="" attribute in your Shortcode, which briefly describes the Item Number). 
- `%%initial_term%%` = This value represents the term length of the Initial Period. This is a numeric value, followed by a space, then a single letter. 
- `%%regular_term%%` = This is the term length of the Regular Period. This is a numeric value, followed by a space, then a single letter. 
- `%%modification%%` = 1 if/when a Billing Modification has just taken place; otherwise, 0 indicates a new Customer. 
- `%%user_first_name%%` = The First Name listed on their User account. This value might be different than what is on file with your Payment Gateway. 
- `%%user_last_name%%` = The Last Name listed on their User account. This value might be different than what is on file with your Payment Gateway.

## Verifying the Integrity of Replacement Codes

If you know a little PHP, you can verify (validate) the integrity of the Replacement Codes returned by s2Member. This process is important because, in this particular situation, Replacement Codes are passed publicly in the query string of your Custom Return URL. In other words, a Customer could manually change one of the values (like the dollar amounts). For this reason, you should always validate the data returned to any processing routines you use. In the PHP code for your Custom Return URL, you can use this s2Member API Function: `s2member_pro_paypal_s2p_v_query_ok()`. (If you're embedding PHP code inside a Post/Page, you'll need to use a plugin such as [ezPHP](http://wordpress.org/plugins/ezphp/) to allow processing of arbitrary PHP code.)

Here are some examples:

1. Shortcode attribute: `success="/thank-you/?subscr_id=%%subscr_id%%&initial=%%initial%%&regular=%%regular%%"`

2. s2Member returns Customer to: `/thank-you/?subscr_id=123&initial=0.00&regular=24.95&s2p-v=234098234-23409sdfs234sd234209sdf`

3. Now, in your Custom Return Page, you will need to use this code to validate the transaction details before processing anything:

```php
<?php  
if (s2member_pro_paypal_s2p_v_query_ok ($_SERVER["QUERY_STRING"]))  
    {  
        echo 'Looks good. Verified in the first 10 seconds.';  
    }  
?>
```

s2Member only verifies a query string for up to 10 seconds following submission. After 10 seconds, `s2member_pro_paypal_s2p_v_query_ok()` always returns `false`, even if the integrity of the query string is valid. This limitation prevents a Customer from bookmarking your Return URL, possibly causing duplicate commissions, in case you are using it for tracking purposes.

Again, if you only need to obtain details for the purpose of tracking sales, you should just use the simpler API Tracking methods provided by s2Member (**WordPress Dashboard → s2Member → API / Tracking**). The API Tracking methods track each sale exactly **one**  time for each Customer.

If it is your intention to allow Customers to bookmark your Custom Return URL, you can do that. Just be aware that `s2member_pro_paypal_s2p_v_query_ok()` will return false after the first 10 seconds. If you want to verify after 10 seconds, you can pass a second argument to the function, like this:

```php
<?php  
if (s2member_pro_paypal_s2p_v_query_ok ($_SERVER["QUERY_STRING"], "ignore-time"))  
    {  
        echo 'Looks good. Verified; regardless of time.';  
    }  
?>
```

### Could a Customer change the timestamp in the URL?

Based on the structure of the URL, it might look like this is possible, however, it is **not**. s2Member uses an advanced checksum to prevent this.

### Can I get rid of the `s2p-v` variable?

No, s2Member **always** passes this variable to your Custom Return URL for necessary verification purposes.
