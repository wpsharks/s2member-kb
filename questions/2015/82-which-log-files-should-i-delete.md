---
title: Which log files should I delete?
categories: questions
tags: log-files-debug, troubleshooting
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/82
toc-enable: false
---

> In order to resolve an issue with live site we left debugging active. I now have various log files stored on the server.  Which can I or should I delete now that I have switched off logs/debugging?  I could not find this information anywhere on forum or knowledgebase.

We suggest that _all_ log files be removed being entering into a production state; i.e. once your site goes live, _all_ log files should be deleted. Please don't leave any behind.

### How can I delete _all_ log files?

Log into WordPress and go to: **s2Member ⥱ Log Files (Debug) ⥱ Logs Viewer**. There you will find a link near the top that reads, "Debugging Tools/Tips & Other Important Details". Click the link to toggle those tools, and then choose, "Permanently Delete All Log Files".

![2015-02-05_14-36-25](https://cloud.githubusercontent.com/assets/53005/6067733/a2095cf2-ad44-11e4-8d76-55d3b213a7f2.png)
