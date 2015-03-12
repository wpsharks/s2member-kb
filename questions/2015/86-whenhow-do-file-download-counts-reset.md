---
title: When/how do download counts reset?
categories: questions
tags: download-options, basic-download-restrictions
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/86
---

> I just need to know from what point do they reset. Date of registration, date of first download, first day of the month etc.

## Basic Download Restrictions

s2Member's Basic Download Restrictions are configured in this area of the Dashboard.

![2015-02-05_08-56-24](https://cloud.githubusercontent.com/assets/1563559/6065850/f3d91a02-ad14-11e4-946a-c3ff275eee08.png)

So let's take the following example. I will allow Members at Level 1 to download up to `30` files every `7` days. When do the counts reset? It's different for each Member.

If Member ID 123 is at Level 1, and they download one file today (their first download), they have the rest of today, and then another 6 days to download up to 29 more files. At the end of the 7 day period (6 days after the day of their first download), the count will reset — for them.

So the timer starts when their first download takes place, and then it stops (resets) X number of days later, depending on the way you configure s2Member's Basic Download Restrictions.

## Unique Downloads Only

Repeated downloads of the same exact file are not tabulated against the total count. Once a file has been downloaded, future downloads of the same exact file, by the same exact Member will not be counted against them. In other words, if a Member downloads the same file three times, the system only counts that as one unique download.

In addition, multiple variations of popular media formats are only counted once. This is because many site owners provide multiple download options to their Users/Members, for compatibility purposes. Files that have the same exact name, with one of these extensions, will only be counted one time: `avi`,`wav`,`mpa`,`mpeg`,`mpv`,`mps`,`m1v`,`m2v`,`mp4`,`mp3`,`m3u`,`flv`,`f4v`,`3gp`,`3g2`,`aac`,`m4a`,`webm`,`ogg`,`ogv`,`pls`,`ogm`,`m4u`,`mov`,`qtl`,`asf`,`wmv`,`wvx`,`wma`,`wax`,`ra`,`rm`,`ram`.