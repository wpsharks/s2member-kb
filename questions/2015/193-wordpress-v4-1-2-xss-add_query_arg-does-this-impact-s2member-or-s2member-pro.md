---
title: WordPress v4.1.2 XSS (add_query_arg); does this impact s2Member or s2Member Pro?
categories: questions
tags: 
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/193
---

Referencing [Security Advisory: XSS Vulnerability Affecting Multiple WordPress Plugins](https://blog.sucuri.net/2015/04/security-advisory-xss-vulnerability-affecting-multiple-wordpress-plugins.html)

> Does the recent " XSS Vulnerability Affecting Multiple WordPress Plugins" affect s2member? Has anyone checked the code?

---

The WordPress security team has said that they did a review of the top 100-300 plugins and that they are continuing to look for vulnerable plugins. s2Member is in that list of top plugins. As of right now (to our knowledge), s2Member has not been found to contain any code which would make it vulnerable in this way, no.

However, we are, of course, doing our own review of the codebase for both s2Member and s2Member Pro. In our research thus far, we find no calls to `add_query_arg()` or `remove_query_arg()` that are left unescaped—whether they include argument 2 or not; i.e., whether they use `$_SERVER['REQUEST_URI']` or not.

Having said that, we will continue to research this, as always. Security is a top priority in the s2Member plugin. Each new release of s2Member is tweaked and tuned for improved security, and we are looking at ways to further improve security in calls to `add_query_arg()` and `remove_query_arg()` for the next release. Please keep tabs on our [changelog](http://s2member.com/changelog/) for further details.