---
title: Troubleshooting the Pro Updater
categories: tutorials
tags: pro-updater, troubleshooting
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/158
---

> Upgrade failed. Connection failed (please try again).

This would indicate that s2Member had an issue connecting to the WebSharks update server. It's possible that your web server is blocking the connection, or that some security software (such as ModSecurity) is blocking the requests.

I recommend contacting your web host and asking them to check the log files to see if any requests to `s2member.com` are being blocked.