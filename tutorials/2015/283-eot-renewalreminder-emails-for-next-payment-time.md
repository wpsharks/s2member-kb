---
title: EOT Renewal/Reminder Emails for Next Payment Time
categories: tutorials
tags: mu-plugins-hacks, eot-time
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/283
---

By default, EOT Renewal/Reminder Email notifications that you configure with s2Member are only sent to customers who will be expiring soon, and not to those who simply have another payment due; i.e. if your customers are on a recurring plan, they [don't have a fixed EOT Time](http://s2member.com/kb-article/when-is-an-eot-time-set-for-each-user/), because their access continues for as long as they keep paying you.

**However**, it is possible to alter the behavior of EOT Renewal/Reminder Email notifications, so that your reminder will go out to customers who have another upcoming payment due also. This requires an MU Plugin file to alter the behavior in this way.

Create this directory and file:
`/wp-content/mu-plugins/s2-hacks.php`

```php
<?php
add_filter('ws_plugin__s2member_options', function($options) {
    $options['pro_eot_reminder_email_on_npt_also'] = '1';
    return $options;
});
```

**Warning:** If you apply this hack, you will need to consider that EOT Renewal/Reminder Email notifications will now be sent for both purposes.

1). If customers are about to expire.
2). If customers have another payment due soon.

For this reason, (depending on what you sell), you may need to design the email notification in such a way that a single email can serve both purposes. For some sites (depending on what you sell) that may not be possible. We are working to add a separate customizable email in a future version of s2Member Pro for that reason. Thanks for your patience.