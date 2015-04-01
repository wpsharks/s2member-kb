---
title: How do I set the [s2Member-List /] field labels?
categories: questions
tags: s2member-list, shortcodes
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/181
toc-enable: off
---

The `[s2Member-List /]` shortcode (see [s2Member-List Shortcode Documentation](http://s2member.com/kb-article/s2member-list-shortcode-documentation/)), allows you to include any number of additional fields in the output using the `show_fields=""` shortcode attribute. If you don't give these fields a specific label, they will just output a default value:

```text
[s2Member-List show_fields="s2member_access_label" /]
```

![2015-04-01_17-39-38](https://cloud.githubusercontent.com/assets/53005/6953412/2f9cb1e0-d897-11e4-9490-f874b35a713a.png){.fancy-image}

To customize the labels, simply prepend the label name to the field name and separate the label from the field name with a semicolon (`:`):

```text
[s2Member-List show_fields="Membership Level:s2member_access_label" /]
```

![2015-04-01_17-39-07](https://cloud.githubusercontent.com/assets/53005/6953416/37693736-d897-11e4-99e0-1d03458dff3a.png){.fancy-image}

Note that this works when including multiple fields as well; simply separate each `label:field` pair with a comma, e.g., `Membership Level:s2member_access_label,Expiration Date:s2member_auto_eot_time`.

### Can I customize the `[s2Member-List /]` output even more?

Yes. See [Custom Template for `[s2Member-List /]`](http://s2member.com/kb-article/using-a-custom-template-for-s2member-list/).
