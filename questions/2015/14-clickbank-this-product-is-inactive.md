---
title: ClickBank: "This product is inactive"?
categories: questions
tags: clickbank, troubleshooting
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/14
toc-enable: false
---

If you receive this error:

```text
IMPORTANT!

This product is inactive and/or no longer for sale. 
This product has been disabled for one or more of the following reasons: 

Limited quantities 
Limited offer period 
Terms of service violation
```

This error comes from ClickBank. Please check that the Product in your ClickBank account is still active. The Product ID you should check is the one that matches the value of the `cbp=“"` attribute in your button shortcode. If your s2Member ClickBank button shortcode has `cbp=“2"`, then you should check Product ID# 2 in your ClickBank account.