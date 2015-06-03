---
title: Manually Deactivating s2Member
categories: tutorials
tags: troubleshooting
author: brucewsinc
github-issue: https://github.com/websharks/s2member-kb/issues/71
---

If you think s2Member is causing issues with your website, or if you've been blocked by s2Member's Brute Force IP/Login Restrictions, you may find it necessary to manually disable s2Member.

Should the need arise, the easiest method of disabling s2Member (or any other plugin) is to rename the directory that s2Member resides in on your server. To do that, you'll need to use an FTP client. We recommend [FileZilla™](http://filezilla-project.org/).

s2Member is located in your `wp-content/plugins` directory. If you're using s2Member Pro, you only need to disable the s2Member Framework; i.e., this disables both s2Member and s2Member Pro.

![screen shot 2015-01-28 at 2 13 46 am](https://cloud.githubusercontent.com/assets/1568616/5933808/a1d50c3e-a693-11e4-973b-a4841d3d80b0.png)

Once you fix the issue, you can **restore the original directory name** of `s2member` (don't forget this part), then renable s2Member via the WordPress Dashboard.
