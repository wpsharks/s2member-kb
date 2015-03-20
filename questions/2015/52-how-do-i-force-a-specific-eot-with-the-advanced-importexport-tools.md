---
title: How do I force a specific EOT with the Advanced Import/Export Tools?
categories: questions
tags: import-export-tools
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/52
toc-enable: off
---

If you want to force a specific EOT (End of Term) for multiple users, you can use the [Advanced Import/Export Tools](http://s2member.com/kb/kb-q/importing/) to export your users, edit the resulting CSV file, and then add the new EOT value. When you import the modified CSV file, the users' EOT times will be updated.

Here's an example that modifies the EOT time for two users (IDs `123` and `456`):

```text
"ID", "meta_key__wp_s2member_auto_eot_time"
"123", "1406281258"
"456", "1406222258"
```

_EOT = End of Term. This is given as a UNIX timestamp. See details below regarding this Meta Field._

**`meta_key__wp_s2member_auto_eot_time`** This is one of the _most_ useful fields when importing users from another/previous membership platform. If you fill this field in (it’s a UNIX timestamp), you are telling s2Member to terminate account access at that specific time. This is extremely helpful when you import customers from another membership platform into s2Member. For instance, if you don’t care to deal with the hassle of synchronizing all of the accounts (or if that just isn’t possible), you can simply flag each of your past account holders with an expiration time at which they will lose membership access in the new system. **Tip:** this field is also editable in the s2Member UI. Click `[edit]` next to any user, then scroll down to edit this field for a particular user.

### UNIX Timestamps vs Regular Dates

The important thing to note here is that unlike the editing a user's EOT from inside WordPress (where you click [edit] next to a user and then scroll down to the EOT field and change the value), you cannot enter regular dates like `04/12/2015` into the CSV file. 

When supplying the EOT value in the CSV file, the EOT value **must** be in a UNIX Timestamp format (e.g., you would supply the UNIX Timestamp of `1428796800` for `04/12/2015 12:00 AM GMT`).

There are many sites out there that can help you generate UNIX Timestamps. Here's one: http://www.unixtimestamp.com/

### Minimum CSV Fields Required for Modifying the EOT Value

The minimum required fields to modify the EOT for a user via a CSV file are as follows:

```text
"ID", "meta_key__wp_s2member_auto_eot_time"
"123", "1406281258"
"456", "1406222258"
```

The minimum required CSV fields for updating the EOT time for a user are the user's `ID` and the `meta_key__wp_s2member_auto_eot_time` field (the EOT time in UNIX Timestamp format). If any additional fields are included, those fields will also be updated (if they were modified) when you import the CSV file.
