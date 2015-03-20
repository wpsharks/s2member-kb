---
title: How do I switch between multiple video resolutions using the [s2Stream /] shortcode and JW Player?
categories: questions
tags: jw-player, s2stream, shortcodes, download-options
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/102
toc-enable: off
---

The `[s2Stream /]` shortcode includes a  `player_resolutions=""` shortcode attribute. The `player_resolutions=""` shortcode attribute is a comma-delimited list of all available resolution options, which allows you to specify multiple videos, each with their own quality/resolution. This can be tricky to setup, so please read carefully. You'll also want to review and reference the [[[s2Stream /]] Shortcode Documentation](http://s2member.com/kb-article/s2stream-shortcode-documentation/).

In order to offer multiple resolution options you should make additional variations (i.e., resolutions) available by uploading those variations to the same directory where `file_download=""` lives. In addition, when you use `player_resolutions=""`, each of your files (including the one you specify in `file_download=""`) _must_ end with `-r{resolution option value}`; where `{resolution option value}` must begin with a numeric resolution (in height) followed by any label you prefer; e.g., `-r720p-HD` or maybe `-r1080p-HD`. The full file name would be something like: `video-r720p-HD.mp4`
  
**Here is a Quick Example:**

```wpsc
  [s2Stream file_download="video-r720p-HD.mp4" player_resolutions="r720p-HD,r1080p-HD,r480p-SD" player_aspectratio="16:9" /]
```

Note that each of these files _must_ exist on the server (i.e., you must create the additional resolutions and upload all of them for this to work properly). In this example I would need to render and upload the following files: `video-r720p-HD.mp4`, `video-r1080p-HD.mp4`, `video-r480p-SD.mp4`.

For video files served over HTTP, the default resolution will be the one you list first in the comma-delimited list: `player_resolutions="r720p-HD,r1080p-HD,r480p-SD"`. In this example the default resolution would be: `video-r720p-HD.mp4`.

For video files served over the RTMP protocol (i.e., `player="jwplayer-v6-rtmp"` or `player="jwplayer-v6-rtmp-only"`), the default resolution will be chosen dynamically based on the bandwidth capability of the connecting visitor; i.e., the default resolution is chosen automatically; using the best resolution possible for the device that is currently viewing the video.
  
**Tip:** When using `player_resolutions=""` it is always a good idea to also define `player_aspectratio=""`. The default aspect ratio is `16:9` if you don’t. While that default value might work for most, if your aspect ratio is different you should define it explicitly; e.g., `player_aspectratio="ww:hh"`.

---

### How does a visitor switch between the resolutions?

When you supply multiple video resolutions to the `[s2Stream /]` shortcode via the `player_resolutions=""` shortcode attribute, the default resolution will be chosen dynamically based on the bandwidth capability of the connecting visitor; i.e. the default resolution--the best resolution possible for the device that is currently viewing the video--is chosen automatically.

Visitors viewing the video from a desktop browser will see a "HD" toggle button that allows switching between High Definition (HD) and Standard Definition (SD).

![2015-03-20_14-40-14](https://cloud.githubusercontent.com/assets/53005/6758913/3e62554c-cf12-11e4-8aeb-d8c9f378580a.png)
![2015-03-20_14-39-42](https://cloud.githubusercontent.com/assets/53005/6758915/3f29d158-cf12-11e4-8a7d-c661aa3a58d0.png)

---

See also: 

- [s2Member | JW Player® w/ s2Stream Shortcodes](http://www.s2member.com/kb/jwplayer-s2stream-shortcodes/)
- [JW Player | HD Quality Toggling](http://support.jwplayer.com/customer/portal/articles/1428524-hd-quality-toggling)
