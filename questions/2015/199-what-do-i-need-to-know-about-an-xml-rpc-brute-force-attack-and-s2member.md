---
title: What do I need to know about an XML-RPC brute-force attack and s2Member?
categories: questions
tags: restriction-options, security
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/199
---

**Question:** Our s2Member Pro websites have been experiencing a recent brute-force flood attack against the `xmlrpc.php` file of the site. I was wondering what, if anything, you recommend we do to limit the effects of this attack on s2Member.

**Answer:** Many web hosting companies recommend adding the following snippet of code to your sites' `.htaccess` file, to temporarily deny access to the `xmlrpc.php` file:

```text
<Files "xmlrpc.php"> 
Order allow,deny 
Deny from all 
</Files>
```

The XML-RPC (`xmlrpc.php`) is a feature of WordPress itself and is not specific to, or even part of, the s2Member plugin. A brute-force attack against `xmlrpc.php` is a very common type of attack for WordPress sites. We've seen that using an `.htaccess` rule to deny access to that file is the best way to temporarily block an attack, however we recommend you contact your web hosting company for specific advice.

As far as s2Member itself: There's nothing specifically related to the XML-RPC attack that you need to do on the s2Member side of things. However, you may want to review these sections of the plugin to ensure that you have appropriate options chosen (the defaults should work fine, but you might want to tweak them):

- **s2Member → Restriction Options → Unique IP Access Restrictions**
- **s2Member → Restriction Options → Bruce Force IP/Login Restrictions**