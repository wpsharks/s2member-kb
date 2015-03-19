---
title: Verify PayPal IPN w/ 3rd-party application using Proxy Key?
categories: questions
tags: api-scripting,paypal,mu-plugins-hacks
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/29
---

> Question: What I've planned to do is place an IPN script (similar to the one that comes with s2Member pro account as an extra), and set a custom payment gateway notification url to that IPN script. Now it seems the connection is happening, but there is a problem w/ post vars verification.

You can avoid this problem by passing your Proxy Key, which will automatically verify the incoming IPN; i.e., since it not actually from PayPal, s2Member needs you to pass the Proxy Key. Please see: **Dashboard → s2Member → PayPal Options → IPN Integration**. There you will find a link that expands another section with additional details and an IPN URL which already contains the Proxy Key that you need.

![](https://cloud.githubusercontent.com/assets/1563559/5744661/2be85fb8-9bcf-11e4-8b8a-869310d14416.png)