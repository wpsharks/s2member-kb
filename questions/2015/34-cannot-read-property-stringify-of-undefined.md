---
title: Cannot read property 'stringify' of undefined?
categories: questions
tags: troubleshooting,error-messages
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/34
---

> On creation of new field "test123" the JavaScript Console reports:  `Uncaught TypeError: Cannot read property 'stringify' of undefined ws_plugin__s2member_menu_pages_js`

> I also get Server Error 500 when attempting to load images brand-xlink.png & add-icon.png.

I have seen this reported in the past and the two errors that you are experiencing are most likely connected to each other. If you look again I'm betting that you will also find JavaScript/CSS files in the developer console that are returning a `500` (or other) error status too.

That would explain why you are seeing the `stringify` error, as the underlying JavaScript/CSS resources are failing to load. There are also high odds that the s2Member UI looks bad in this case; i.e., not what was intended for you to see in the Dashboard.

Please see: [How to Correct 500 Internal Server Errors](https://github.com/websharks/s2member-kb/issues/35)