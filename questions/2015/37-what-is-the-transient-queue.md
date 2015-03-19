---
title: What is the "Transient Queue"?
categories: questions
tags: troubleshooting, log-files-debug
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/37
---

If you see a log entry like the following in your `gateway-core-ipn.log`:

```text
  's2member_log' => 
  array (
    0 => 'IPN received on: Tue Jan 13, 2015 1:38:55 pm UTC',
    1 => 's2Member POST vars verified with a Proxy Key',
    2 => 's2Member originating domain (`$_SERVER["HTTP_HOST"]`) validated.',
    3 => 's2Member `txn_type` identified as ( `web_accept|subscr_signup` ).',
    4 => 's2Member `txn_type` identified as ( `web_accept|subscr_signup` ) w/o update vars.',
    5 => 'Signup Confirmation Email sent to: "Example" <example@example.com>.',
    6 => 'Storing `payment` for Subscription via ( `web_accept` ).',
    7 => 'Creating an IPN response for `subscr_payment`. This will go into a Transient Queue; and be processed during registration.',
    8 => 'Storing IPN signup vars into a Transient Queue. These will be processed on registration.',
  ),
```

This happens whenever a "Button" integration is used, where the registration occurs _after_ the payment is received. In this case, s2Member stores the payment details until after the paid registration occurs shortly thereafter. This way s2Member can process the payment notification and connect that to a WP User ID so that it can be stored properly with the user's account in WordPress. 

So this log entry is a success, just a different sort of success. One where I would expect to see another IPN shortly after this, where s2Member fed its own IPN processor with the payment IPN during registration. During registration, s2Member will pretend to be PayPal and submit the IPN again; i.e., now that it has a user ID to associate with it.

---

## Registration Access Link sent after signup

```text
    5 => 'Signup Confirmation Email sent to: "Example" <example@example.com>.',
```

This is where the user gets the email that contains the special registration link, and they use this link to complete registration at the Level they paid for. During this registration, s2Member sees that it has a payment IPN in the transient queue, and we should see an IPN entry that processes the payment at this time.

See also: **Dashboard → s2Member → PayPal Options → Signup Confirmation Email**

---

## What If I'm using Pro-Forms and not using Buttons?

In the case of a Pro-Form, this "Transient Queue" would not occur. With a Pro-Form, the registration actually occurs at the same time as the payment. (Technically, it occurs before the IPN processing takes place in the case of a Pro-Form.) So if you saw the "Transient Queue" message in the IPN log and you're using Pro-Forms, that would be an indication that at least one of your shortcodes, somewhere on your site, is for a payment button instead of for a Pro-Form.

---

## Customers report successful payment, but they don't receive access; why?

Best guess here, would be that instructions on the site are not clear enough, or they are misleading in some way. 

A customer completing checkout through a Button is returned (by default) to the registration page, where they can complete registration and gain access as a next step after checkout. 

If the customer misses this registration somehow, then an email with a link to complete registration is also there as a fallback in this scenario (i.e., when using payment Buttons, the user is both returned to a registration page _and_ receives an email with a link to the registration page, just in case they somehow miss, or forget to fill out, the registration form after payment). 

Following the link in the email to complete registration would provide the access they need. A site owner can also generate a Registration Access Link for a customer reporting that they did not receive this email, or if they missed the registration step after checkout. See: **Dashboard → s2Member → PayPal Button → Registration Access Links**

---

## How can I stop people from creating Free Subscriber Accounts?

If you have **Open Registration** enabled on the site and your customers somehow miss the final step where they are expected to register for paid access, they might instead return to the home page of the site and click through to register like a free user, completely missing the paid access cookies provided after checkout and through the link in the email.

What can increase the odds of this occurring, is when the site has been integrated with something like ccBill, where real-time processing after checkout is not possible. In the case of ccBill (and this can happen in rare cases with ClickBank and PayPal Standard too), the email becomes the only way to get registered with paid access. So again, if the customer does not follow the email and instead uses the **Open Registration** form like anyone else, they end up with an account that is not what they actually paid for.

Solution is to close Open Registration to avoid confusion (see: **Dashboard → s2Member → General Options → Open Registration**). Or, to move to Pro-Forms. Or, just be very careful to provide clearer instructions after checkout, either before checkout begins, or through the application of a custom `success=""` URL (see: **Dashboard → s2Member → PayPal Buttons → Shortcode Attributes (Explained)**) where you redirect new customers after payment to a special page where you give customers some warning about this possible confusion and help instruct them how to complete the signup process.