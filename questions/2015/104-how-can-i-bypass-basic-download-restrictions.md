---
title: How can I bypass the Basic Download Restrictions?
categories: questions
tags: basic-download-restrictions, s2file, s2stream, shortcodes
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/104
---

**Question:** How can I bypass the Basic Download Restrictions?

**Answer:** If you want to use the `[s2File /]` or `[s2Stream /]` shortcodes and you don't want to specify download restrictions in `s2Member ⥱ Download Options ⥱ Basic Download Restrictions` (i.e., you want to bypass Basic Download Restrictions), simply add `check_user="no"` to your shortcode attribute.

If you serve files using a File Download Key (see `s2Member ⥱ Download Options ⥱ Advanced Download Restrictions`), the Basic Download Restrictions will always be bypassed.

See also: **s2Member ⥱ Download Options ⥱ Shortcode Attributes & API Functions (Explained)**
