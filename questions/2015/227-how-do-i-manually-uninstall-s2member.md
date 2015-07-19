---
title: How do I uninstall s2Member?
categories: questions
tags: troubleshooting, uninstalling
author: patdumond
github-issue: https://github.com/websharks/s2member-kb/issues/227
---

Uninstalling s2Member is easy. It uninstalls like any other plugin in WordPress. Just "deactivate" s2Member and then "delete" the plugin from your WordPress Dashboard. If you're running s2Member Pro, log in via FTP and delete the `s2member-pro` add-on directory also.

*Having said that, s2Member is a larger/complex plugin that packs a lot of functionality. Therefore, whenever you uninstall it there are a few things that you might want to consider.*

## Plugin Deletion Safeguards

Whenever you deactivate and delete s2Member, the plugin will check your Plugin Deletion Safeguards setting. If you want s2Member to *completely* erase all of its options, WordPress Roles, log files, etc...; please be sure to disable *Plugin Deletion Safeguards* first.

See: **Dashboard → s2Member → General Options → Plugin Deletion Safeguards**

If you leave Plugin Deletion Safeguards enabled (the safest and default setting), s2Member will leave all of the s2Member options and related membership data inside your WordPress database. That way, if you reinstall s2Member later, all of your existing configuration will be restored.

To backup your s2Member configuration for use later, you can use the s2Member Pro Import/Export feature; see **Dashboard → s2Member → Import / Export → s2Member Options (Import/Export)** (this is an s2Member Pro-only feature). Note, however, that this only backs up your s2Member plugin configuration; it does not backup any s2Member-related user configuration. If you want to back up user configuration, you must back up your entire WordPress database. See https://codex.wordpress.org/WordPress_Backups.

### Will uninstalling s2Member delete my existing members?

No. Even if you disable the Plugin Deletion Safeguards, **s2Member will never delete users**. However, some s2Member-related user information _will_ be lost when Plugin Deletion Safeguards have been turned off (if you leave Plugin Deletion Safeguards enabled, then no s2Member-related user information will be lost). 

### What is deleted when Plugin Deletion Safeguards are disabled? 

Here is a list of the things that s2Member deletes during the uninstallation process whenever Plugin Deletion Safeguards have been turned off.

- s2Member-generated Roles in WordPress; e.g., s2Member Level1, s2Member Level 2, etc. Note that the "Subscriber" Role is also used by s2Member, but that Role is actually a part of the WordPress core, so it is left intact.

- s2Member plugin configuration options; e.g., payment gateway credentials, restriction options, coupon codes, tax configuration data, custom registration/profile fields generated with s2Member, etc.

- s2Member-related CRON jobs are terminated; e.g., the Auto-EOT system.

- s2Member-related plugin directories; e.g., `s2member-files`, `s2member-logs`, etc.

- s2Member-related transient values that are stored in the WordPress database; e.g., IPN processing history, simultaneous login monitoring data, and other temporary/transient data that s2Member uses.

- s2Member-related metadata; i.e., data that is attached to user accounts, or to specific posts/pages in WordPress. For instance, the Paid Subscr. ID for each customer, the payment gateway they used, the CCAPs they have, their EOT time, etc. In the case of posts/pages, s2Member will drop restriction options, CCAP requirements, and things like `s2member_force_ssl`. These bits of information are only used by s2Member, and therefore it is all deleted when s2Member is removed.

## How do I completely remove all s2Member files and data?

If you've decided you are never going to use s2Member again, you should completely remove all files and data associated with the plugin. Keep in mind that if you follow this route and then later change your mind about using s2Member, you will have to reinstall and reconfigure everything. So be sure this is what you want to do, especially if you've been using s2Member for some time and have it deeply woven into your website.

1. Backup your files and database. (You can **never** say you will never look back!)
1. Disable s2Member *Plugin Deletion Safeguards*: **WordPress Dashboard → s2Member → General Options → Plugin Deletion Safeguards**. Set to "No (upon deletion, erase all data/options)".
1. Navigate to **WordPress Dashboard → Plugins**.
1. Deactivate the *s2Member Framework* plugin.
1. Delete the *s2Member Framework* plugin. Select "Yes, Delete these files and data" when prompted.
1. Using your preferred method of file access on your web server, delete the `/wp-content/plugins/s2member-pro/`directory. This should be the only s2Member directory remaining if you followed the instructions above. If it is not, review the **s2Member Folders** section above and delete the remaining folders after careful review of their contents as described.

## How do I reinstall s2Member and save existing configuration?

If you're having some problems with s2Member and you just need to remove and reinstall the plugin, follow this checklist:

1. Backup your files and database. See https://codex.wordpress.org/WordPress_Backups
1. Enable s2Member *Plugin Deletion Safeguards*: **WordPress Dashboard → s2Member → General Options → Plugin Deletion Safeguards**. Set to "Yes (safeguard  all data/options)".
1. Navigate to **WordPress Dashboard → Plugins**.
1. Deactivate the *s2Member Framework* plugin.
1. Delete the *s2Member Framework* plugin. Select "Yes, Delete these files and data" when prompted.
1. Using your preferred method of file access (e.g., FTP), delete the following directories on your web server inside the WordPress plugins directory:
	- `s2member`
	- `s2member-pro`
1. Make another backup of your files and database. 

Now you can reinstall **s2Member Framework** and **s2Member (Pro)**. See [s2Member Installation](http://s2member.com/installation/). (Don't forget to make another backup when you're finished! :) )

## What are the s2Member Folders / Directories?

`/wp-content/plugins/`

- This is where all of your WordPress plugins live. This is the default path to all of the s2Member directories.

`/wp-content/plugins/s2member`

- The `s2member` directory contains the s2Member Framework--this is the s2Member plugin itself (i.e., the s2Member Framework). It is safe to remove this folder (and its contents) as part of the uninstall process. In fact, WordPress should remove this automatically whenever you deactivate and delete the plugin from your WordPress Dashboard.

`/wp-content/plugins/s2member-files` 

- The `s2member-files` directory is generated automatically by s2Member. It's usually okay to just delete this folder and its contents as part of the uninstall process. In fact, s2Member will do this for you automatically when **Plugin Deletion Safeguards** are disabled. However, the purpose of this directory is to store file downloads that you want to have protected by s2Member. 

     **Note:** If s2Member sees that you've placed any files in the `s2member-files` directory when you uninstall s2Member, it will be left as-is for your review; i.e., you will need to remove it manually. If you find that to be the case, it's worth a quick review of what this directory contains before you delete it. In other words, make sure you're not deleting downloadable files that you intend to keep as part of your offering to users.

`/wp-content/plugins/s2member-logs` 

- The `s2member-logs` directory is generated automatically by s2Member. You can usually just delete this folder and its contents as part of the uninstall. s2Member will do this for you automatically when **Plugin Deletions Safeguards** are disabled. However, if you find that it still exists for some reason, it might be worth a quick review before you delete it. Just check to see if there are any archived log files in this directory that you care about, and back those up before you wipe them away.

`/wp-content/plugins/s2member-pro` 

- The `s2member-pro` directory contains all of the s2Member Pro add-on files; e.g., additional payment gateway integrations and code that powers pro-only features in s2Member. It is safe to remove this folder (and its contents) as part of the uninstall process.
