---
title: Advanced Import/Export Tools
categories: tutorials
tags: import-export-tools
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/121
---

s2Member comes with two different Import/Export Tool flavors. Both flavors import/export in the [CSV (comma-separated values)](http://en.wikipedia.org/wiki/Comma-separated_values) format. However, they each construct CSV data differently. Advanced Import/Export Tools allow for a _much_ larger set of data to be manipulated. In this article I will discuss the Advanced Import/Export Tools. If you would like to learn more about the [default Simple Import/Export Tools](https://github.com/websharks/s2member-kb/issues/125) please [click here](https://github.com/websharks/s2member-kb/issues/125).

---

## Why "Advanced" Import/Export Tools?

### Advanced Import/Export Tools were Designed to:

<div class="li-margins"></div>

- Adhere to established standards when it comes to CSV files. Thereby making it easy for site owners to build and/or edit CSV files exported with s2Member in popular editors such as Numbers, MS Excel, OpenOffice Calc; or even just a simple text editor will do fine also. Some of these standards include things like not requiring any specific column order, obeying the standard for a double quote encapsulation, UTF-8 encoding, and allowing a CSV import file to contain multi-line field values.
- Allow for _all_ user-related data to be exported. Not just a subset with the most important details, but everything. This includes every database column in the `wp_users` table, all unique meta key rows from the `wp_usermeta` table, and all custom field values that a user has; which would be associated with any custom fields that a site owner configured with s2Member.
- Allow for all of the same data to be reimported using the same CSV format that s2Member delivers its Advanced Export Format in. Admittedly, this is a difficult task, because many of the values stored by WordPress (and other plugins) in the `wp_usermeta` table is actually a glob of serialized arrays. Thus, editing it all from a CSV file is challenging. s2Member eases some of this by converting a few _key_ data fields into JSON. More on this below.
- Allow for only some data fields to be imported, and any that are not imported are just left unchanged. In short, if you only want to update a user’s email address using the Import Tool, it should be as simple as this.

  ```text
  "ID", "user_email"
  "123", "user@example.com"
  ```
- Extend s2Member’s Import/Export functionality in ways that make it useful for other plugins too (i.e., to include data for everything, not just for fields related to s2Member itself). For instance, if you are running plugins that grant users points, awards, record their activity, or store any other useful information about each user; it is nice to export this data into CSV format and manipulate it in creative ways. It might even be helpful to use programs like MS Excel, OpenOffice, or Numbers to build charts and graphs. Of course it is also possible to edit the exported CSV data and then reimport it to achieve a mass update.

---

### A Few Quick Import Examples

---

#### Creating New Users

```text
"user_login", "user_email", "user_pass"
"johndoe", "john@example.com", "pasSw29914943!"
"maryjane", "mary@example.com", "uudkO90!!~!"
```

The order of your columns does not matter, so long as your CSV headers contain the proper field keys. The minimum required field keys to create a new user are: `user_login` and `user_email`. If you exclude `user_pass`, then a password will be generated automatically. However, that’s not a great idea, because s2Member’s import routine is silent. Customers are not emailed their password. It is up to you to get a password to your user. Or, you can just have them do a reset if you like.

---

#### Mass-Updating Existing Users

```text
"ID", "role", "ccaps", "meta_key__wp_s2member_subscr_gateway", "meta_key__wp_s2member_subscr_id", "meta_key__wp_s2member_subscr_cid"
"123", "s2member_level1", "music,videos", "paypal", "S-8234LSDK23KKSL", ""
"456", "s2member_level4", "games,music", "stripe", "sub_0290902234953ff", "cus_290242f65k44k3k3"
```

The order of your columns does not matter, so long as your CSV headers contain the proper field keys. Field keys are documented below. Please take a look at the four different data classifications below.

---

#### Forcing a Specific EOT Time

```text
"ID", "meta_key__wp_s2member_auto_eot_time"
"123", "1406281258"
"456", "1406222258"
```

EOT = End of Term. This is given as a UNIX timestamp. See details below regarding this Meta Field.

---

#### Adding Administrative Notes

```text
"ID", "meta_key__wp_s2member_notes"
"123", "I upgraded this account manually."
"456", "I contacted this customer. They left us a great review :-) The customer writes, ""amazing service, you guys are the best!"""
```

Note the use of `""` in this particular example (check the end of the last line). Each value is encapsulated by double quotes. Therefore, if you need to use a literal double quote you should escape it with another double quote; i.e., two double quotes inside an encapsulated field will result in one double quote being imported. If you don’t escape double quotes your CSV file will be corrupted.

_The use of a double quote as the escape char (and as the encapsulation) is a standard in most CSV file editors. I recommend Numbers on a Mac, MS Excel or OpenOffice Calc. If you use these applications you won’t need to worry about all of the rules._

---

## Four Data Classifications

Each line in s2Member’s Advanced Export File (which is the same format used for importation) consists of four data classifications. Understanding these classifications is important if you intend to fully understand what you're dealing with. The four classifications are: **User Fields**, **Capability Fields**, **Meta Fields**, and **Custom Fields**.

<div class="li-margins"></div>

1. **User Fields:** If you pull a quick export using the Advanced Export Tool, look at the first line of the exported CSV data. This line includes a list of CSV headers. While the order of your CSV data columns doesn’t matter, s2Member always spits out the **User Fields** first in export files, just to keep data classifications easy to understand. So, from left-to-right, you will find the following **User Field** headers. These correlate with the column names in your [`wp_users` database table](http://codex.wordpress.org/Database_Description#Table:_wp_users).

  ```text
  "ID","user_login","user_nicename","user_email","user_url","user_registered","user_activation_key","user_status","display_name"
  "1", "johndoe22", "johndoe22", "john@example.com", "http://john.example.com", "2014-04-04 17:06:50", "", "", "John Doe"
  ```

2. **Capability Fields:** This data classification consists of only three data columns. These include `role`, `ccaps`, and `meta_key__wp_capabilities`. While there are three, you can simplify this a bit and _only_ use `role` and `ccaps`. s2Member exports all three of these data columns, but when you import and/or mass update users; s2Member will give precedence to `role` and `ccaps` if they exist, and only look at `meta_key__wp_capabilities` if they don’t. Note that `meta_key__wp_capabilities` is a core WordPress meta field that is often difficult to deal with. It exists in this classification only for advanced site owners and developers that fully understand it. All others can simply use `role` and `ccaps`. s2Member will deal with the particulars automatically for you.

  ```text
  "role","ccaps"
  "s2member_level1", "music,videos"
  ```
    - **`role`** This can be a number (i.e., a Membership Level: `1`, `2`, `3`, `4`, etc) or any WordPress Role name (e.g., `subscriber`, `s2member_level1`, etc). See: [this KB article](https://github.com/websharks/s2member-kb/issues/122) for clarification.
    - **`ccaps`** This can be a comma-delimited list of Custom Capabilities the user should have. This is an advanced feature provided by s2Member. For further details, please watch [this video](https://github.com/websharks/s2member-kb/issues/73/) about how to extend s2Member beyond just Membership Levels.
3. **Meta Fields:** This is by far the largest data classification. The data columns in this classification correlate with those in your WordPress [`wp_usermeta` table](http://codex.wordpress.org/Database_Description#Table:_wp_usermeta). Every user in WordPress has metadata associated with their account. This metadata includes things like their Paid Subscr. ID, which payment gateway they completed checkout with, the time of their last payment, Custom Capability access times recorded by s2Member, a login counter, and much much more.

  WordPress itself uses metadata fields to store a user’s first name, last name, and a few other things. There can be many of these Meta Fields. Depending on the number of plugins that you run, you could even have hundreds of fields for each user. It is best to consult the documentation for each of your plugins to determine which metadata fields contain the data you would like to modify or better understand. In the context of this article I will only cover those which s2Member creates.

    **Meta Field Prefix**

    Each **Meta Field** (as seen in your CSV headers) should have the following prefix to place it into a **Meta Field** data classification. If you pull a quick export using s2Member’s Advanced Export Tool you will find several data columns like these. Notice the `meta_key__ prefix`? This is required for Meta Fields.
	 
    ```text
    "meta_key__wp_s2member_custom","meta_key__wp_s2member_subscr_id","meta_key__wp_s2member_subscr_baid","meta_key__wp_s2member_subscr_cid","meta_key__wp_s2member_subscr_gateway","meta_key__wp_s2member_registration_ip","meta_key__wp_s2member_ipn_signup_vars","meta_key__wp_s2member_paid_registration_times","meta_key__wp_s2member_access_cap_times","meta_key__wp_s2member_sp_references","meta_key__wp_s2member_last_status_scan","meta_key__wp_s2member_first_payment_txn_id","meta_key__wp_s2member_last_payment_time","meta_key__wp_s2member_auto_eot_time","meta_key__wp_s2member_file_download_access_arc","meta_key__wp_s2member_file_download_access_log"
        "www.example.com","9983JKSD03343","2098234DF","980234LSEFJ","stripe","123.456.789.0","{private: JSON object}","{""level"":1406275414,""level1"":1406275414}","{""1406275414.0001"":""level1""}","{private: JSON object}","1406271660","90823GAUI92323F","1406554660","1406271700","{private: JSON object}","{private: JSON object}"
    ```

    **s2Member-Related Meta Fields**

    _**Note:** each of these fields many not always be included in **your* export file. Typically you will have some and not others. s2Member only includes data that it actually has; i.e., that s2Member has found a reason to store. Therefore, if you find that your export file is missing any of these columns, it means s2Member has never collected that specific information for any of your users (e.g., if you are missing the download-related meta values, it might be because your site doesn’t use s2Member’s File Download functionality)._
	 
	 _It’s also worth mentioning that you can always import **any* data columns you like. Just because s2Member doesn’t export certain columns (because there is no data for them yet), you can still import whatever you want to. In fact, you can even import your own custom Meta Field columns if you so choose. Just give them a unique name, prefixed with `meta_key__` of course.

    - **`meta_key__wp_s2member_custom`** This is set for paying members. It should always start with your domain name. Optionally, followed by any pipe-delimited values that you need to collect in s2Member API Notifications. Example: `www.example.com`, or perhaps: `www.example.com|christmas-special`. **Tip:** this field is also editable in the s2Member UI. Click `[edit]` next to any user, then scroll down to edit this field for a particular user.
    - **`meta_key__wp_s2member_subscr_id`** s2Member sets this to the last paid Subscription or Transaction ID associated with a particular user. This is a key field in s2Member because it is the primary reference to a third-party payment gateway; i.e., it is what connects a particular user with a particular Subscription or Transaction by ID. **Tip:** this field is also editable in the s2Member UI. Click `[edit]` next to any user, then scroll down to edit this field for a particular user.
    - **`meta_key__wp_s2member_subscr_baid`** For internal use only. s2Member sets this to track Billing Agreement IDs on some payment gateways such as PayPal via Express Checkout, when/if a Billing Agreement is needed to complete checkout.
    - **`meta_key__wp_s2member_subscr_cid`** For internal use only. s2Member sets this to track Customer IDs on some payment gateways such as Stripe. In the case of Stripe, a customer will have both a Customer ID and also a Subscription or Transaction ID. **Tip:** when applicable, this field is also editable in the s2Member UI. Click `[edit]` next to any user, then scroll down to edit this field for a particular user.
    - **`meta_key__wp_s2member_subscr_gateway`** This associates the Paid Subscr. ID with a particular payment gateway. One of: `stripe`, `paypal`, `alipay`, `authnet`, `google`, `clickbank`, or `ccbill`.  **Tip:** this field is also editable in the s2Member UI. Click `[edit]` next to any user, then scroll down to edit this field for a particular user.
    - **`meta_key__wp_s2member_registration_ip`** s2Member sets this to the user’s original IP address used during registration/checkout (i.e., whenever an account is first established for the user). If this is empty, s2Member will fill it in automatically as soon as the customer logs in for the first time. Once this value is set it should not be changed again.
    - **`meta_key__wp_s2member_ipn_signup_vars`** s2Member keeps some data associated with the original core gateway IPN process. This can be quite complex, but it generally includes a summary of all transaction details associated with a customer’s first payment. This is presented in the export file as a JSON object to make it easier to edit if you deem necessary.
    - **`meta_key__wp_s2member_paid_registration_times`** This is presented in the export file as a JSON object to make it easier to edit if you deem necessary. See also: `s2member_access_cap_times`. Example: `{"level":1406275414,"level1":1406275414}`. Where the `level` key is the first payment time, period, at whatever Level. The other keys are a record of the first payment time at each specific Membership Level the customer has purchased. Obviously, not every customer will have paid for every Membership Level, so some keys will be empty for some users, but not for others. Every paying customer will have the `level` key however. The values here are UNIX timestamps.
    - **`meta_key__wp_s2member_access_cap_times`** Similar to `s2member_paid_registration_times`, but with much more information. This is presented in the export file as a JSON object to make it easier to edit if you deem necessary. s2Member records the time at which a customer gains or loses any s2Member-related capability within WordPress; whether it be paid for or not. Each key is a UNIX timestamp represented as a float with a precision of `4`. Each value is the capability after having the capability prefix `access_s2member_` stripped away. Example: `{"1406275414.0001":"level1", "-1406279999.0001":"level1"}`.
      
		_**Note:** A timestamp can also be negative, indicating the loss of a particular capability._
		
		Another example: `{"1406275414.0001":"level1", "1406275414.0002":"ccap_music"}`. A customer would have both of these times if they paid for `access_s2member_level1` and the Custom Capability `access_s2member_ccap_music`; even if they weren’t purchased together at the same exact time they would still have both of these, because they received both of these WordPress Capabilities at some point in time. That said, in this particular example, they _where_ purchased together in the same transaction obviously, because the times are nearly identical.
    - **`meta_key__wp_s2member_sp_references`** Systematic use only. This field is currently undocumented and unimportant at this time. This is presented in the export file as a JSON object. In the future s2Member may expose some additional functionality connected to this data whenever possible.
    - **`meta_key__wp_s2member_last_status_scan`** Systematic use only. This is a UNIX timestamp indicating the last time s2Member checked a particular customer’s status on the payment gateway associated with their account (if there is one). This is only relevant for certain payment gateways such as Authorize.Net. Most payment gateways notify s2Member and this field is not necessary in many cases. In fact, this is only needed for payment gateways where s2Member must poll for the latest details regarding the current status of a paid subscription plan.
    - **`meta_key__wp_s2member_first_payment_txn_id`** The is the first transaction ID associated with a customer’s subscription. **Note:** if the customer changes their subscription (e.g., upgrades or downgrades), this is reset each time they do so; i.e., this is the first payment transaction ID in a subscription plan. Or, if the customer’s purchase was a “Buy Now” transaction, this is simply a copy of the transaction ID for that purchase.
    - **`meta_key__wp_s2member_last_payment_time`** This is a UNIX timestamp indicating the time of the last payment s2Member was notified about for this customer. When a payment gateway charges a customer s2Member is notified behind-the-scenes, so this value is updated periodically over the course of a subscription plan. In the case of a Buy Now transaction, this is simply the original transaction time.
    - **`meta_key__wp_s2member_auto_eot_time`** EOT = End of Term. This is one of the _most_ useful fields when importing users from another/previous membership platform. If you fill this field in (it’s a UNIX timestamp), you are telling s2Member to terminate account access at that specific time. This is extremely helpful when you import customers from another membership platform into s2Member. For instance, if you don’t care to deal with the hassle of synchronizing all of the accounts (or if that just isn’t possible), you can simply flag each of your past account holders with an expiration time at which they will lose membership access in the new system. **Tip:** this field is also editable in the s2Member UI. Click `[edit]` next to any user, then scroll down to edit this field for a particular user.
    - **`meta_key__wp_s2member_file_download_access_arc`** Systematic use only. This is presented in the export file as a JSON object. It is rather complex. This is how s2Member tracks a user’s downloads over the lifetime of the account. This serves as a long-term archive for data that was originally collected by `s2member_file_download_access_log`.
    - **`meta_key__wp_s2member_file_download_access_log`** Systematic use only. This is presented in the export file as a JSON object. This is how s2Member keeps track of a user’s file downloads within the current period, based on your configuration of s2Member. If you wish to reset the download count for a particular user, you could simply erase this data; i.e., empty this column for a particular user. s2Member will recreate the data automatically, giving the user a fresh start.
    - **`meta_key__wp_s2member_last_login_time`** This is a UNIX timestamp indicating the time that a user’s last login session began (i.e., the last time they actually logged into your site). **Tip:** this field is also visible in the s2Member UI. In the list of Users within WordPress, this is an available column to show or hide.
    - **`meta_key__wp_s2member_login_counter`** This is a running counter which indicates the total number of times that a user has logged into their account at your site. **Tip:** this field is also visible in the s2Member UI. In the list of Users within WordPress, this is an available column to show or hide.
    - **`meta_key__wp_s2member_notes`** For administrative use only. These are administrative notes (if any) that you’ve kept, regarding a particular user. **Tip:** this field is also editable in the s2Member UI. Click `[edit]` next to any user, then scroll down to edit this field for a particular user.
4. **Custom Fields:** This data classification deals with Custom Registration/Profile Fields you configure with s2Member. See: **Dashboard → s2Member → General Options → Registration Profile Fields**. If you want to import Custom Fields, the easiest way to build your import file is to go ahead and configure those fields with s2Member in the Dashboard. Fill them in for at least one user and then pull an export file using s2Member’s Advanced Export Tool. If you look at the very end of any line (Custom Fields generally come last; though the order does not matter) you will find something like this:

    ```text
    "custom_field_key__company","custom_field_key__dept"
    "WebSharks","Web Design"
	 ```
	 
    Notice the `custom_field_key__ prefix` here? This is what pulls certain columns in your CSV file into the **Custom Fields** classification. The actual key names (e.g., `company` or `dept`; in this particular example) are based on the “Unique ID” value that you configure for a given field whenever you generate them in the Dashboard with s2Member. Again, the easiest way is just to generate some fields and pull an export to be sure that you’re on the right path before working hard to build your import file.

    **Custom Fields w/ Array Values**

    It is possible, with s2Member, to configure certain fields that collect more than a single value; e.g., a select menu that allows multiple sections, or a series of multiple checkboxes. If you configure any of these, s2Member uses a simple array in JSON format in your CSV column. So for instance, if you find that one of your Custom Field columns in the export file contains something like: `["Fishing", "Sports", "Computers"]`, this is three separate values that form a simple array in JSON format.
