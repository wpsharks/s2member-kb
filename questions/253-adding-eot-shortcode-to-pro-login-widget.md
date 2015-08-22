---
title: Can I add the New EOT Shortcode to the PRO Login Widget?
categories: questions
tags: eot-time
author: renzms
github-issue: https://github.com/websharks/s2member-kb/issues/253
---

Yes, you can add it using PHP code or the `[s2Eot /]` shortcode itself, please use the equivalent PHP code found on: [PHP Equivalent for Developers](http://s2member.com/kb-article/s2eot-shortcode-documentation/#toc-e00e3e46). 

The Pro Login Widget supports arbitrary **XHTML/PHP** and even shortcodes. You can insert the PHP or even the `[s2Eot /]` shortcode right into these fields.

![image](https://cloud.githubusercontent.com/assets/13220018/9360398/91cdb25c-46c8-11e5-8d68-24129ec11e00.png)


This box is a sample of the string, and you would need to enclose it like so :

```
<?php
print_r($eot = s2member_eot());
?>
```

<hr>

For further reading in regards to EOT and when its set for each user, please see : [When is an EOT Time set for each user](http://s2member.com/kb-article/when-is-an-eot-time-set-for-each-user/)

*Tip*: If you plan to use **PHP inside a WordPress Post/Page**, you will first need to install a plugin that allows you to run PHP code inside your WordPress Pages. We recommend [ezPHP](https://wordpress.org/plugins/ezphp/)

