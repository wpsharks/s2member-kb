---
title: '[s2Member-List /] Shortcode Documentation'
categories: tutorials
tags: shortcodes,s2member-list
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/123
---

The `[s2Member-List /]` shortcodes makes it possible for site owners to build a list of their members in a variety of ways. The shortcode might be used to present a list of your highest ranking members, or simply to provide other members with a way to search for each other. There are a lot of use cases for this.

---

## `[s2Member-List /]` Shortcode Examples

--

### Display All Users; 25 Users Per Page (Default)

```wpsc
[s2Member-List /]
```

### Display a List of Free Subscribers

```wpsc
[s2Member-List roles="subscriber" /]
```

or… using the levels attribute (same thing in this case)

```wpsc
[s2Member-List levels="0" /]
```

### Users at Level 2; Who ALSO have CCAPS `premium` & `ultimate`

```wpsc
[s2Member-List levels="2" ccaps="premium,ultimate" /]
```

### All Users; and Also Display Some Additional Fields

```wpsc
[s2Member-List show_fields="user_login,user_registered,custom_field_id" /]
```

_The list of field IDs can include anything compatible with s2Member’s [get_user_field()](https://github.com/websharks/s2member-kb/issues/130) function._

### Users w/ CCAP mentor

```wpsc
[s2Member-List ccaps="mentor" /]
```

### Ordered by Display Name (Exclude Super Admin)

```wpsc
[s2Member-List orderby="display_name" order="ASC" exclude="1" /]
```

_This assumes the Super Admin is user ID `1`. That may not always be the case. Please change `1` to the user ID associated with the Super Admin on your installation of WordPress. A plugin like [WP Show IDs](http://wordpress.org/plugins/wp-show-ids/) could be handy._

### Users at Level 2 (and with ALL of these CCAPS)

```wpsc
[s2Member-List levels="2" ccaps="bonus,ultimate_package,supreme" rlc_satisfy="ALL" /]
```

### Users at Level 2 (or with ANY of these CCAPS)

```wpsc
[s2Member-List levels="2" ccaps="bonus,ultimate_package,supreme" rlc_satisfy="ANY" /]
```

### Allow Users to Search for Each Other

```wpsc
[s2Member-List-Search-Box /]
[s2Member-List enable_list_search="yes" /]
```

### Only Allow Members at Level 2 to Search for Each Other

```wpsc
[s2If current_user_can(access_s2member_level2)]
	[s2Member-List-Search-Box /]
	[s2Member-List levels="2" enable_list_search="yes" /]
[/s2If]
```

_To learn more about `[s2If /]`, see: [Simple Shortcode Conditionals](https://github.com/websharks/s2member-kb/issues/119)_

---

## Optional Shortcode Attributes (Documentation)

### These Attributes Impact the User Query (i.e. the Search Itself)

<div class="li-margins"></div>

-   `roles` Optional. This can be a comma-delimited list of Role IDs (or a single Role ID); e.g., `subscriber`, `s2member_level1`, `s2member_level2`, `author`, `contributor`, etc. The default is to include all users. If you’re not familiar with WordPress Roles, please see [s2Member Roles/Capabilities](https://github.com/websharks/s2member-kb/issues/122). **Note:** Ordinarily this is set to just one specific Role; i.e., when you want to list users that have a specific Role. However, it is also possible to provide a comma-delimited list of Roles and set `rlc_satisfy="ANY"` (details below). For instance, if you set `roles="subscriber,s2member_level1" rlc_satisfy="ANY"` you will list users with a Role of either `subscriber` or `s2member_level1`.
-   `levels` Optional (works as an alternative to `roles`). This can be a comma-delimited list of numeric Membership Levels (or a single Membership Level); e.g., `0`, `1`, `2`, `3`, `4`, etc. The default is to include all users, no matter what Membership Level or Role they might have. **Note:** Ordinarily this is set to just one specific Level; i.e., when you want to list users that have a specific Membership Level. However, it is also possible to provide a comma-delimited list of Levels and set `rlc_satisfy="ANY"` (details below). For instance, if you set `levels="0,1" rlc_satisfy="ANY"` you will list users with a Level of either `0` or `1` (i.e., Free Subscribers and/or Level 1 Members).
-   `ccaps` Optional. This will limit the query to users that have one or more Custom Capabilities (CCAPS). This can be a single CCAP or a comma-delimited list of CCAPS; e.g., `ccaps="music,videos,free_gift"` **Note:** By default, a user must have all of the CCAPS that you list for them to be included in the list. However, it is also possible to provide a comma-delimited list of CCAPS and set `rlc_satisfy="ANY"` (details below). For instance, if you set `ccaps="freemium,premium" rlc_satisfy="ANY"` you will list users that have either the `freemium` or `premium` CCAP (either/or).
-   `rlc_satisfy` Optional, defaults to a value of `ALL`. By default, anything you specify in `roles`, `levels` and/or `ccaps` is required (i.e., ALL conditions must be satisfied). If you set `rlc_satisfy="ANY"`, then any `roles`, `levels` and/or `ccaps` in the list will be included in the list of results. The `rlc_satisfy` attribute correlates with the `roles`, `levels` and `ccaps` attributes collectively. It does not impact other shortcode attributes in any way.
-   `search` Optional. This will limit the query to users matching a specific keyword (or keyword phrase) that you specify. See also `search_columns` to help customize your search further.
-   `search_columns` If you supply a `search` keyword (or phrase) these are the [wp_users](http://codex.wordpress.org/Database_Description#Table:_wp_users) table columns that will be searched. This should be a comma-delimited list of [wp_users](http://codex.wordpress.org/Database_Description#Table:_wp_users) table columns. The default is `ID,user_login,user_email,user_url,user_nicename`. **Note:** It is also possible to search Custom Registration/Profile Fields you created with s2Member. To search custom fields use `s2member_custom_field_[my unique id]`, where you replace `[my unique id]` with the Unique ID that you gave the field when you created it with s2Member. Please be advised that searching Custom Registration/Profile Fields may result in a slower DB query; i.e., at this time is _not_ recommended on sites with more than 5000 users.
-   `include` Optional. This will limit the set of results to only a specific user ID that you list, or a comma-delimited list of multiple user IDs is also acceptable. Note: **this does NOT simply include additional users by ID** (i.e., it’s NOT in addition to other query vars). Instead, this filters the set of results to include only those user IDs that you list. For instance, you might want to query all users at Membership Level 1, but then you might choose to include only specific user IDs from that set of results using the `include` attribute. The `include` attribute could also be used on it’s own of course; i.e., without any other query filters.
-   `exclude` Optional. This will force the exclusion of a specific user by ID. You can specify a single user ID to exclude, or a comma-delimited list of multiple user IDs.
-   `order` Optional sort order. Defaults to `DESC`. This can be one of `DESC` or `ASC`.
-   `orderby` Optional. Defaults to `registered`. Sort by `ID`, `login`, `nicename`, `email`, `url`, `registered`, `display_name`, or `post_count`.
-   `limit` Optional. Defaults to `25` results per page.

---

### These Attributes Control Output Display (i.e., the Template)

<div class="li-margins"></div>

-   `show_avatar` Optional, defaults to `yes`. Should the user’s avatar be displayed? This can be any boolean-ish value like `1|on|yes|true` or `0|off|no|false`.
-   `avatar_size` Optional. Defaults to `48` pixels; i.e., `48`.
-   `link_avatar` Optional, defaults to `""` (an empty string; i.e., no link). If you want to link the user’s avatar to another area of your site (e.g., a user profile page) you can set this to a URL of your choosing. Or, you could set this to something like `http://www.gravatar.com/%%md5.email%%` where `%%md5.email%%` is a Dynamic Replacement Code. If you decide to customize this, the following Replacement Codes are available if you need them: `%%ID%%`, `%%username%%`, `%%nicename%%`, `%%display_name%%`, `%%email%%`, `%%md5.email%%` (an MD5 hash of the email address).
-   `show_display_name` Optional, defaults to `yes` (recommended). Should the user’s display name be shown? This can be any boolean-ish value like `1|on|yes|true` or `0|off|no|false`.
-   `link_display_name` Optional, defaults to `""` (an empty string; i.e., no link). If you want to link the user’s display name to another area of your site (e.g., a user profile page) you can set this to a URL of your choosing. If you decide to customize this, the following Replacement Codes are available if you need them: `%%ID%%`, `%%username%%`, `%%nicename%%`, `%%display_name%%`, `%%email%%`, `%%md5.email%%` (an MD5 hash of the email address). If you’re using BuddyPress you might set this to: `/members/%%nicename%%/`
-   `show_fields` Optional, defaults to `""` (an empty string, i.e., no fields). This is one of the most useful shortcode attributes. You can build a list of fields for each user. For instance, if you have Custom Registration/Profile Fields configured with s2Member you can provide a comma-delimited list of unique Field IDs here. If the user has a value for that field it will be displayed in the final output. e.g., `show_fields="user_login,user_registered,custom_field_id"`. The list of field IDs can include anything compatible with s2Member’s [get_user_field()](https://github.com/websharks/s2member-kb/issues/130) function.

  _**Privacy Policy:** Please be careful about displaying information about a user that might go public without the user’s consent. Generally speaking, it’s good idea to label any field that you intend to display publicly (and mention it in your privacy policy too), so a user knows your intention is to display it in the list of users publicly._
  
  **TIP `show_fields`:** By default, each field’s label is generically constructed from the field’s ID. However, you can customize the field labels (optionally) using a special `:` colon-delimited format as follows: `show_fields="Field Label 1:field_id1,Field Label 2:field_id2"`. This produces a table with the following format:
  
  |      `Field Label 1`     |     `Field Label 2`     |
  |  ----------------------- |  ---------------------  |
  |  `[value for field_id1]` | `[value for field_id2]` |
-   `template` Optional. If you would like to use a custom template file for the final output display, you can specify a file path relative to `WP_CONTENT_DIR` here. Please grab the default template file and make a copy to work from. Put your copy somewhere in the `WP_CONTENT_DIR`. See `s2member-pro/includes/templates/members/member-list.php`

---

### This Attribute Enables Search Box Functionality

-   `enable_list_search` Optional, defaults to no. Should users be allowed to search for each other? This can be any boolean-ish value like `1|on|yes|true` or `0|off|no|false`. **Note:** this works in conjunction with the `[s2Member-List-Search-Box /]` shortcode. If you set `[s2Member-List enable_list_search="yes" /]` you can add an additional shortcode that creates a search box for users; e.g., `[s2Member-List-Search-Box /]` — which produces a search box.

    #### `[s2Member-List-Search-Box /]` Attributes Explained

    Example: `[s2Member-List-Search-Box action="" placeholder="" /]`

    <div class="li-margins"></div>

    -   `action` Optional, defaults to `""` (i.e., an empty string); which will work just fine if your list of members is on the same page as your search box. This correlates with the `<form action="">` used by the search box. If your search box is located on a different page set `action="http://example/path/to/my/list/of/members"`; i.e., the URL to a page where an `[s2Member-List enable_list_search="yes" /]` shortcode is being used.
    -   `placeholder` Optional, defaults to `Search users…`. If you would like to change the default watermark that appears inside the search box set this to whatever you like better.
    -   `template` Optional. If you would like to use a custom template file for the search box markup, you can specify a file path relative to `WP_CONTENT_DIR` here. Please grab the default template file and make a copy to work from. Put your copy somewhere in the `WP_CONTENT_DIR`. See `s2member-pro/includes/templates/members/member-list-search-box.php`

---

### These Attributes are Rarely Used (i.e., for Advanced Site Owners)

<div class="li-margins"></div>

-   `blog` Optional, for multisite WP installations only. This defaults to the current blog, but if you prefer to list members from a specific blog you can pass a numeric blog ID in this shortcode attribute. **Note:** If you have a [Multisite Network Support License](http://s2member.com/prices/) for s2Member Pro and you `define('MULTISITE_FARM', TRUE);` in your `/wp-config.php` file, this will ONLY work from the Main Site in your Network (for security purposes). However, if `MULTISITE_FARM` is not set to `TRUE`, this works from any child blog in a network.
-   `args` Optional, for advanced use only. Here you can provide a full set of your own arguments to the WordPress core function [get_users()](http://codex.wordpress.org/Function_Reference/get_users). If this shortcode attribute is supplied, many of the other shortcode attributes are ignored in favor of what you specify here. In short, if you supply `args` you don’t need to specify other shortcode attributes that deal with the user query. However, you may still want to customize shortcode attributes that impact the final template display. Such as those prefixed with `show_` or `link_`. _**Note:** multiple `args` should be passed in query string format so they can be parsed by [wp_parse_args()](https://codex.wordpress.org/Function_Reference/wp_parse_args); e.g., `role=s2member_level1&orderby=registered&order=DESC`_
