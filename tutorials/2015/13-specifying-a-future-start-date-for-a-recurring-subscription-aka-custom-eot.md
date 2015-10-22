---
title: Specifying a future start date for a recurring subscription (aka Custom EOT)
categories: tutorials
tags: eot-time, mu-plugins-hacks
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/13
---

_Note: The technique described below works with recurring subscriptions, i.e., subscriptions that utilize a payment gateway. If you want to use this technique on a Free Registration Form, see the note at the bottom of this article._

Let's say you have a site that offers a yearly membership and you're about to invite a bunch of people to sign up (or you have an existing membership base who you're going to invite to renew their subscription). However, you want all your members to start their recurring subscription on the same date.

For example, let's say today is January 1st, 2015 and you want everyone who signs up between now and February 1st to have their recurring annual subscription start on February 1st, 2015. That means their annual subscription will expire on February 1st, 2016.

You want to let them signup (or renew) between now and February 1st, but you don't want their annual subscription date to really _start_ until February 1st.

### Dynamic Trial Period

What we can do is utilize the s2Member Pro-Form "Trial Period". We will charge members for 1 year when they sign up, but we give them free access between now (when they sign up) and February 1st. 

The trick is calculating how many days exist between now (when the member is signing up / renewing) and the "start" of our annual cycle (February 1st, in this example). To do that, we use the following PHP code. You'll need to place this code inside your Post / Page, right above your Pro-Form. 

_Note: You will need to be running the [ezPHP](http://wordpress.org/plugins/ezphp/) plugin to allow running PHP code directly inside WordPress Posts / Pages._

```php
<?php
// Change these to the date you want the annual cycle to officially start 
$cycle_start_year = '2015';
$cycle_start_month = '2';
$cycle_start_day = '1';

$cdate = mktime(0, 0, 0, $cycle_start_month, $cycle_start_day, $cycle_start_year);
$today = time();
$difference = $cdate - $today;
if ($difference < 0) { $difference = 0; }
$trial_days = floor($difference/60/60/24); // Calculated number of days until yearly cycle should start
?>
```

Be sure to change the `$cycle_start_year`, `$cycle_start_month`, and `$cycle_start_day` values to the appropriate date.

Now, we just need to modify the Pro-Form shortcode to include a dynamic Trial Period attribute (`tp=""`). You'll do that by setting it to `tp="<?php echo $trial_days; ?>"`. Be sure that the Trial Term is set to Days (`tt="D"`) and if you want to make this dynamic trial period free (i.e., you only want to charge the member for 1 year, not 1 year + some amount for the trial period), then set the Trial Amount to zero (`ta="0"`).

_For more details about the various Pro-Form shortcode attributes, see **Dashboard → s2Member (Pro) → PayPal Pro-Forms → Shortcode Attributes (Explained)**._

That's it! Now when someone signs up, they will be charged for 1 year of access and they will be granted access immediately upon successful payment. However, their subscription won't actually expire until 1 year from the "cycle start" date that you defined in the PHP code.

---

### Complete Example PayPal Pro-Form with Dynamic Trial Amount

```php
<?php
// Change these to the date you want the annual cycle to officially start 
$cycle_start_year = '2015';
$cycle_start_month = '2';
$cycle_start_day = '1';

$cdate = mktime(0, 0, 0, $cycle_start_month, $cycle_start_day, $cycle_start_year);
$today = time();
$difference = $cdate - $today;
if ($difference < 0) { $difference = 0; }
$trial_days = floor($difference/60/60/24); // Calculated number of days until yearly cycle should start
?>

[s2Member-Pro-PayPal-Form level="1" ccaps="" desc="$100.00 USD / Yearly (recurring charge, for ongoing access)" ps="paypal" lc="" cc="USD" dg="0" ns="1" custom="example.com" ta="0" tp="<?php echo $trial_days; ?>" tt="D" ra="1.00" rp="1" rt="Y" rr="1" rrt="" rra="2" accept="paypal" accept_via_paypal="paypal" coupon="" accept_coupons="0" default_country_code="" captcha="0" /]
```

---

### Dynamic EOT for Free Registration Forms

If you want to use the technique described in the article above to create a dynamic EOT for a free subscription, you'd first generate a Free Subscription Form (e.g., **Dashboard → s2Member (Pro) → PayPal Pro-Forms → Free Registration Form**) and then modify the shortcode as described above (note the `tp=""` attribute modified to use the dynamic days):

```text
[s2Member-Pro-PayPal-Form register="1" level="0" ccaps="" desc="Signup now, it's Free!" custom="example.com" tp="<?php echo $trial_days; ?>" tt="D" captcha="clean" /]
```

This creates a Free Subscription form that results in the account expiring (EOT) after `$trial_days`.

### Always use the current year for `$cycle_start_year`

If you always want the cycle start year to be the current year, you can modify the above code as follows:

```php
$cycle_start_year = date('Y'); // Always use the current year
```

### Relative Date for the Cycle Start

This example shows how to use the infamous [strtotime()](http://php.net/manual/en/function.strtotime.php) function in PHP to build dates that are relative; i.e., cycle begins on the first day of the next month in this case.

```php
$cycle_start_year = date('Y', strtotime('first day of next month'));
$cycle_start_month = date('n', strtotime('first day of next month'));
$cycle_start_day = date('j', strtotime('first day of next month'));
```
