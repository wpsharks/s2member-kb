---
title: How do I manually uninstall s2Member?
categories: questions
tags: troubleshooting, uninstalling
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/227
---

Uninstalling s2Member is easy. It uninstalls like any other plugin in WordPress. Just "deactivate" s2Member and then "delete" the plugin from your WordPress Dashboard. If you're running s2Member Pro, log in via FTP and delete the `s2member-pro` add-on directory also.

*Having said that, s2Member is a larger/complex plugin that packs a lot of functionality. Therefore, whenever you uninstall it there are a few things that you might want to consider.*

## Plugin Deletion Safeguards

Whenever you deactivate and delete s2Member, if you want s2Member to *completely* erase all of its options, WordPress Roles, log files, etc...; please be sure to disable *Plugin Deletion Safeguards* first.

See: **Dashboard → s2Member → General Options → Plugin Deletion Safeguards**

**QUESTION: If I turn Plugin Deletion Safeguards off, will s2Member also delete members? i.e., my users? What data is being guarded when this is on?**

No. s2Member will never delete users. Here is a list of the things that s2Member deletes whenever Plugin Deletion Safeguards have been turned off before an uninstall occurs.

- s2Member-generated Roles in WordPress; e.g., s2Member Level1, s2Member Level 2, etc. Note that the "Subscriber" Role is also used by s2Member, but that Role is actually a part of the WordPress core, so it is left intact.

- s2Member plugin configuration options; e.g., payment gateway credentials, restriction options, coupon codes, tax configuration data, custom registration/profile fields generated with s2Member, etc.

- s2Member-related CRON jobs are terminated; e.g., the Auto-EOT system.

- s2Member-related plugin directories; e.g., `s2member-files`, `s2member-logs`, etc.

- s2Member-related transient values that are stored in the WordPress database; e.g., IPN processing history, simultaneous login monitoring data, and other temporary/transient data that s2Member uses.

- s2Member-related metadata; i.e., data that is attached to user accounts, or to specific posts/pages in WordPress. For instance, the Paid Subscr. ID for each customer, the payment gateway they used, the CCAPs they have, their EOT time, etc. In the case of posts/pages, s2Member will drop restriction options, CCAP requirements, and things like `s2member_force_ssl`. These bits of information are only used by s2Member, and therefore it is all deleted when s2Member is removed.

## s2Member Folders

- The default folder path to the s2Member folders is: `/wp-content/plugins/`

- `/wp-content/plugins/s2member` contains the s2Member Framework -- it **is** the s2Member plugin. It is safe to remove this folder (and its contents) as part of the uninstall process. In fact, WordPress should remove this automatically whenever you deactivate and delete the plugin from your WordPress Dashboard.

- `/wp-content/plugins/s2member-files` is generated automatically by s2Member. It is usually okay to just delete this folder and its contents as part of the uninstall. In fact, s2Member will do this for you automatically with *Plugin Deletion Safeguards*disabled. However, the purpose of this directory is for it to contain protected file downloads that you offer members. 

     - If s2Member sees that you've placed any files in this directory, it will be left as-is for your review; i.e., you will need to remove it manually. If you find that to be the case, it's worth a quick review of what this directory contains before you delete it. In other words, make sure you're not deleting downloadable files that you intend to keep as part of your offering to users.

- `/wp-content/plugins/s2member-logs` is generated automatically by s2Member. You can usually just delete this folder and its contents as part of the uninstall and s2Member will do this for you automatically with *Plugin Deletions Safeguards* disabled. However, if you find that it still exists for some reason, it might be worth a quick review before you delete it. Just check to see if there are any archived log files in this directory that you care about, and back those up before you wipe them away.

- `/wp-content/plugins/s2member-pro` contains all of the s2Member Pro add-on files; e.g., additional payment gateway integrations and code that powers pro-only features in s2Member. It is safe to remove this folder (and its contents) as part of the uninstall process.

## Complete Uninstall or File Replacement?

You've decided you need to uninstall s2Member for some reason. Now you want to know the best way to do that. The first question: Do I need to retain my s2Member data? If the answer is "No" and you never plan to look back, uninstalling is pretty straight-forward. 

### Completely Uninstall s2Member Files and Data

If you've decided you are never going to use s2Member again, you should completely remove all files and data associated with the plugin. Keep in mind that if you follow this path and change your mind about using s2Member, you will have to reinstall and reconfigure everything. So be sure this is what you want to do, especially if you've been using s2Member for some time and have it deeply woven into your website.

1. Backup your files and database. (You can **never** say you will never look back!)
1. Disable s2Member *Plugin Deletion Safeguards*: **WordPress Dashboard → s2Member → General Options → Plugin Deletion Safeguards**. Set to "No (upon deletion, erase all data/options)".
1. Navigate to **WordPress Dashboard → Plugins**.
1. Deactivate the *s2Member Framework* plugin.
1. Delete the *s2Member Framework* plugin. Select "Yes, Delete these files and data" when prompted.
1. Using your preferred method of file access on your web server, delete the `/wp-content/plugins/s2member-pro/`directory. This should be the only s2Member directory remaining if you followed the instructions above. If it is not, review the **s2Member Folders** section above and delete the remaining folders after careful review of their contents as described.

### Remove the Plugin in Order to Reinstall

If you're having some problems with s2Member and need to remove and reinstall the plugin, follow this checklist:

1. Backup your files and database. 
1. Enable s2Member *Plugin Deletion Safeguards*: **WordPress Dashboard → s2Member → General Options → Plugin Deletion Safeguards**. Set to "Yes (safeguard  all data/options)".
1. Navigate to **WordPress Dashboard → Plugins**.
1. Deactivate the *s2Member Framework* plugin.
1. Delete the *s2Member Framework* plugin. Select "Yes, Delete these files and data" when prompted.
1. Using your preferred method of file access, delete the following directories on your web server:
	- `s2member`
	- `s2member-pro`
1. Make another backup of your files and database. 

Now you can reinstall *s2Member* and *s2Member (Pro). (Don't forget to make another backup when you're finished! :) )