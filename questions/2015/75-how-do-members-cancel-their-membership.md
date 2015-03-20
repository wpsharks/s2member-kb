---
title: How Do Members Cancel Their Membership?
categories: questions
tags: eot-time, pro-forms, manual-intervention
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/75
toc-enable: off
---

Members can cancel their membership using a Billing Cancellation Form that you can generate for the Payment Gateway you're using (e.g., **s2Member → Stripe Pro-Forms → Stripe Billing Cancellation Forms**). When a subscribed member uses the form, their recurring subscription will be canceled and their account will be downgraded as per your Automatic EOT Behavior settings (**s2Member → Stripe Options → Automatic EOT Behavior**). 

Canceling a membership generally implies that access is revoked, whether that be access to their account entirely (i.e., preventing a member from logging in) or revoking access to specific content while still allowing access to the account (i.e., a member can login, but they can't access restricted content).

We recommend that you always start protecting content with a **Level 1** restriction and that you reserve **Level 0 / Subscriber** for members who should not have any access to protected content. That way a member can be downgraded to **Level 0 / Subscriber** and keep their account, while simultaneously revoking their access to any content protected at **Level 1** or higher.

Allowing a member to keep their account on your site has the added benefit of allowing them to easily renew their membership at some point in the future, as opposed to having to create a new account. This also allows you to offer special discounted membership to those members who previously purchased access.

Note that if you're running a free membership system, you can still utilize this system of reserving **Level 1+** for active members and reserving **Level 0 / Subscriber** for inactive members. This allows you to 'deactivate' a member without deleting their account entirely.

### How Do Paid Members Cancel Their Membership?

To offer your paying subscribers the option to cancel their subscription, you can create a "Cancel Membership" page and then place the Billing Cancellation Form (e.g., **s2Member → Stripe Pro-Forms → Stripe Billing Cancellation Forms**) on that page.

![2015-03-20_15-23-08](https://cloud.githubusercontent.com/assets/53005/6759284/3d007604-cf15-11e4-9c5c-f673a90ec415.png)

You can then link to the "Cancel Membership" page from their "My Account" page (i.e., the Login Welcome Page). When a member cancels their membership using the form, their recurring subscription will be canceled on the payment gateway and their account will be downgraded as per your Automatic EOT Behavior settings (**s2Member → Stripe Options → Automatic EOT Behavior**). 

### How Do Free Members Cancel Their Membership?

Free memberships can be cancelled (so-to-speak), by setting an EOT Time on the account (edit the users account and set a date/time you want the account to expire in the `Automatic EOT Time` field). When the EOT Time arrives, the account will be "downgraded" as per your Automatic EOT Behavior settings (**s2Member → Stripe Options → Automatic EOT Behavior**).

![2015-03-20_15-25-56](https://cloud.githubusercontent.com/assets/53005/6759400/234b42b0-cf16-11e4-913c-87c47dbc1022.png)

Note that this assumes that you're using **Level 1+** for active members and reserving **Level 0 / Subscriber** for inactive members. If you were using **Level 0 / Subscriber** for active members, then the only way to "downgrade" or "cancel" the members account is to delete it entirely from the system.

In short, **Level 0 / Subscriber** is as low as you can go. If you want to "cancel" free members, content should be protected at **Level 1** or higher, so that demoting a free member back to **Level 0 / Subscriber** will effectively "cancel" their access.

As an alternative to setting an EOT Time, you can also "cancel" a members access by manually changing their Role from **Level 1+** to **Level 0 / Subscriber** and then saving the changes to their account.

![2015-03-20_15-31-36](https://cloud.githubusercontent.com/assets/53005/6759411/38ffa97a-cf16-11e4-8d82-5653d762a5d0.png)
