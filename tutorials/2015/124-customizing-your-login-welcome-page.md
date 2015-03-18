---
title: Customizing your Login Welcome Page
categories: tutorials
tags: login-welcome-page
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/124
---

## What Is The Login Welcome Page?

This is the Page where a user (anyone who can log into your site) is redirected to upon logging in. By default, s2Member has just _one_ Login Welcome Page. A **Login Welcome Page** (in the context of s2Member) is a Page you create in WordPress (like any other Page), and then you designate it as your Login Welcome Page when configuring s2Member. This can be configured (or reconfigured) from: **Dashboard → s2Member → General Options → Login Welcome Page**

---

## The Purpose Of A Login Welcome Page

The Login Welcome Page that you configure with s2Member will serve as a customer’s “**My Account**” page, or something similar. Most site owners will use this Page to introduce links to important areas of their site so that users can gain access to whatever it is you’ve sold them. This makes it easy for a customer to find what they’ve purchased and to locate information associated with their account.

Some site owners will also insert the `[s2Member-Profile /]` shortcode into this Page. Or, they might choose to insert a link that takes the user to a separate Page which contains the `[s2Member-Profile /]` shortcode. The `[s2Member-Profile /]` shortcode produces a Profile Editing Form; making it possible for a customer to update their profile (i.e., change their name, email address, any custom fields you’ve configured, etc). Please see: **Dashboard → s2Member → General Options → Profile Modifications** to learn more about this shortcode.

---

## Dealing with “Conditions” On Your Login Welcome Page

Obviously, not every customer will have access to the same content/services you offer. Maybe you’ve restricted content with s2Member in different ways, at different Membership Levels, or with different Custom Capability packages. If someone logs into your site as a Free Subscriber you might want to show a Free Subscriber something _different_ than you show a Member at Level 1. **Why?** Because, if you always display links to content that requires Membership Level 1, but it’s a Free Subscriber who logs in, those links will _not_ work for them. So let’s _not_ show those links to a Free Subscriber. That would be a more sophisticated approach in most cases.

In order to accomplish this, site owners will typically use [Simple Shortcode Conditionals](https://github.com/websharks/s2member-kb/issues/119) in their Login Welcome Page so they can tailor the content/links displayed on the Login Welcome Page to specific groups of users (e.g., Free Subscribers, Members at Level 1, Members at Level 2, Members with a particular Custom Capability, etc). You can learn more about Simple Shortcode Conditionals [here](https://github.com/websharks/s2member-kb/issues/119). See also: **Dashboard → s2Member → API / Scripting → Simple/Shortcode Conditionals**

---

## Using A Special Redirection URL — Dynamic Login Welcome Page(s)

Sometimes Simple Shortcode Conditionals are not enough to accomplish everything you need. For instance, you might find the need to have an entirely different Login Welcome Page for each group of users that you have. Or, maybe an entirely different Login Welcome Page for every user (based on their User ID in WordPress, or their username). This is possible with s2Member. I will explain briefly here.

The first thing you’ll want to do is take a look at this section of your Dashboard. See: **Dashboard → s2Member → General Options → Login Welcome Page → Special Redirection URL**. Instead of designating a single Page in WordPress as your Login Welcome Page, you can define a specific URL instead. And, s2Member supports a few Replacement Codes here; making it possible to formulate a Special Redirection URL dynamically.

**Replacement Codes available here include:**

- `%%current_user_nicename%%` Nicename; generally used in URLs as a slug.
- `%%current_user_login%%` The user's login; i.e., their username.
- `%%current_user_level%%` The user's Membership Level.
- `%%current_user_id%%` The user's unique ID in WordPress.
- `%%current_user_role%%` The user's WordPress Role; see: [Roles/Capabilities](https://github.com/websharks/s2member-kb/issues/122).
- `%%current_user_ccaps%%` A hyphen-delimited list of all Custom Capabilities the user has access to.
- `%%current_user_logins%%` Number of times a user has logged into your site.

So this makes it possible to construct a Login Welcome Page URL dynamically, based on whatever Replacement Code values that you make a part of the final URL. Once you set up this Special Redirection URL, you can simply create multiple Pages in WordPress to accommodate all possibilities that you foresee, based on the dynamic nature of your Special Redirection URL.

---

### Example 1 (Based on Username)

If I create a Special Redirection URL like this:

```text
http://www.example.com/%%current_user_login%%-account-page
```

I might create the following Pages in WordPress to accommodate each username that logs into the site.

```text
http://www.example.com/johndoe22-account-page
http://www.example.com/maryjane-account-page
http://www.example.com/billybob-account-page
http://www.example.com/acmecorp-account-page
...and so on, for each username...
```

---

### Example 2 (Based on Membership Level)

If I create a Special Redirection URL like this:

```text
http://www.example.com/%%current_user_level%%-account-page
```

I might create the following Pages in WordPress to accommodate each Membership Level.

```text
http://www.example.com/0-account-page
http://www.example.com/1-account-page
http://www.example.com/2-account-page
http://www.example.com/3-account-page
http://www.example.com/4-account-page
```

---

## One-Time Offers Upon Login (requires s2Member Pro)

If you’re running s2Member Pro you can change things up a bit, based on the number of times a user has logged into your site in the past. **One-Time Offers (Upon Login)** is an s2Member Pro feature that can be extremely powerful, because many site owners like to promote special offers that provide discounts on account upgrades. Or, they might want to issue a password reset reminder once in awhile as a customer logs in. Some site owners might like to notify a customer about something important on their very first login, but _only_ on their first login. One-Time Offers make all of these things possible.

When a user logs in, depending on how many times they’ve logged-in in the past, they might be redirected to different URLs that you configure ahead of time. See: **Dashboard → s2Member → General Options → One-Time Offers (Upon Login)**. Just like a Special Redirection URL (discussed above) s2Member supports several Replacement Codes here too.

**Replacement Codes available here include:**

- `%%current_user_nicename%%` Nicename; generally used in URLs as a slug.
- `%%current_user_login%%` The user's login; i.e., their username.
- `%%current_user_level%%` The user's Membership Level.
- `%%current_user_id%%` The user's unique ID in WordPress.
- `%%current_user_role%%` The user's WordPress Role; see: [Roles/Capabilities](https://github.com/websharks/s2member-kb/issues/122).
- `%%current_user_ccaps%%` A hyphen-delimited list of all Custom Capabilities the user has access to.
- `%%current_user_logins%%` Number of times a user has logged into your site.

_It’s important to realize that One-Time Offers (Upon Login) are a supplement to your existing Login Welcome Page configuration. They add an additional layer of control over login redirections that occur on your site, and they will work together with any of the methodologies that I’m discussing in this article._

---

## Login Welcome Page Templates (To Help Get You Started)

As part of this article, I will include a few Login Welcome Page examples. These might serve as Login Welcome Page templates for some of you that need assistance. Just paste a code sample into a WordPress Page from your Dashboard :-) 

These examples include several things that I went over in this article, but they _also_ include examples of the `[s2Get constant="" /]` shortcode, which I did _not_ go over in this article. If you need help understanding any of this, please see: **Dashboard → s2Member → API / Scripting** for a list of advanced functionalities provided by s2Member—with respect to shortcodes and scripting.

---

### Only The Essentials (A Bare Bones Example)

```html
<h4>Welcome <strong>[s2Get constant="S2MEMBER_CURRENT_USER_DISPLAY_NAME" /]</strong><em>!</em></h4>
<h4>You can edit your profile using the form below.</h4>
[s2Member-Profile /]
```

---

### Additional Details (Slightly Advanced)

```html
<h4>Welcome <strong>[s2Get constant="S2MEMBER_CURRENT_USER_DISPLAY_NAME" /]</strong><em>!</em></h4>
<h4>Your Account Details:</h4>

Membership Level: [s2Get constant="S2MEMBER_CURRENT_USER_ACCESS_LEVEL" /]
Your are a:  [s2Get constant="S2MEMBER_CURRENT_USER_ACCESS_LABEL" /]

Your User ID is: [s2Get constant="S2MEMBER_CURRENT_USER_ID" /]
Your Username is: [s2Get constant="S2MEMBER_CURRENT_USER_LOGIN" /]
Your Email Address is: [s2Get constant="S2MEMBER_CURRENT_USER_EMAIL" /]

Your First Name is: [s2Get constant="S2MEMBER_CURRENT_USER_FIRST_NAME" /]
Your Last Name is: [s2Get constant="S2MEMBER_CURRENT_USER_LAST_NAME" /]

You have logged in [s2Get constant="S2MEMBER_CURRENT_USER_LOGIN_COUNTER" /] times.
Your IP Address is: [s2Get constant="S2MEMBER_CURRENT_USER_IP" /]

Custom Registration/Profile Field: [s2Get user_field="custom_field_id" /]
See: s2Member® -> General Options -> Registration/Profile Fields

<h4>You can edit your profile using the form below.</h4>
[s2Member-Profile /]
```

---

### Based On Role Of Current User (Slightly Advanced)

```html
<h4>Welcome <strong>[s2Get constant="S2MEMBER_CURRENT_USER_DISPLAY_NAME" /]</strong><em>!</em></h4>

[s2If current_user_is(subscriber)]
	You are a Free Subscriber.
[/s2If]

[s2If current_user_is(s2member_level1)]
	You are a Member @ Level #1.
[/s2If]

[s2If current_user_is(s2member_level2)]
	You are a Member @ Level #2.
[/s2If]

[s2If current_user_is(s2member_level3)]
	You are a Member @ Level #3.
[/s2If]

[s2If current_user_is(s2member_level4)]
	You are a Member @ Level #4.
[/s2If]

[s2If current_user_is(administrator)]
	You are an Administrator.
[/s2If]

<h4>You can edit your profile using the form below.</h4>
[s2Member-Profile /]
```

---

### Based On Capabilities Of Current User (Slightly Advanced)

```html
<h4>Welcome <strong>[s2Get constant="S2MEMBER_CURRENT_USER_DISPLAY_NAME" /]</strong><em>!</em></h4>

[s2If current_user_can(access_s2member_level1)]
    Content for Members who are logged in with an s2Member Level >= 1.
[/s2If]

[s2If current_user_cannot(access_s2member_level1)]
    Content for Free Subscribers.
[/s2If]

<h4>You can edit your profile using the form below.</h4>
[s2Member-Profile /]
```
