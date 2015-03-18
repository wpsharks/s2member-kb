---
title: Common Troubleshooting Tips
categories: tutorials
tags: troubleshooting
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/132
---

We’ve seen a few common problems that site owners run into when using the s2Member plugin. For that reason we’ve compiled a list of common troubleshooting tips that should help you find and correct these problems quickly.

_**Important Note:** Each of the sections below rely on you having the latest up-to-date version of s2Member and s2Member Pro. We also expect that you will conduct your tests and perform all troubleshooting actions in a default/clean installation of WordPress; i.e., if you are having trouble, **the very first thing you should do is isolate your installation of s2Member**. Please see: [Testing in a Clean Installation](https://github.com/websharks/s2member-kb/issues/81)_

---

## Safety First (Always Have a Backup)

Before we get into the troubleshooting tips it’s important to note that you should **always have a backup** of your WordPress installation. Please see [WordPress Backups](http://codex.wordpress.org/WordPress_Backups) for more information. If something goes wrong you can always revert to the backup and start over. However, if there is no backup it may be a lot harder to recover from a problem. Backups are very important.

Also, to protect your s2Member settings and data during updates or reinstallation, please make sure you have s2Member's "Plugin Deletion Safeguards" enabled. See: **Dashboard → s2Member → General Options → Plugin Deletion Safeguards** for more information.

---

## Web Server Configuration or Conflicts

To test for server configuration issues and/or conflicts, please install and run the: [s2Member Server Scanner](https://github.com/websharks/s2member-kb/issues/133)

## Conflicting Plugins (or a Conflicting Theme)

Please review this article carefully: [Testing in a Clean Installation](https://github.com/websharks/s2member-kb/issues/81). Testing in a clean installation involves you setting up a fresh installation of WordPress; i.e., one that does _not_ include any other active plugins and it runs with a default WordPress theme. If you’re using any [Must-Use Plugins](http://codex.wordpress.org/Must_Use_Plugins), please remember to deactivate those as well.

If you test in a clean installation of WordPress and the problem does _not_ exist there, you _now_ know that a theme or plugin conflict exists on your live site. The next step is to begin installng other plugins (one-by-one, on the test installation of WordPress) until you can reproduce the same issue that you're experiencing on the live site. Reproducing a theme or plugin conflict is 90% of the work involved in resolving such a conflict. Identifying the conflicting theme or plugin will give you a few options:

- Look carefully at the configuration of a conflicting theme or plugin. Are there any config. changes you can make that might resolve the conflict? Either in the conflicting theme/plugin, or in s2Member itself?
- Is there another plugin that offers similar functionality, but perhaps does _not_ introduce a conflict?
- Have you contacted the s2Member developers and also the developers of the conflicting plugin to ask questions?

## Outdated s2Member (or s2Member Pro) Installation

The very first thing that any s2Member support representative will ask, is what version of s2Member you're running. We ask that you install the latest up-to-date copy of both s2Member and s2Member Pro. Bug are reported daily and issues with the s2Member software are fixed and pushed out in each new release of the software.

For this reason, and, so that everyone is on the same page, we ask that you update to the latest available version of s2Member before reporting a bug. Simply updating to the latest available version may correct the issue that you're reporting; i.e., the issue may have already been reported by someone else. This is why it's important to keep your installation of s2Member and s2Member Pro up-to-date at all times.

- Please see: [Update Instructions](http://s2member.com/updating/)
- See also: [s2Member Unified Changelog](http://s2member.com/changelog/) for further details.

## Log Files (s2Member's Built-in Debugger)

Please see: **s2Member ⥱ Log Files (Debug) ⥱ Logging Configuration**

It's a good idea to enable s2Member's logging functionality and review log file entries on your own. s2Member's log files can help you learn more about what is going on behind-the-scenes. Are emails not being sent? Are customers not being upgraded to a paid status? Did you receive an error after checkout? Things like this are often caused by HTTP communication failures that occur behind-the-scenes. s2Member's log files will tell you (and s2Member support representatives) more about these types of problems.

_**Note:** s2Member support representatives may ask for log files so they can be reviewed carefully during their investigation. Please be sure to enable s2Member's logging functionality and have something in your logs before opening a support ticket; i.e., reproduce the issue with logging enabled please._

## Configuration Issues and/or User Error

There’s also the likely possibility that you’ve configured something wrong—which can happen to anybody, particularly when learning to use something new. User error would be determined in ways specific to the problem. So instead of explaining each possible scenario in this article, I’ll leave that to the s2Member support representative that’s working with you. If you have a question about how something works, please don’t hesitate to ask an s2Member support representative for clarification. Or you can search our [Knowledge Base](http://s2member.com/kb/) for articles related to the questions that you have.
