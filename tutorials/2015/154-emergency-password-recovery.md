---
title: Emergency Password Recovery
categories: tutorials
tags: troubleshooting
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/154
---

**[This article at WordPress.org](http://codex.wordpress.org/Resetting_Your_Password)** already covers quite a few scenarios. Very helpful in an emergency situation. However, since s2Member is so tightly integrated with WordPress (when it comes to user access) we thought it might help to cover emergency password recovery in greater detail and provide a few suggestions of our own.

### Easiest Way to Recover a Lost Password

**If you simply forgot your password,** you should able to use the “Lost Password” functionality that is already provided by WordPress via `/wp-login.php?action=lostpassword`. Simply visit that URL on your site and WordPress will allow you to reset your password via email confirmation.

![](http://cdn.websharks-inc.com/s2member/uploads/2014/07/2014-07-02_13-17-021.jpg){.aligncenter}

**If you lost access because of a theme or plugin malfunction/conflict** you should consider restoring your WordPress database from an earlier snapshot; i.e., before your access was lost. We suggest this because if you lost access as the result of a theme/plugin malfunction there is a good chance that your WordPress Roles/Capabilities have been corrupted. That’s not always the case, but restoring your database would be the safest bet. **If database restoration is not an option**, please follow the advice presented by [this article](http://codex.wordpress.org/Resetting_Your_Password). We suggest going with the phpMyAdmin option that is detailed in the article.

#### A Quick Summary of the Actions Required

-   Access your WordPress database via phpMyAdmin. Just about every web host will offer you this tool. Please check your web hosting control panel for phpMyAdmin and access it through your browser.
-   Open the `wp_users` table, edit your user account. You can find yourself by username. Usually admin, or user ID `1`. Click to edit that row in the database.
-   Change the password to what you like (making sure to choose the MD5 hash option from the select menu there). The screenshot below should help to clarify this last step nicely. You should enter your password in plain text. Choosing MD5 will hash the plain text for WordPress automatically.

![](http://cdn.websharks-inc.com/s2member/uploads/2014/07/2014-06-30_23-48-51.jpg){.aligncenter}
