---
title: '[s2If /] Simple Shortcode Conditionals'
categories: tutorials
tags: shortcodes,restriction-options,s2if,conditional-tags
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/119
---

## A Quick Overview of Conditionals

s2Member makes it very simple to protect entire Posts/Pages/Categories/Tags/URIs/etc. This can be accomplished from inside WordPress. See: **Dashboard → s2Member → Restriction Options**. Or, from your Post/Page editing station in WordPress. We consider this to be point-and-click functionality. Very easy.

**What many site owners don’t realize though**, is that s2Member _also_ makes it easy to protect “parts” of a Post or Page. You can even get creative about what you display to certain Users/Members, based upon your own custom criteria. s2Member’s **Simple Shortcode Conditionals** are the key to accomplishing this. In fact, to say that s2Member can merely protect “parts” of a Post or Page is an understatement. With s2Member’s **Simple Shortcode Conditionals** you can not only protect parts of your content, you can also deal with other kinds of conditions; making these a vital part of a successful membership site.

---

## A Few Scenarios where Simple Shortcode Conditionals can Help

<div class="li-margins"></div>

-   Sometimes it’s necessary to allow everyone to access to your content (e.g., everyone can land on a certain Post or Page and view it), but maybe you need to hide (protect) a certain part of that content. Or, maybe you need to display something different to non-members.
-   Maybe you need to change the way something appears (or even what details are given), based on the current Post or Page, the current Post Type. Or, perhaps based on what Tags that content may have, what Category it’s in, what Sidebar it’s in, if it’s Sticky or not, who authored the content, etc.
-   Maybe you want to display certain data, but only if a member has previously completed an action. Such as joining your mailing list, filling out a survey, visiting a certain Post or Page, filling in a value for a certain Profile Field, clicked a certain link, etc, etc.
-   In some cases you might want to display something different depending on the time of day it is. Or, depending on how long an existing member has been paying you. This would be considered Content Dripping and Simple Shortcode Conditionals can help with this too. See also: [Content Dripping Shortcodes](https://github.com/websharks/s2member-kb/issues/129)

**Note:** There are many situations like this. Obviously, s2Member can’t possibly predict every possible scenario—in every possible business model. But what we _can_ do is provide the tools you need to make things like this easier to deal with. 

---

## Simple Shortcode Conditional Tags

s2Member makes Simple Conditionals available to you from within WordPress, using Shortcodes that are compatible with both the Visual Editor and also the HTML Tab in WordPress. In this section we’ll demonstrate several functions that are possible using Shortcodes. I will list a few here, but you can also take a look at [Conditional Tags](http://codex.wordpress.org/Conditional_Tags) available for WordPress in general. There are _many_ possibilities—well beyond the the scope of this article and the examples given here.

### Most Popular Conditional Tags in s2Member

- [is_user_logged_in()](http://codex.wordpress.org/Function_Reference/is_user_logged_in)
- [current_user_can(capability)](http://codex.wordpress.org/Function_Reference/current_user_can)
- [current_user_can_for_blog(blog_id,capability)](http://codex.wordpress.org/Function_Reference/current_user_can_for_blog)
- [user_can(user_id, capability)](http://codex.wordpress.org/Function_Reference/user_can)
- [is_super_admin(user_id)](http://codex.wordpress.org/Function_Reference/is_super_admin)

Most of these [Conditional Tags](http://codex.wordpress.org/Conditional_Tags) work together with s2Member & [WordPress Roles/Capabilities](http://codex.wordpress.org/Roles_and_Capabilities). It would be a good idea to learn more about WordPress Roles/Capabilities so you can understand exactly what you’re working with. The examples below will serve you well, but the [article on WordPress Roles/Capabilities](http://codex.wordpress.org/Roles_and_Capabilities) is recommended if you’re having trouble. See also: [s2Member Roles/Capabilities](https://github.com/websharks/s2member-kb/issues/122).

To make use of these [Conditional Tags](http://codex.wordpress.org/Conditional_Tags), please follow the code samples below. Using [Shortcodes](http://codex.wordpress.org/Shortcode_API) for WordPress it’s easy to build Simple Conditionals into your content. With Simple Shortcode Conditionals you can accommodate many different scenarios; all based on a Member’s Level, Custom Capabilities—or other factors.

s2Member’s [Shortcodes](http://codex.wordpress.org/Shortcode_API) can be used inside a Post/Page and also inside Text Widgets.

---

## Simple Shortcode Examples w/ `[s2If /]`

### There are two different Shortcodes being demonstrated here:

1. `[s2If /]` (for testing simple conditional expressions).
2. `[s2Get /]` (to get an API Constant value, a Custom Field, or meta key).

---

### Example 1: Full access for anyone that is logged in:

```html
[s2If is_user_logged_in()]
    Content for anyone that is logged in, regardless of their Membership Level.
[/s2If]

[s2If !is_user_logged_in()]
    Some public content. They're NOT logged in.
        A leading !exclamation means false.
[/s2If]
```

---

### Example 2: Full access for any Member with a Level >= 1:

```html
[s2If current_user_can(access_s2member_level1)]
    Some content for Members who are logged in with an s2Member Level >= 1.
[/s2If]

[s2If !current_user_can(access_s2member_level1)]
    Some public content.
[/s2If]
```

---

### Example 3: Specific content for each different Member Level:

```html
[s2If current_user_is(s2member_level4)]
    Some premium content for Level 4 Members.
[/s2If]

[s2If current_user_is(s2member_level3)]
    Some premium content for Level 3 Members.
[/s2If]

[s2If current_user_is(s2member_level2)]
    Some premium content for Level 2 Members.
[/s2If]

[s2If current_user_is(s2member_level1)]
    Some premium content for Level 1 Members.
[/s2If]

[s2If current_user_is(s2member_level0)]
    Some content for Free Subscribers.
[/s2If]

[s2If !current_user_can(access_s2member_level0)]
    Some public content.
[/s2If]
```

---

### Example 4: Simple Conditionals w/ integrated use of `[s2Get /]`:

```html
[s2If current_user_is(s2member_level1)]
    Content for Members at exactly Level# 1, on this Blog.
[/s2If]

[s2If current_user_is(s2member_level2) OR current_user_is_for_blog(24,s2member_level2)]
    They are either a Level #2 Member on this Blog,
    OR ... they're at Level# 2 on Blog ID# 24 (i.e. Multisite Networking)

        * Note the use of `OR` here. True if either condition is met.
[/s2If]

[s2If current_user_is(s2member_level3) OR current_user_is(s2member_level4)]
    Content for Level #3 - OR - Level #4 Members. Either/or.

    Hi there [s2Get constant="S2MEMBER_CURRENT_USER_DISPLAY_NAME" /].
    You have [s2Get constant="S2MEMBER_CURRENT_USER_ACCESS_LABEL" /].

        ^ This uses the s2Get Shortcode to retrieve the value of s2Member API Constants.
            These are also documented under: `Dashboard → s2Member → API Scripting`.

        So, this might come out to something like:
            `Hi there John.
            You have Gold Membership.`

        Here is a Custom Field value:
        [s2Get user_field="country_code" /]
        Custom Registration/Profile Field with the ID: `country_code`.
[/s2If]
```

---

### Example 5: Inside a Text Widget:

This example uses the [is_page()](http://codex.wordpress.org/Function_Reference/is_page) Conditional Tag in WordPress. In this example we only display content in this Text Widget to Members at Level 1 or higher—and only on a specific Page with the Slug: `members-only`. This example also demonstrates nested Shortcode Conditionals. Notice that NESTED Conditionals require a preceding underscore (i.e., `_s2If`, `__s2If`, `___s2If`). You can go up to three levels deep (e.g., `___s2If`).

```html
[s2If is_page(members-only)]
	[_s2If current_user_can(access_s2member_level1)]
		We're on a specific Page of the site, with Slug: `members-only`.
		Some content for Members who are logged in with an s2Member Level >= 1.
	[/_s2If]
[/s2If]
```

_You can also accomplish this with the [Widget Logic](http://wordpress.org/extend/plugins/widget-logic/) plugin (compatible with s2Member). However, the syntax is slightly different; it uses 100% PHP syntax. See also: [Menu Items Visibility Control](http://wordpress.org/extend/plugins/menu-items-visibility-control/)_

---

### Example 6: Conditional Tags that accept arrays:

This example uses the [is_page()](http://codex.wordpress.org/Function_Reference/is_page) Conditional Tag in WordPress (which accepts array values too). In this example we only display content in this Text Widget to Members at Level 1 or higher—and only on specific Pages (plural). This example also demonstrates nested Shortcode Conditionals. Notice that NESTED Conditionals require a preceding underscore (i.e., `_s2If`, `__s2If`, `___s2If`). You can go up to three levels deep (e.g., `___s2If`).

```html
[s2If is_page({members-only,my-profile,123,994})]
	[_s2If current_user_can(access_s2member_level1)]
		We're on one of these pages: `members-only`, `my-profile`, Page ID `123` or `994`.
		Some content for Members who are logged in with an s2Member Level >= 1.
	[/_s2If]
[/s2If]
```

_You can also accomplish this with the [Widget Logic](http://wordpress.org/extend/plugins/widget-logic/) plugin (compatible with s2Member). However, the syntax is slightly different; it uses 100% PHP syntax. See also: [Menu Items Visibility Control](http://wordpress.org/extend/plugins/menu-items-visibility-control/)_

---

### Example 7: Using Conditionals together with other Shortcodes:

This example also demonstrates how to test for access to Custom Capabilities.

```html
[s2If current_user_can(access_s2member_ccap_free_gift)]
    This Member can access Custom Capability: `free_gift`.
    Hi there [s2Get constant="S2MEMBER_CURRENT_USER_DISPLAY_NAME" /]!
    	~ Claim your free gift by clicking here.
[/s2If]

[s2If !current_user_can(access_s2member_level4)]
    Content for someone who does NOT have Level #4 access.
   [s2Member-PayPal-Button modify="1" level="4" ra="49.95" desc="Upgrade To Level #4" /]
[/s2If]

[s2If current_user_is(administrator)]
    Content specifically for a WordPress® Administrator.
[/s2If]

[s2If current_user_is(editor)]
    Content specifically for a WordPress® Editor.
[/s2If]

[s2If current_user_is(author)]
    Content specifically for a WordPress® Author.
[/s2If]

[s2If current_user_is(contributor)]
    Content specifically for a WordPress® Contributor.
[/s2If]

[s2If current_user_is(subscriber)]
    Content specifically for a WordPress® Subscriber.
[/s2If]
```

---

## s2Member Supports All WordPress Conditional Tags

s2Member supports ALL [Conditional Tags](http://codex.wordpress.org/Conditional_Tags) in WordPress—plus a few extra variations that are made possible by s2Member.

**Including, but not limited to:**

- `is_user_logged_in()`
- `is_user_not_logged_in()`
- `user_is(user_id, role)`
- `user_is_not(user_id, role)`
- `user_can(user_id, capability)`
- `user_cannot(user_id, capability)`
- `current_user_is(role)`
- `current_user_is_not(role)`
- `current_user_can(capability)`
- `current_user_cannot(capability)`
- `current_user_is_for_blog(blog_id,role)`
- `current_user_is_not_for_blog(blog_id,role)`
- `current_user_can_for_blog(blog_id,capability)`
- `current_user_cannot_for_blog(blog_id,capability)`
- `is_multisite()`
- `is_main_site()`
- `is_super_admin()`
- `is_admin()`
- `is_blog_admin()`
- `is_user_admin()`
- `is_network_admin()`
- `is_404()`
- `is_home()`
- `is_front_page()`
- `is_comments_popup()`
- `is_singular(ID|slug|{slug,ID})`
- `is_single(ID|slug|{slug,ID})`
- `is_page(ID|slug|{slug,ID})`
- `is_page_template(file.php)`
- `is_attachment()`
- `is_feed()`
- `is_trackback()`
- `is_archive()`
- `is_search()`
- `is_category(ID|slug|{slug,ID})`
- `is_tax(taxonomy,term)`
- `is_tag(slug|{slug,slug})`
- `has_tag(slug|{slug,slug})`
- `is_author(ID|slug|{slug,ID})`
- `is_date()`
- `is_day()`
- `is_month()`
- `is_time()`
- `is_year()`
- `is_sticky(ID)`
- `is_paged()`
- `is_preview()`
- `is_comments_popup()`
- `in_the_loop()`
- `comments_open()`
- `pings_open()`
- `has_excerpt(ID)`
- `has_post_thumbnail(ID)`
- `is_active_sidebar(ID|number)`

---

## `[s2If /]` Tips & Tricks

<div class="li-margins"></div>

1. **True/false** example:
 - `[s2If current_user_can()][/s2If]`
 - or false `[s2If !current_user_can()][/s2If]` (i.e., the `!` tests for a false value).
2. **False explicitly** example:
 - `[s2If current_user_cannot()][/s2If]` This is a special addition provided by s2Member that makes false testing easier for some.
3. **Passing an ID** example:
 - `[s2If is_page(24)][/s2If]` For functions that require an argument in the form of an ID.
4. **Passing a Slug** example:
 - `[s2If is_page(my-cool-page)][/s2If]` For functions that require an argument in the form of a slug.
5. **Passing an Array** example:
 - `[s2If is_page({my-cool-page,24,about,contact-form})][/s2If]` (i.e., to pass an array of values, please use comma-delimitation).

**Tip:** do NOT use spaces in your Simple Conditional arguments.

- **INVALID:** `[s2If is_page(My Membership Options Page)][/s2If]` _Use slugs or IDs instead, no spaces please—spaces will break the Shortcode parser._

---

### Implementing AND/OR Conditional Expressions

**Tip:** do NOT mix AND/OR expressions together in a single expression.

- **INVALID:** `[s2If is_user_logged_in() AND is_page(1) OR is_page(2)][/s2If]` _Use one or the other; do NOT mix AND/OR together. If you need to have both types of logic use nesting._

This example demonstrates nested Shortcode Conditionals. Notice that NESTED Conditionals require a preceding underscore (i.e., `_s2If`, `__s2If`, `___s2If`). You can go up to three levels deep (e.g., `___s2If`).

```html
[s2If is_user_logged_in() AND current_user_is(s2member_level1)]
  [_s2If is_page(1) OR is_page(2)]
  	Content appears here.
  [/_s2If]
[/s2If]
```

---

### Implementing an "else" Condition

Sometimes you might want to check for a condition, but if that is false, you do something else by default (i.e., an `else` condition). This is a bit tricky if you're not already familar with conditional logic, but the example below should serve you well. To accomplish this with Simple Shortcode Conditionals you combine `[s2If][/s2If]` with a nested `[else]` tag.

```html
[s2If current_user_can(access_s2member_ccap_music)]
	Content for members with the Custom Capability: music
	[else]
		You will need to pay for access to music please.
[/s2If]
```

---

## Straight-Up PHP Conditional Tags (e.g., `<?php if(): ?>`)

If you're a developer or a site owner and you already have experience with PHP tags, you might have noticed that all of these `[s2If][/s2If]` examples are relying upon PHP functions in the WordPress content management system. Understanding this, it becomes obvious that you could also bypass the use of `[s2If][/s2If]` in favor of regular PHP tags—if you wanted to. This can be easier in some cases, but really it's a personal preference :-)

```php
<?php if(current_user_can('access_s2member_ccap_music')): ?>
	Content for members with the Custom Capability: music
<?php else: // Else show this. ?>
	You will need to pay for access to music please.
<?php endif; ?>
```

See also: [ezPHP for WordPress](https://wordpress.org/plugins/ezphp/) if you'd like to use PHP tags in WordPress Posts/Pages.
