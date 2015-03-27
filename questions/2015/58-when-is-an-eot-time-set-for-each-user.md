---
title: When is an EOT Time set for each user?
categories: questions
tags: eot-time
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/58
---

## EOT Time is Not Always Present in WordPress

The EOT field is not always present, because sometimes this is controlled by the underlying Subscription Profile; i.e., on the payment gateway side. The EOT field is only filled if s2Member needs to control this without the use of a Subscription Profile, or when an EOT has actually occurred against a Subscription Profile on the payment gateway side.

## What is a Subscription Profile?

It's sometimes referred to as a Recurring Profile, Billing Profile, Automatic Recurring Billing Profile (ARB), or just as a "Subscription". The name varies from one payment gateway to another. The important thing to note, is that a "Subscription Profile" is used any time a charge needs to occur on a specific date. Either in regular intervals, or after an initial/trial period has ended. s2Member does not deal with payment scheduling on its own, it depends upon functionality provided by your payment gateway; i.e., on a Subscription Profile.

For this reason, anytime there is a "Subscription Profile" used, s2Member leaves the EOT field empty. In such a scenario, the EOT is triggered by events that occur against the Subscription Profile.

## Cases where s2Member Sets the EOT on Checkout, Immediately

- The subscription is on a fixed term and there is no trial period; i.e. there is no Subscription Profile needed. s2Member has exclusive control over the EOT, because the Button/Form that you generated does not require a Subscription Profile to be used on the payment gateway side.

  In this scenario, s2Member sets an EOT so that access can be removed at a specific time in the future. With fixed-term access, this is always known right from the beginning; e.g., 1 Year Membership, 2 Year Membership, etc. — both non-recurring, and the charge is taken immediately upon completing checkout.

   For example, when you generate a Button/Form with s2Member, if the option that you choose is not labeled, "Subscription" then a Subscription Profile is not necessary; i.e., it will be a "Buy Now" Button or Pro Form. The charge takes place immediately; just one time. In other words, if the purchase provides fixed-term access and the transaction is "Buy Now"; an EOT is set immediately, because there is just one immediate payment (no Subscription Profile), and the end date is known right from the beginning. 

  _NOTE: If a purchase provides lifetime access; there is no EOT Time whatsoever._

## Cases where s2Member Sets the EOT Later, as Necessary

- Any time there is a Subscription Profile used; noting that if there is a trial associated with the subscription, even if the subscription itself is on a fixed term, a Subscription Profile is still used. This allows s2Member to set a future start date for billing. Billing may, at times, occur only once, but the EOT is not set until billing is actually supposed to stop. In the case of a recurring subscription, this may not occur until payments start to fail, the user cancels, or until the `rrt` Regular Recurring Times has been reached and the subscription should end naturally.
- A refund occurs and your configuration states that this should trigger an EOT.
- A chargeback occurs and your configuration states that this should trigger an EOT.
- You enter an EOT manually by editing the user's account in WordPress.

## What happens if an EOT was already set and the user "renews"?

There are three possible scenarios here:

1. If your EOT Behavior option is set to Auto-Extend (like we have at ZenCache.com) and the new purchase is for fixed-term access, the existing EOT Time (if it is a future date) will be automatically extended with the amount of time that you are now paying for. For instance, if a site owner has 3 years of support at ZC and they purchase another year; they now have a total of 4 years.

2. Or, if your EOT Behavior options have Auto-Extend off, the old time is erased and replaced by the new time associated with a new fixed-term purchase.

3. The new purchase is a "Subscription" (i.e., not fixed-term). In this case, s2Member will simply erase the old EOT Time and wait for a new one to occur. No matter what Auto-Extend is set to.
