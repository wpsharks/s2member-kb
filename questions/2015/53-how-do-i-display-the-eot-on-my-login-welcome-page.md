---
title: How do I display the EOT Date/Time?
categories: questions
tags: login-welcome-page, mu-plugins-hacks, s2eot, eot-time
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/53
toc-enable: off
---
To display the EOT date/time, we recommend using the `[s2Eot /]` shortcode (see [\[s2Eot /\] Shortcode Documentation](http://s2member.com/kb-article/s2eot-shortcode-documentation/)). The `[s2Eot /]` shortcode is the easiest way to display the EOT Date/Time and has many options that will allow you to handle various scenarios (Fixed-Term Subscriptions, Recurring Subscriptions, and scenarios where there is no EOT time at all).

The easiest way to use the `[s2Eot /]` shortcode is to place the shortcode on a single line by itself with no options.

```wpsc
[s2Eot /]
```

If an EOT can be determined (common with Fixed-Term Subscriptions), this will output something like `Access Expires: Jul 16th, 2025, 12:00 am UTC`. If an NPT (next payment time) can be determined (common with Recurring Subscriptions), you'll see something like `Next Payment: Mar 5th, 2022, 12:00 am UTC`. Otherwise, if an EOT cannot be determined at all, the shortcode will display nothing.

**Note**: There are _many_ other options for the `[s2Eot /]` shortcode, including ways to customize the message that is shown. Please review the [\[s2Eot /\] Shortcode Documentation](http://s2member.com/kb-article/s2eot-shortcode-documentation/) for futher details.

## Displaying the EOT Date/Time with PHP 

While the `[s2Eot /]` shortcode will be sufficient for most site owners, developers may want even finer control. Please see the [\[s2Eot /\] PHP Equivalent for Developers](http://s2member.com/kb-article/s2eot-shortcode-documentation/#toc-e00e3e46).

**Tip**: If you plan to use PHP inside a WordPress Post/Page, you will first need to install a plugin that allows you to run PHP code inside your WordPress Pages. We recommend [ezPHP](http://wordpress.org/plugins/ezphp/).
