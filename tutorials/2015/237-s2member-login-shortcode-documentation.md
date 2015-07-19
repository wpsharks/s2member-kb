---
title: '[s2Member-Login /] Shortcode Documentation'
categories: tutorials
tags: shortcodes, s2member-login-shortcode
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/237
---

The `[s2Member-Login /]` shortcode makes it possible for you to introduce a login form in any Post/Page that you create with WordPress. It can also double as a way to display a profile summary whenever a user is already logged-in (optional).

**NOTE: This shortcode requires s2Member Pro.**

## `[s2Member-Login /]` Shortcode Example 1

```wpsc
[s2Member-Login /]
```

_Displays a simple login box. If the user is already logged-in, it displays nothing._

---

## `[s2Member-Login /]` Shortcode Example 2

```wpsc
[s2Member-Login login_redirect="http://example.com/account/" /]
```

_Upon logging in, the user is redirected immediately to: `http://example.com/account/`_

---

## `[s2Member-Login /]` Shortcode Example 3

```wpsc
[s2Member-Login show_summary_if_logged_in="1" /]
```

_If the user is already logged in, a profile summary is displayed instead, including their avatar._

---

## `[s2Member-Login /]` Attributes (Explained)

---

### When Not Logged In Yet

<div class="li-margins"></div>

- `title="Membership Login"` Title when _not_ logged in. Defaults to `Membership Login`. You can set this to an empty string if you want to exclude the title.

-  `signup_url="%%automatic%%"` Default value is `%%automatic%%`, which creates a "Signup Now" link which leads to the Membership Options Page that you configured with s2Member. Or, you can enter a full Signup URL of your own. If you set this to an empty string it will not be shown.

  _Note: If this is `%%automatic%%` and the current user has just completed a "Button" transaction and is now able to register for paid access, this dynamically changes to a Registration Access Link for that paying customer. Applicable with PayPal "Buttons" or ClickBank "Buttons" only._

- `login_redirect=""` The default value is an empty string, which indicates that the user should be redirected to their Login Welcome Page that you configured with s2Member. Or, you can set this to `%%previous%%` (Previous Page), `%%home%%` (Home Page). Or, use a full URL of your own.

---

### When Already Logged In

- `show_summary_if_logged_in="0"` This defaults to a value of `0` (off). If you want to display the user's profile summary if they are already logged in, you must set this to `1` (true). Otherwise, with the default behavior, the remaining shortcode attributes documented below are not applicable.

---

<div class="li-margins"></div>

- `profile_title="My Profile Summary"` Title when a user is already logged in. You can set this to an empty string if you want to exclude the title.

- `display_gravatar="1"` Display Gravatar image when logged in? `1` = yes, `0` = no. Gravatars are based on email address. The default value is `1` (i.e., display the Gravatar).

- `link_gravatar="1"` Link Gravatar image to gravatar.com? `1` = yes, `0` = no. By linking the image to gravatar.com, the user will better understand what they need to do in order to change this image. The default value is `1` (i.e., link the Gravatar).

- `display_name="1"` Display the current user's WordPress Display Name when logged in? `1` = yes, `0` = no. The default value is `1` (i.e., display their name).

- `logout_redirect="%%home%%"` The default value is `%%home%%`. You can set this to an empty string to indicate that a user should be redirected to `/wp-login.php`. Or, you can use `%%previous%%` (Previous Page), `%%home%%` (Home Page). Or, use a full URL of your own.

- `my_account_url="%%automatic%%"` The default value is `%%automatic%%`, which creates a "My Account" link that leads back to their Login Welcome Page. Or, use a full URL of your own. Set this to an empty string to exclude this if you prefer.

- `my_profile_url="%%automatic%%"` The default value is `%%automatic%%`, which creates a "My Profile" link that spawns a popup window where the user can edit their s2Member profile. Or, use a full URL of your own. Set this to an empty string to exclude this if you prefer.

---

## PHP Equivalent For Developers

See: [Embedding the Pro Login Widget via PHP](https://s2member.com/kb-article/pro-login-widget/#toc-3610725f)
