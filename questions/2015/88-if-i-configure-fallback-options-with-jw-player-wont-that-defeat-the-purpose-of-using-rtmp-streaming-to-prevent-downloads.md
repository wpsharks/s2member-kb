---
title: If I configure fallback options with JW Player, won't that defeat the purpose of using RTMP streaming to prevent downloads?
categories: questions
tags: download-options, jw-player, rtmp, s2stream
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/88
---

As long as you set things up as instructed in the s2Member documentation, the downloads are always protected by s2Member File Download Restrictions. This includes the files you configure as fallback options for JW Player.

When you're using RTMP Streaming and you have fallback options configured, those fallback options will only be used if JW Player is unable to use the RTMP option. It's true that enabling the fallback options will increase the chances that somebody could trick JW Player into forcing one of the fallback options and then possibly gain access to downloading the video (even then, they'd still need to have s2Member permissions to do so), but the benefits of configuring fallback options are that you increase compatibility across multiple devices. 

You'll need to weigh your options and decide if preventing downloads as much as possible (using RTMP-only) is more or less important than providing a wide range of compatibility across multiple types of devices to ensure that your video plays no matter where it's being viewed from.

Related article: [`[s2Stream /]` Shortcode Documentation](https://github.com/websharks/s2member-kb/issues/126)