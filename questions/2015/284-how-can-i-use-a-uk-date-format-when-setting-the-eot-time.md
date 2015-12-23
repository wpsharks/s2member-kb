---
title: How can I use a UK date format when setting the EOT Time?
categories: questions
tags: eot-time
author: raamdev
github-issue:
github-issue: https://github.com/websharks/s2member-kb/issues/284
---

If you are editing a users profile and setting the Automatic EOT Time, you can use any date format allowed by the [PHP `strtotime()` function](http://us3.php.net/manual/en/function.strtotime.php). However, if you try to enter the UK date format of `DD/MM/YYYY` and then save the changes, you'll notice that the format is parsed as `MM/DD/YYY` (US format), or not parsed at all.

This is due to the way that the PHP `strtotime()` function works. It assumes that if the date contains slashes then it is intended to be a date in the US format (`MM/DD/YYYY`). However, if the date is formatted using dashes or dots (`DD-MM-YYYY` or `DD.MM.YYYY`), it will parse the date as a UK date.

So when using a UK date format, please use dashes (`-`) or dots (`.`) instead of slashes (`/`).

![Automatic EOT Time: UK Format](https://cloud.githubusercontent.com/assets/53005/11969516/58171cec-a8e8-11e5-81c8-78b21ce856ae.png)
