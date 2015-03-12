---
title: How do I configure Basic Download Restrictions for unlimited RTMP streaming?
categories: questions
tags: download-options, rtmp, jw-player, basic-download-restrictions
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/93
---

**Question:** How do I configure Basic Download Restrictions for unlimited RTMP streaming?

**Answer:** s2Member does not differentiate between regular file downloads and RTMP streaming; when you play an RTMP stream, it is considered by s2Member as a file download. 

If you want to allow unlimited RTMP streaming, you should configure `s2Member ⥱ Download Options ⥱ Basic Download Restrictions` for unlimited file downloads at the applicable level.

For example, to allow unlimited streaming for Level 1, you should configure File Downloads for Level 1 to `999999999` every `365` days:

![2015-02-07_13-57-04](https://cloud.githubusercontent.com/assets/53005/6093542/38599f04-aed1-11e4-9c01-936e8ec8a027.png)

#### But what if I don't want to allow file downloads?

If you don't want to allow file downloads at all, you'll need to configure your player or `[s2Stream /]` shortcode to use RTMP streaming-only, without any fallback options. 

That will prevent users from gaining access to the original MP3 or MP4 file. However, not configuring fallback options also decreases compatibility across devices. You'll need to decide which is more important: preventing downloads at all cost, or maximizing playback compatibility across various devices (such as phones and tablets).

Related: [If I configure fallback options with JW Player, won't that defeat the purpose of using RTMP streaming to prevent downloads?](https://github.com/websharks/s2member-kb/issues/88)


#### What if I don't want file downloads counted against the user's allotted amount?

If you don't want file downloads (including each time an RTMP-stream is played) counted against the user's total allotted amount, you can pass `count_against_user="no"` in your `[s2File /]` and/or `[s2Stream /]` shortcode.

#### What if I don't want s2Member to check the user's download permissions at all?

Please see [How can I bypass the Basic Download Restrictions?](https://github.com/websharks/s2member-kb/issues/104)