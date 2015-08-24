---
title: Can the EOT Time be added to the Pro Login Widget?
categories: questions
tags: eot-time, s2eot, pro-login-widget, login-widgets, login-registration
author: renzms
github-issue: https://github.com/websharks/s2member-kb/issues/253
toc-enable: off
---
Yes, the Pro Login Widget supports arbitrary **XHTML/PHP** and even shortcodes inside the "Additional XHTML/PHP Code?" field, so the EOT (End-of-Term) Date/Time information can be added to the Pro Login Widget by inserting the `[s2Eot /]` shortcode (see [\[s2Eot /\] Shortcode Documentaion](http://s2member.com/kb-article/s2eot-shortcode-documentation/)) into the "Additional XHTML/PHP Code?" field of the widget.

![Pro Login Widget](https://cloud.githubusercontent.com/assets/53005/9455502/dd98876e-4a99-11e5-8b63-4b796ccec706.png)

Since the "Additional XHTML/PHP Code?" field of the widget also supports PHP, you could even use the [PHP-equivalent of the s2Eot shortcode](http://s2member.com/kb-article/s2eot-shortcode-documentation/#toc-e00e3e46) to achieve even finer control over how the information is displayed.

## Further Reading
- [\[s2Eot /\] Shortcode Documentation](http://s2member.com/kb-article/s2eot-shortcode-documentation/)
- [When is an EOT Time set for each user?](http://s2member.com/kb-article/when-is-an-eot-time-set-for-each-user/)
