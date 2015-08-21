---
title: Is it possible to import coupon codes?
categories: questions
tags: pro-coupon-codes
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/259
---

You can add coupons in your WordPress Dashboard one-by-one, or you can import them if you'd like. However, at this time, there is no UI for coupon code importation. Until we add this in, see [short-term workaround](#-import).

## To Add Coupons via the Dashboard

See: **Dashboard → s2Member → Pro Coupon Codes**

![2015-08-21_09-55-44](https://cloud.githubusercontent.com/assets/1563559/9415307/d50083ec-47ea-11e5-970d-9bfc1d03b6ba.png)

---

## To Import Coupon Codes via Import File {#-import}

### 1. Create this directory and file:
`/wp-content/mu-plugins/s2-new-coupons.php`

```php
<?php
add_action('init', function(){
  if(empty($_GET['s2_new_coupons']) || $_GET['s2_new_coupons'] !== '[secret key]')
    return; // Not a coupon addition request, or not a valid key.
  
  if(!is_file(ABSPATH.'s2-new-coupons.txt'))
    return; // Coupon file does not exist.
  
  $new_coupons = trim(file_get_contents(ABSPATH.'s2-new-coupons.txt'));
  $GLOBALS['WS_PLUGIN__']['s2member']['o']['pro_coupon_codes'] .= "\n".$new_coupons;
  update_option('ws_plugin__s2member_options', $GLOBALS['WS_PLUGIN__']['s2member']['o']);
  exit('New coupons added successfully!');
});
```

### 2. Change `[secret key]`

In the above code, change `[secret key]` to a random password that only you know.

### 3. Create a file containing your new coupon codes.

Format (one per line):

```text
code|discount|start(YYYY-MM-DD)~end(YYYY-MM-DD)|directive|singulars|users|max-uses
```

For additional details on each of these fields, see:
**Dashboard → s2Member → Pro Coupon Codes**

Example file: `/s2-new-coupons.txt`

```text
SAVE5PERCENT|5%
SAVE10|10
CHRISTMAS2015|25%|2015-12-01~2016-01-01
JULY4TH|40%|2015-07-04~2015-07-05|ta-only|1||1000
SAVE20|20|~2015-10-03|ta-only|||1000
```

### 4. Upload `/s2-new-coupons.txt`

Upload `/s2-new-coupons.txt` via FTP, to the root of your WordPress installation; i.e., in the same directory as `/wp-config.php`. Once you're done with the next step, you can remove this file. It is only needed for the import. After that, you can delete it if you'd like.

### 5. Access this URL in your browser to do the import.

```text
http://yoursite.com/?s2_new_coupons=[secret key]
```

You should see a message that reads:

> New coupons added successfully!

_Check your Dashboard to confirm the import worked as expected._

![2015-08-21_09-54-49](https://cloud.githubusercontent.com/assets/1563559/9415295/b7b4dd2e-47ea-11e5-9c43-989fd2a34841.png)
