---
title: Double Opt-In Checkbox Config.
categories: tutorials
tags: api-list-servers
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/179
---

## MailChimp, AWeber, and GetResponse

See: **Dashboard → s2Member → API / List Servers**

In this article I'll discuss the Double Opt-In Checkbox that can be configured to display in registration/checkout forms. How to configure it, what's possible, etc.

See: **Dashboard → s2Member → API / List Servers → Double Opt-In Checkbox**

---

Ordinarily, the checkbox is presented to a potential subscriber in order to get their permission to send them a confirmation email. And, so they are prepared for it to come. However, it can also be disabled completely.

---

![](http://cdn.websharks-inc.com/s2member/uploads/2014/01/Selection_112.png)

---

## Double Opt-In Checbox Options

All of these options are presented under the assumption that your list server will require a double opt-in procedure. It’s very unusual that a list server would agree to allowing a single opt-in from my experience. If you can swing it though (and there are times when this is possible), then the checkbox would still be used (recommended); because it would serve as the single opt-in.

---

#### Yes – the box must be checked (checked by default). {.no-b-margin}
#### Yes – the box must be checked (unchecked by default). {.no-t-margin}

Both of these options mean the same thing. The only difference is that the box is either checked by default (or not). Both of these settings tell s2Member that it _should_ connect with your list server if the box is checked.

Both of these options also assume that this connection (via the API) is going to result in a confirmation email being sent to the potential subscriber. If you find a way to circumvent this (e.g., by getting permission from your list server to do so), then this simply means that a subscriber would be added to the list (with no confirmation) if the box is checked.

---

#### No, do not display (or require) the checkbox.

This tells s2Member that your list server integration is not dependent upon the checkbox. In short, all new registrants receive the confirmation email, because the checkbox is actually not in use at all. So checked or unchecked; it does not matter; the checkbox is not even being used. In a case like this, there is only a single opt-in (the confirmation email). If you find a way to circumvent the confirmation email (by getting permission from your list server to do so), this would be a blind subscription (no opt-in at all).

---

#### UPDATE Jun 2016 (Blind Subscription)

With MailChimp it is now possible to avoid the confirmation email. Assuming that you (and MailChimp) find this to be an acceptable practice for your site. You can disable the confirmation email with s2Member by creating an MU plugin file.

Create: `/wp-content/mu-plugins/s2-mc-hacks.php`

```php
<?php
add_filter('ws_plugin__s2member_mailchimp_double_optin', '__return_false');
```

_This disables the confirmation email altogether._

##### There are two ways to use this:

###### *1.* With the Opt-In Checkbox Enabled

###### e.g., Yes – the box must be checked (checked by default). {.no-b-margin}
###### e.g., Yes – the box must be checked (unchecked by default). {.no-t-margin}

With either of these options you are showing the checkbox. If the box is checked when the form is submitted, the user is subscribed w/o a confirmation email. This is considered to be a single opt-in, but without email confirmation. All you got was the checkbox, and if the checkbox was checked by default that's even less proof that a user _actually_ intended to subscribe. Therefore, this methodology (while possible), is NOT recommended. You could upset your subscribers and/or MailChimp.

###### *2.* With the Opt-In Checkbox Disabled

###### e.g., No, do not display (or require) the checkbox.

In this case, the user is _always_ subscribed when they submit the form, and they are subscribed without any knowledge of it occurring at all. NOT recommended! You will almost certainly upset your subscribers and/or MailChimp.
