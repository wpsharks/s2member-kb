---
title: Protecting ALL Posts/Pages
categories: tutorials
tags: restriction-options
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/156
---

## Protect ALL, But With Exceptions?

Do you have 100’s or even thousands of WordPress Posts or Pages? Trying to protect them ALL in one shot? Hmm, but maybe you want to make a few exceptions; i.e., maybe not really _all_ of them?

## Avoid Using the `all` Keyword for Posts/Pages

A common mistake when you attempt to protect all Posts or all Pages, is to use s2Member's Post/Page  Restriction Options. While this does make it quite easy to protect everything, because the instructions here show that you can simply type the special keyword `all` to protect everything; it does _not_ allow for any exceptions to be made now or in the future. For that reason, please try to avoid using the `all` keyword when there are in fact exceptions to the rule.

## TIP: Protect Content Using WordPress Tags

Instead of using the `all` keyword in s2Member's Restriction Options, consider changing the way you protect content. For this, we move to s2Member's Tag Restriction Options. See: **s2Member ⥱ Restriction Options ⥱ Tag Access Restrictions**

Here we can say that any Post with a certain tag will be protected. This makes it easy for us to protect content in ways that allow for greater flexibility. For instance, if you protect the tag `members only` (just an example tag), then you simply add this tag to ALL Posts that should be protected, but then exclude those few exceptions that should not be protected, by simply not giving some Posts the protected tag.

This works for Pages too. See: [Tag Pages plugin](https://wordpress.org/plugins/tag-pages/)

## Adding Tags to ALL Posts is Easy

Adding tags to lots of Posts at once is easy if you use the built-in Bulk Editing tools provided by WordPress. Screenshot example below.

[![2015-03-11_21-52-15](https://cloud.githubusercontent.com/assets/1563559/6612884/254be544-c839-11e4-84f2-2d4f9fa51242.png)](https://cloud.githubusercontent.com/assets/1563559/6612884/254be544-c839-11e4-84f2-2d4f9fa51242.png)

_See also: [Custom Bulk Edit plugin](https://wordpress.org/plugins/custom-bulkquick-edit/)._
