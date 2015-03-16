---
title: How can I debug my payment gateway integration?
categories: questions
tags: troubleshooting
author: brucewsinc
github-issue: https://github.com/websharks/s2member-kb/issues/70
---

### Enable s2Member's Logging Routines

If you're having problems with Payment Buttons or Pro-Forms, the first step is to turn on s2Member's logging routines. This is an easy way to debug s2Member. Please see: **_Dashboard ⥱ s2Member ⥱ Log Files (Debug) ⥱ Logging Configuration_**

s2Member's log files will report any problems encountered during payment processing, along with additional data and a dump of all runtime variables. This information can be helpful to developers and/or s2Member support representatives. This step (i.e., turning on s2Member's logging routines) is all that's needed to unveil most issues encountered during payment processing.

### Dealing w/ Other Edge Cases

In cases where s2Member's ability to log issues is hindered, or if all you're getting is just a "white screen", you'll need to move your attention to WordPress itself. If there are no issues reported in s2Member's log files and you're still having a problem, the most likely cause is a server misconfiguration, or a plugin that is interfering with s2Member's ability to operate as intended.

### Additional Recommendations

- Run the [s2Member Server Scanner](https://github.com/websharks/s2member-kb/issues/133).
- If that turns up nothing, please see: [Testing in a Clean Installation](https://github.com/websharks/s2member-kb/issues/81).
- You can also try [`WP_DEBUG`](http://codex.wordpress.org/WP_DEBUG) mode. Please see [this article](http://codex.wordpress.org/WP_DEBUG) at WordPress.org for more information.
