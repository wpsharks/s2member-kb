---
title: How to Correct 500 Internal Server Errors
categories: tutorials
tags: error-messages,troubleshooting
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/35
toc-enable: false
---

Unfortunately, the solution is not the same for everyone. What might be causing 500 errors on your server could be different from what causes this on another.

##### Possible causes of 500 internal server error:

- Missing files; i.e. a corrupted installation of s2Member or s2Member Pro. I'd suggest a full reinstall of the s2Member plugin to rule this out.

- Apache compatibility. s2Member comes with several `.htaccess` files that require Apache 2.1 or higher, or an Apache-compatible web server. If one or more of the rules set by s2Member in its `.htaccess` files are not possible in your environment, this could result in a 500 internal server error. Inspecting your Apache error log on your own, or with help from your hosting company, will be a first step to identifying the specific line in a specific `.htaccess` file that is causing problems. Upgrading to a newer version of Apache may also be a route to explore.

- Server-side permission issues. If your host refuses to serve files from `/wp-content/plugins/s2member` when/if the files in this directory do not have the expected permission settings, this could result in a 500 internal server error. It's best to seek assistance from your hosting company to resolve this. Ask, "why does this link produce a 500 internal server error?"; attaching an example link to one of the s2Member files that result in a 500 internal server error.