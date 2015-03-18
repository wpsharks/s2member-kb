---
title: '[s2MOP /] Shortcode'
categories: tutorials
tags: api-scripting,membership-options-page,shortcodes,s2mop
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/131
---

There is a new s2Member Pro Shortcode that can be used to enhance your Membership Options Page (i.e., the page in s2Member where you list membership options).

Your Membership Options Page is also the page where people without access to certain areas of your site are redirected to; e.g., when a visitor tries to access members-only content, but they are not yet a member. Or, perhaps they are, but they don’t yet have a membership which allows access to something available only at a higher Membership Level. So, your Membership Options Page is a key element of your site. It serves as the focal point of your s2Member installation.

Understanding this, we can see it becomes important for s2Member to provide information about what the visitor was attempting to access, before they were redirected to the Membership Options Page. This is where s2Member’s MOP Vars come in (i.e., Membership Options Page Variables). Whenever s2Member redirects a visitor to your Membership Options Page it will include some important MOP Vars in the query string of the URL. These variables can be used to provide more informative messages, or even to provide a different set of Membership Options (i.e., Payment Buttons or a Pro-Form) based on what a visitor was attempting to access.

For further details on this feature and a few examples of its use, please check your Dashboard under: **s2Member → API / Scripting → Membership Options Page / Variables**

---

## Introducing the `[s2MOP /]` Shortcode

Up until now, using s2Member’s MOP Vars in any meaningful way required the use of PHP tags and some knowledge of web programming and query string data. These things are not super complex, but now the `[s2MOP /]` Shortcode makes it easy for _anyone_ to implement messages based on this data in a variety of ways. You could even wrap the `[s2MOP /]` shortcode with [Simple Shortcode Conditionals](https://github.com/websharks/s2member-kb/issues/119) :-)

The `[s2MOP /]` shortcode is optional of course, but for those of you who would like to greet potential customers with a message (one that can also be quite specific)—this is for you! When a visitor is redirected away from members-only content and over to your Membership Options Page, the `[s2MOP /]` shortcode can be used to display a message for them. This can help to avoid confusion, and it may also impress your visitors; thereby building confidence in your site, products and/or services.

It’s pretty simple really. The `[s2MOP /]` shortcode (when inserted into your Membership Options Page) will detect the presence of s2Member MOP Vars and help you present a message that says something like, _“You were trying to access a protected Page which requires Bronze Membership”_. Of course, the message on your site might be very different from this. The `[s2MOP /]` Shortcode will make it easy for you to customize this as you see fit.

## A Quick Overview w/ Examples

The `[s2MOP /]` Shortcode can be called upon using `[s2MOP][/s2MOP]` or `[s2MOPNotice][/s2MOPNotice]` (an alias that does the same thing). The message you want to display goes in between the shortcode tags, and the message may optionally contain `%%` Replacement Codes that are filled in dynamically by the s2Member software. There are also a few Shortcode Attributes that can be used to limit the use of a particular message to certain scenarios (these attributes are all optional however).

### Example `[s2MOP /]` Shortcode

##### The easiest way to use the s2MOP Shortcode

_This goes at the top of your Membership Options Page, using the WordPress editor._

```html
[s2MOP]You attempted to access members-only content.[/s2MOP]
```

_**NOTE:** the message you define is only displayed on your Membership Options Page if s2Member’s MOP Vars are present; i.e., when a visitor is redirected to your Membership Options Page after they attempted to access content they were not allowed to see._

### A Few More `[s2MOP /]` Examples

```html
[s2MOP]You were trying to access a protected: %%SEEKING_TYPE%%[/s2MOP]
```

```html
[s2MOP]You were trying to access content that requires a %%REQUIRED_TYPE%% that you don't have.[/s2MOP]
```

```html
[s2MOP]You were trying to access content protected via %%RESTRICTION_TYPE%% restrictions[/s2MOP]
```

```html
[s2MOP seeking_type="post" required_type="level" restriction_type="post"]You were trying to access a restricted post with Post ID %%SEEKING_POST_ID%% which requires that you be a Member at Level #%%REQUIRED_LEVEL%%[/s2MOP]
```

```html
[s2MOP required_type="level"]"%%POST_TITLE%%" is a protected %%SEEKING_TYPE%% that requires Membership Level %%REQUIRED_LEVEL%%[/s2MOP]
```

```html
[s2MOP required_type="level" required_value="0|1"]You were trying to access a Post that requires Level <code>0</code> or <code>1</code>[/s2MOP]
```

```html
[s2MOP required_type="ccap" required_value="free_gift"]This content required a Custom Capability called <code>free_gift</code>[/s2MOP]
```

## Shortcode Attributes (All Optional)

<div class="li-margins"></div>

-   `seeking_type` — If supplied, this tells s2Member to _only_ display your message if the visitor is attempting to access a particular type of content. One of `post|page|catg|ptag|file|ruri` or any pipe-delimited combination that you prefer. This correlates with the `[seeking type]` value in s2Member’s MOP Vars; described in greater detail at the bottom of this article.
-   `restriction_type` — If supplied, this tells s2Member to _only_ display your message if the visitor is attempting to access something that is protected in a particular way with s2Member. One of `post|page|catg|ptag|file|ruri|ccap|sp|sys` or any pipe-delimited combination that you prefer. This correlates with the `[restriction type]` value in s2Member’s MOP Vars; described in greater detail at the bottom of this article.
-   `required_type` — If supplied, this tells s2Member to _only_ display your message if the visitor is attempting to access something that requires a particular type of access. One of `level|ccap|sp` or any pipe-delimited combination that you prefer. This correlates with the `[requirement type]` value in s2Member’s MOP Vars; described in greater detail at the bottom of this article.
-   `required_value` — If supplied, this tells s2Member to _only_ display your message if the visitor is attempting to access something that requires a particular type of access, and where that particular “type value” has one of the values listed in `required_value=""`. There are two examples above that use `required_value=""`. This can be a single value or a pipe-delimited set of values to test for. The “type value” correlates with the `[requirement type value]` in s2Member’s MOP Vars; described in greater detail at the bottom of this article. _NOTE: If `required_type=""` contains multiple values (e.g., `required_type="ccap|level"`) the `required_value=""` attribute is ignored; i.e., the shortcode cannot be extended to cover this use case. Please use multiple instances of `[s2MOP /]` instead._

## Message Replacement Codes (All Optional)

<div class="li-margins"></div>

-   `%%SEEKING_TYPE%%` – If used, will be replaced with one of the following: `Page|Post|Category|Tag|File|URI`.
-   `%%SEEKING_PAGE_ID%%` – If used, will be replaced with the numerical ID of the protected page the visitor is attempting to access (e.g., `42`).
-   `%%SEEKING_POST_ID%%` – If used, will be replaced with the numerical ID of the protected post the visitor is attempting to access (e.g., `42`).
-   `%%SEEKING_CAT_ID%%` – If used, will be replaced with the numerical ID of the protected category the visitor is attempting to access (e.g., `42`).
-   `%%SEEKING_TAG_ID%%` – If used, will be replaced with the numerical ID of the protected tag the visitor is attempting to access (e.g., `42`).
-   `%%SEEKING_FILE%%` – If used, will be replaced with the protected file the visitor is attempting to access (e.g., `pdfs/ebook.pdf`). File paths are relative to `/s2member-files/`, or your Amazon® S3 Bucket.
-   `%%SEEKING_RURI%%` – If used, will be replaced with the protected Request URI the visitor is attempting to access (e.g., `/movies/`).
-   `%%SEEKING_URI%%` – If used, will be replaced with the protected URI the visitor is attempting to access (e.g., `http://example.com/movies/`).
-   `%%REQUIRED_TYPE%%` – If used, will be replaced with one of the following: `Level|Capability|Specific Post/Page`.
-   `%%REQUIRED_LEVEL%%` – If used, will be replaced with the numeric Level the visitor is required to have for access (e.g., `2`, for Level 2).
-   `%%REQUIRED_LEVEL_LABEL%%` – If used, will be replaced with a Label that describes the Level the visitor is required to have for access (e.g., `Silver Membership`, for Level 2). If you’ve configured s2Member with custom Membership Level Labels, your custom Label will be used here. See: **Dashboard → s2Member → General Options → Membership Levels/Labels** for more information.
-   `%%REQUIRED_CCAP%%` – If used, will be replaced with the Custom Capability the visitor is required to have for access (e.g., `movies`, for Custom Capability "movies").
-   `%%REQUIRED_SP%%` – If used, will be replaced with the numerical ID of the Specific Post/Page the visitor is attempting to access (e.g., `42`).
-   `%%RESTRICTION_TYPE%%` – If used, will be replaced with one of the following: `Page|Post|Category|Tag|File|URI|Custom Capability|Specific Post/Page|Systematic`.
-   `%%POST_TITLE%%` – If used, will be replaced with the title of the Post the visitor is attempting to access.
-   `%%POST_EXCERPT%%` – If used, will be replaced with an excerpt of the post the visitor is attempting to access. If no excerpt is set, one will be generated using the first 55 words (configurable via `excerpt_length`; see the [WordPress Codex](https://codex.wordpress.org/Plugin_API/Filter_Reference/excerpt_length)). Note that you may want to surround this replacement tag with `[s2If has_excerpt()][/s2If]` to prevent the raw replacement tag from appearing when the restricted content doesn’t support excerpts. (See [Simple Shortcode Conditionals](https://github.com/websharks/s2member-kb/issues/119).)
-   `%%PAGE_TITLE%%` – If used, will be replaced with the title of the Page the visitor is attempting to access.

---

## s2Member MOP Vars (Explained)

See also: **Dashboard → API / Scripting → Membership Options Page / Variables**

```text
-----------------------------------------------------------------------------------------------------------
Example redirection link with MOP Vars, in pseudo code:
-----------------------------------------------------------------------------------------------------------

s2Member's MOP Vars are now a double-dot (`..`) delimited list of six values.

	.../membership-options-page/
	?_s2member_vars=[restriction type]..[requirement type]..[requirement type value]..
			[seeking type]..[seeking type value]..[seeking URI base 64 encoded]

-----------------------------------------------------------------------------------------------------------

Here is a breakdown that explains each of the values:

	* `[restriction type]` = A string. One of: `post|page|catg|ptag|file|ruri|ccap|sp|sys`
		- The s2Member Restriction Type you've configured which is preventing access.
		- Restriction Type `post` indicates that Post Access Restrictions triggered the redirection.
		- Restriction Type `page` indicates that Page Access Restrictions triggered the redirection.
		- Restriction Type `catg` indicates that Category Access Restrictions triggered the redirection.
		- Restriction Type `ptag` indicates that Post Tag Access Restrictions triggered the redirection.
		- Restriction Type `file` indicates that File Access Restrictions triggered the redirection.
		- Restriction Type `ruri` indicates that Request URI Access Restrictions triggered the redirection.
		- Restriction Type `ccap` indicates Custom Capability Restrictions triggered the redirection.
		- Restriction Type `sp` indicates Specific Post/Page Access Restrictions triggered the redirection.
		- Restriction Type `sys` indicates Systematic (i.e. something s2Member protects automatically).

	* `[requirement type]` = A string. One of: `level|ccap|sp`
		- Requirement Type `level` indicates that a Membership Level is required for access.
		- Requirement Type `ccap` indicates that a Custom Capability is required for access.
		- Requirement Type `sp` indicates that a Specific Post/Page purchase is required for access.

	* `[requirement type value]` = A string. The Level, CCAP or Specific Post/Page ID required for access.
		- This value correlates with `[requirement type]` to supply more specific information.
			For instance, if `[requirement type]` is `level`, `[requirement type value]`
			might be `1` to indicate that Level `1` is required for access.
		- In the case of a CCAP, this will be set to the CCAP required for access.
		- In the case of a Specific Post/Page, this is set to the Post/Page ID in WordPress.

	* `[seeking type]` = A string. One of: `post|page|catg|ptag|file|ruri`
		- This identifies the type of content a visitor was attempting to access.
			A Post (`post`), Page (`page`), Category (`catg`), Post Tag (`ptag`), File (`file`),
			 or a Request URI (`ruri`) to indicate something that doesn't fall into any other classification.

	* `[seeking type value]` = A string. A Post ID, Page ID, Category ID, Post Tag ID, File, or Request URI.
		- This correlates with `[seeking type]` to supply more specific information.
			For instance, if `[seeking type]` is `post`, this might be `123` to indicate the
			visitor was attempting to access Post ID `123` in WordPress.
		- File paths are relative to `/s2member-files/`, or your Amazon® S3 Bucket.
		- Request URIs are base 64 encoded. Use PHP's `base64_decode()` to decode the value.

	* `[seeking URI; base 64 encoded]` = A string. Base 64 encoded URI that a visitor was attempting to access.
		- Request URIs are base 64 encoded. Use PHP's `base64_decode()` to decode the value.

-----------------------------------------------------------------------------------------------------------

* The use of MOP Vars is 100% completely optional (for advanced site owners).
```

---

## PHP Example Code (For Developers Choosing NOT to use the Shortcode)

```php
<?php
if(!empty($_REQUEST["_s2member_vars"]))
	@list($restriction_type, $requirement_type, $requirement_type_value, $seeking_type, $seeking_type_value, $seeking_uri)
			= explode("..", stripslashes((string)$_REQUEST["_s2member_vars"]));

if (!empty($seeking_type) /* One of: page|post|catg|ptag|file|ruri */ )
    echo 'You were trying to access a protected: ' . esc_html($seeking_type) . '.';
```
