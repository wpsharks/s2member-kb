---
title: '[s2Drip /] Shortcode'
categories: tutorials
tags: api-scripting,content-dripping,shortcodes
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/129
---

## What is Content Dripping?

Content Dripping is the gradual, pre-scheduled release of premium website content to paying Members. This has become increasingly popular, because it allows older Members; those who have paid you more, due to recurring charges; to acquire access to more content progressively based on their original paid registration time. It also gives you (as the site owner), the ability to launch multiple membership site portals, operating on autopilot, without any direct day-to-day involvement in a content release process.

Up until now, Content Dripping with s2Member required a working knowledge of PHP and s2Member API Functions. With the new `[s2Drip]` Shortcode it is now easy for _anyone_ to drip content in creative ways, using a simple set of Attributes accepted by the `[s2Drip]` Shortcode.

_**Note:** While the `[s2Drip]` Shortcode is quite powerful, there is more work to be done; i.e., more room for improvement. What I discuss in this article is among the first of a set of features that we are working on. Additional improvements may come later in a future release of the s2Member Pro software. If you’d like to post a feature request, please [create a GitHub issue](https://github.com/websharks/s2member/issues). Thanks!_

## Introducing the `[s2Drip]` Shortcode

**The `[s2Drip]` Shortcode requires s2Member Pro.**

The `[s2Drip][/s2Drip]` Shortcode tags are inserted into a Post/Page with the WordPress editor. Inside the shortcode tags you place content that should only be visible to paying members who are at a certain Membership Level (or higher); and have been at this Membership Level (or higher) for at least X number of days. It is also possible to hide this content after X number of days; e.g., to drip content for a specific number of days and then automatically stop the drip too.

### `[s2Drip]` Example #1

```text
[s2Drip access="level1" from_day="4"]
    Some content for Members at Level 1 (or higher).

    This content will show only after day 3 of their paid membership.
        ~ i.e. it starts showing on day 4.

    It will continue to be shown every day thereafter.
[/s2Drip]
```

### `[s2Drip]` Example #2

```text
[s2Drip access="level1" from_day="4" to_day="30"]
    Some content for Members at Level 1 (or higher).

    This content will show only after day 3 of their paid membership.
        ~ i.e. it starts showing on day 4.

    In addition, this content will stop being shown on day 31 of their paid membership.
        ... i.e. show until (and including) day 30; stop showing after day 30.
[/s2Drip]
```

### `[s2Drip]` Example #3

```text
[s2Drip access="level1 AND (ccap_music OR ccap_videos)" from_day="4" to_day="30"]
    Some content for Members at Level 1 (or higher).
    They must also have the CCAP `music` or the CCAP `videos` too.

    This content will show only after day 3 of their paid membership.
        ~ i.e. it starts showing on day 4.

    In addition, this content will stop being shown on day 31 of their paid membership.
        ... i.e. show until (and including) day 30; stop showing after day 30.
[/s2Drip]
```

## `[s2Drip]` Shortcode Attributes Explained

<div class="li-margins"></div>

-   `access` What access is required to view the content? This should include strings like `level0`, `level1`, `level2`; and/or `ccap_music`, `ccap_videos`. You can also use `AND` / `OR` logic here, and even nesting both types of logic is acceptable; e.g., `access="level1 AND (ccap_music OR ccap_videos)"`. Please check the examples above for further clarification. **Note:** if you leave this empty, Membership `level0` is used as the default value (i.e., a Free Subscriber would have access).
-   `from_day` On which day to begin the drip. If this is set to `4`, the content will show only after day 3 of their paid membership; i.e., it starts showing on day 4. If you leave this empty, a value of `0` is used as the default (i.e., the drip begins as soon as they become a paid member).
-   `to_day` On which day to stop the drip (if applicable). If this is set to `30`, the content will stop being shown on day 31 of their paid membership; i.e., show until (and including) day 30; stop showing after day 30. If you leave this empty, the drip is not turned off once it is turned on. In other words, if you only set a `from_day` and exclude `to_day`, the drip begins on `from_day` and remains on.
-   `level` *(deprecated in s2Member Pro v140520, please use `access` instead)*. This indicates which Membership Level is required for the content to be dripped. A paying member must be at this Membership Level (or higher) for the content inside the shortcode tags to be displayed. If you leave this empty, Membership Level `0` is used as the default value (i.e., a Free Subscriber would have access).

Since v140520, a new attribute is available for `[s2Drip]`. It is the `access` attribute (as documented above). This new attribute makes it possible for you to use s2Member access capabilities to do the content drip. You can use `leveln` (*n*: number) for level capabilities, or `ccap_name` for Custom Capabilities, e.g., `level2` or `ccap_music`. You can combine them using `AND` / `OR` logic, and grouping with parenthesis is also possible: `"level3 OR (level2 AND ccap_music)"`.

_**NOTE:** The use of `[s2Drip]` requires s2Member Pro._

_**WARNING:** `[s2Drip]` will **not** work as expected when testing against an Administrator who is logged in. While Administrators do gain full access to all content, Administrators generally do **not** have a paid registration time; i.e., they are not an actual customer. Therefore, please do **not** test this as an Administrator, you WILL be confused :-) Administrators will **always** see the content, no matter what Shortcode Attributes you define._
