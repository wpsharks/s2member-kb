---
title: BuddyPress profile fields or s2Member profile fields? Which should I choose?
categories: questions
tags: buddypress, registration-profile-fields
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/220
toc-enable: false
---

You can create custom profile fields with BuddyPress. Or, you can create custom profile fields with s2Member. Or, you can use a mix of both. s2Member adapts to any of these use cases. How you choose to create profile fields is entirely up to you. There are advantages and disadvantages in both cases.

## Advantages vs. Disadvantages

Really, the only downside to using BuddyPress profile fields, is that these are not currently included in the checkout forms powered by s2Member; i.e., s2Member Pro-Forms don't display fields you created with BuddyPress. However, if you create s2Member profile fields, we integrate these into BuddyPress profiles (public views and profile editing forms) for you automatically.

### So what it comes down to is this...

- If it's truly a "profile" field and not needed during checkout/registration, use BuddyPress (better).
- If it's something that should be introduced in both the profile and during registration/checkout (and you're using s2Member Pro-Forms for registration/checkout); create those fields with s2Member; i.e., use a mix of both when that makes more sense.
- If you want to make it possible for all fields to be shown during registration/checkout, use only s2Member profile fields; as s2Member integrates with BuddyPress. BuddyPress does not integrate with s2Member in the same way.
