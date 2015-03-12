---
title: Are Basic Download Restrictions required?
categories: questions
tags: download-options, basic-download-restrictions
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/77
---

> The s2Member configuration on the website for Basic download restrictions is empty - as I am not using any membership levels as of yet. So I am only using the specific post/page access with payment  buttons and the download key for the actual file link on the page. Why are Download Links not working?

For security purposes, s2Member's File Download functionality is disabled unless and until you explicitly enable File Downloads by configuring at least one of s2Member's Basic Download Restrictions.

Since you're not using Membership Levels for this at all, here's what I suggest.

![2015-02-02_11-23-51](https://cloud.githubusercontent.com/assets/1563559/6008445/042da434-aace-11e4-9aac-d732d8b795e3.png)

This will enable s2Member's File Download functionality so that it works for Specific Post/Page Access, as well as provide unlimited download access for anyone with s2Member Level 0. Since you're not using s2Member Levels at all in this scenario (i.e., you're only using Specific Post/Page access), the "unlimited download access" won't have any effect but Specific Post/Page Access download links will now work as expected.