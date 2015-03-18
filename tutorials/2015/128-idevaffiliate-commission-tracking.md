---
title: iDevAffiliate Commission Tracking
categories: tutorials
tags: api-notifications,api-tracking,idevaffiliate
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/128
---

[iDevAffiliate®](http://s2member.com/r/idev/) (an affiliate management portal) installs in just minutes and it can be integrated seamlessly with s2Member. We recommend iDevAffiliate (Standard Edition is fine) because of its proven track record and its ability to integrate with s2Member using a variety of techniques.

---

https://www.youtube.com/watch?v=RDtW-czrdT8

---

## Simple iDevAffiliate Integration (Has Limitations)

_**Important limitations:** Simple integration does NOT support recurring commission tracking or commission removal on refund/reversal events. Please use the “Advanced” integration instructions if you need things like this. “Advanced” integration is also more reliable overall (recommended)._

For Simple integration, see: **Dashboard → s2Member → API / Tracking**. Here it is possible to provide HTML code snippets (or even PHP code snippets); which will be processed and displayed in key areas of your site whenever a new Membership Signup takes place. Or, when a Membership Modification takes place. There are also slots for things like Custom Capability Sales and Specific Post/Page Sales. Please be sure to cover all of these events (i.e., all possible transaction types). Here is a list of the snippets you will need to perform a “Simple” integration.

### Inside your iDevAffiliate Dashboard

You will need to run your iDevAffiliate → Shopping Cart Integration Wizard. Please choose s2Member from the drop-down menu (or you can also use the Generic Tracking Pixel—that’s fine too).

![](http://cdn.websharks-inc.com/s2member/uploads/3-15-2013-2-09-13-PM.png)

Now (still in iDevAffiliate) please click “**View Integration Instructions**“ and grab your Hidden Image Tag. Take the code provided by iDevAffiliate and add Replacement Codes to your Hidden Image Tag. To save you some trouble, we’ve provided some examples below, one for each s2Member transaction type.

![](http://cdn.websharks-inc.com/s2member/uploads/3-15-2013-4-02-43-PM.png)

---

See: **Dashboard → s2Member® → API / Tracking Codes → Signup Tracking Codes**

Relevant Replacement Codes:

- `idev_saleamt=%%initial%%`
- `idev_ordernum=%%subscr_id%%`
- `profile=xxx` (defined in your URL by iDevAffiliate)

```html
<img src="http://www.example.com/idevaffiliate/sale.php?profile=xxx&idev_saleamt=%%initial%%&idev_ordernum=%%subscr_id%%" border="0" width="1" height="1" />
```

---

See: **Dashboard → s2Member → API / Tracking Codes → Modification Tracking Codes**

Relevant Replacement Codes:

- `idev_saleamt=%%initial%%`
- `idev_ordernum=%%subscr_id%%`
- `profile=xxx` (defined in your URL by iDevAffiliate)

```html
<img src="http://www.example.com/idevaffiliate/sale.php?profile=xxx&idev_saleamt=%%initial%%&idev_ordernum=%%subscr_id%%" border="0" width="1" height="1" />
```

See: **Dashboard → s2Member → API / Tracking Codes → Capability Tracking Codes**

Relevant Replacement Codes: 

- `idev_saleamt=%%amount%%`
- `idev_ordernum=%%txn_id%%`
- `profile=xxx` (defined in your URL by iDevAffiliate)

```html
<img src="http://www.example.com/idevaffiliate/sale.php?profile=xxx&idev_saleamt=%%amount%%&idev_ordernum=%%txn_id%%" border="0" width="1" height="1" />
```

See: **Dashboard → s2Member → API / Tracking Codes → Specific Post/Page Tracking Codes**

Relevant Replacement Codes:

- `idev_saleamt=%%amount%%`
- `idev_ordernum=%%txn_id%%`
- `profile=xxx` (defined in your URL by iDevAffiliate)

```html
<img src="http://www.example.com/idevaffiliate/sale.php?profile=xxx&idev_saleamt=%%amount%%&idev_ordernum=%%txn_id%%" border="0" width="1" height="1" />
```

---

## Advanced (and Recurring) Integration

It’s really not so hard; it’s just a little more sophisticated. The “Advanced” integration method uses s2Member’s event-driven API Notifications instead of it’s API Tracking Codes. s2Member’s API Notifications are event driven HTTP connections that occur silently behind-the-scene. Since they do _not_ depend upon a browser they are much more reliable. Everything is handled server-side. We don’t need to rely on cookie tracking, or on a browser loading up a 1px IMG tag properly. This “Advanced” method takes care of everything. You will _not_ need to perform a “Simple” integration (nor should you). That would only result in duplicate commission tracking. Please stick with one method of integration or the other. Please do _not_ try to mix these two methods together in any way.

### Step 1: Configuring Payment Notifications

Log into your iDevAffiliate Dashboard and go to: **Setup & Tools → Advanced Developer Tools → Custom Functions**

![](http://cdn.websharks-inc.com/s2member/uploads/3-15-2013-3-11-35-PM.png)

Choose: **cURL Tracking Pixel**

![](http://cdn.websharks-inc.com/s2member/uploads/3-15-2013-3-13-03-PM.png)

Copy the URL (and only the URL please):

![](http://cdn.websharks-inc.com/s2member/uploads/3-15-2013-3-57-43-PM.png)

Now, please take the URL provided by iDevAffiliate and add Replacement Codes made possible by s2Member. To save you some trouble we’ve provided some examples below, one for each important s2Member API Notification. Please follow these instructions carefully.

See: **Dashboard → s2Member → API / Notification → Payment Notification**

Relevant Replacement Codes:

- `idev_saleamt=%%amount%%`
- `idev_ordernum=%%txn_id%%`
- `idev_option_1=%%item_name%%`
- `idev_option_2=%%subscr_id%%`
- `idev_option_3=%%cv0%%`
- `ip_address=%%user_ip%%`

Place this URL (all on one line); as a URL that s2Member should notify when a payment occurs. This will award commissions for initial sales, and also for any recurring payments you receive.

```text
http://www.example.com/idevaffiliate/sale.php?idev_saleamt=%%amount%%&idev_ordernum=%%txn_id%%&idev_option_1=%%item_name%%&idev_option_2=%%subscr_id%%&idev_option_3=%%cv0%%&ip_address=%%user_ip%%
```

See: **Dashboard → s2Member → API / Notification → Specific Post/Page Sale**

Relevant Replacement Codes:

- `idev_saleamt=%%amount%%`
- `idev_ordernum=%%txn_id%%`
- `idev_option_1=%%item_name%%`
- `idev_option_2=%%txn_id%%`
- `idev_option_3=%%cv0%%`
- `ip_address=%%user_ip%%`

Place this URL (all on one line); as a URL that s2Member should notify when a Specific Post/Page sale occurs. It’s good to cover this important transaction type, should you decide to use this functionality now, or at some point in the future. This is targeted only to Specific Post/Page sales (nothing more).

```text
http://www.example.com/idevaffiliate/sale.php?idev_saleamt=%%amount%%&idev_ordernum=%%txn_id%%&idev_option_1=%%item_name%%&idev_option_2=%%txn_id%%&idev_option_3=%%cv0%%&ip_address=%%user_ip%%
```

### Step 2: Configuring Commission Terminations

Log into your iDevAffiliate Dashboard and go to: **Setup & Tools → Advanced Developer Tools → API Scripts**

![](http://cdn.websharks-inc.com/s2member/uploads/3-15-2013-3-39-32-PM.png)

Choose: Remove/Decline A Commission

![](http://cdn.websharks-inc.com/s2member/uploads/3-15-2013-3-40-46-PM.png)

Now, please take the URL provided by iDevAffiliate and add Replacement Codes made possible by s2Member®. To save you some trouble we’ve provided some examples below, one for each important s2Member API Notification. Please follow these instructions carefully.

![](http://cdn.websharks-inc.com/s2member/uploads/3-15-2013-3-53-34-PM.png)

See: **Dashboard → s2Member → API / Notification → Refund/Reversal**

Relevant Replacement Codes:

- `order_number=%%parent_txn_id%%`
- `secret=xxxxxxxxxx` (defined in your URL by iDevAffiliate)

Place this URL (all on one line); as a URL that s2Member should notify when a Refund/Reversal occurs. This will revoke a commission (if any) that you awarded an affiliate (the affiliate is notified via email).

```text
http://www.example.com/idevaffiliate/API/scripts/terminate_commission.php?secret=xxxxxxxxxx&order_number=%%parent_txn_id%%
```

See: **Dashboard → s2Member → API / Notification → Specific Post/Page (Refund/Reversal)**

Relevant Replacement Codes:

- `order_number=%%parent_txn_id%%`
- `secret=xxxxxxxxxx` (defined in your URL by iDevAffiliate)

Place this URL (all on one line); as a URL that s2Member should notify when a Refund/Reversal occurs. This will revoke a commission (if any) that you awarded an affiliate (the affiliate is notified via email).

```text
http://www.example.com/idevaffiliate/API/scripts/terminate_commission.php?secret=xxxxxxxxxx&order_number=%%parent_txn_id%%
```
