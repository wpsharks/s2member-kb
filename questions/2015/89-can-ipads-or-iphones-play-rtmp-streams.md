---
title: Can iPad's or iPhone's play RTMP streams?
categories: questions
tags: rtmp, jw-player, download-options, s2stream
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/89
toc-enable: false
---

No, the iOS operating system, which both iPads and iPhones use, is unable to play RTMP streams.

The problem is that HTML5 video tags do not support RTMP. Therefore, Flash is required for RTMP playback through JW Player, and most mobile devices do not support Flash. So providing an MP4/MP3 fallback allows JW Player to fallback on HTML5 video tags and present the raw file; i.e., without using the RTMP protocol that is currently Flash-only.

If you want iPads and iPhones to play audio/video when using RTMP streams with JW Player, you'll need to configure fallback options that will use an MP4 or MP3 file as a fallback option when RTMP streaming is not supported.

Please see the fallback examples here:
**Dashboard → s2Member ⥱ Download Options ⥱ JW Player v6 & RTMP Protocol Examples**
