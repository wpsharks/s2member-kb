---
title: What information does s2Member Pro report to WebSharks?
categories: questions
tags: security
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/239
---

s2Member Pro collects and reports basic environment information to WebSharks (our parent company) to help plan for and improve future versions of s2Member Pro. All of the information collected by WebSharks is stored anonymously with no identifying information. This is not unlike WordPress itself, which reports a lot of information to WordPress about your site. However, s2Member Pro does this on a much smaller scale and, unlike WordPress, does not collect any identifying information that would link that data back to your site.

---

## s2Member Pro collects and reports to WebSharks:

- MD5 Hash of the server IP address (e.g., `2909a2c64757ce93daa60e3cfc653ef1`; note: we do not store any IP addresses; all reported data is stored anonymously; we use this hash to filter out duplicate reports from the same server)
- Server OS (e.g., `Linux`)
- PHP Version (e.g., `5.4`)
- MySQL Version (e.g., `5.5`)
- WordPress Version (e.g., `4.2.2`)
- Product Version (e.g., `150709`)
- Product Name (e.g., `s2member-pro`)

## Why is WebSharks collecting this information?

We use this information to help us make decisions about what versions of PHP, MySQL, WordPress, etc; that we should put our focus on. Ideally, we would always build our software products in a way that optimizes them for the latest versions of PHP/MySQL. However, unless and until we can be relatively certain that our customers are running on servers that are up-to-date, we hold off on doing so. Thus, gathering these statistics helps us make decisions about what/when/how we write code.

## How can I opt-out?

To disable the anonymous stats collection, create an [MU-Plugin](http://codex.wordpress.org/Must_Use_Plugins) with the following filter:

```php
<?php
add_filter('c_ws_plugin__s2member_pro_stats_pinger_enable', '__return_false');
```

## Can I inspect the code used to collect and report this information?

Yes, absolutely. All of the s2Member Pro code is open-source and available for inspection. You'll find the relevant code in `s2member-pro/includes/classes/stats-pinger.inc.php`.

## Where are you storing this information?

The anonymous information is stored securely on a WebSharks server, secured using modern security features. Here's the schema for the database table we use to store the reported information:

```sql
CREATE TABLE IF NOT EXISTS `wp_product_stats` (
  `ID` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  `time` int(10) unsigned NOT NULL,
  `week_time` int(10) unsigned NOT NULL,
  `ip_md5` varchar(32) COLLATE utf8_unicode_ci NOT NULL,
  `os` varchar(45) COLLATE utf8_unicode_ci NOT NULL,
  `php_version` varchar(20) COLLATE utf8_unicode_ci NOT NULL,
  `mysql_version` varchar(20) COLLATE utf8_unicode_ci NOT NULL,
  `wp_version` varchar(20) COLLATE utf8_unicode_ci NOT NULL,
  `product_version` varchar(20) COLLATE utf8_unicode_ci NOT NULL,
  `product` varchar(45) COLLATE utf8_unicode_ci NOT NULL,
  PRIMARY KEY (`ID`),
  UNIQUE KEY `unique_entry` (`week_time`,`ip_md5`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_unicode_ci AUTO_INCREMENT=1 ;
```

## Does the free version of s2Member collect stats?

No. The s2Member Framework (i.e., the free version of s2Member available at WordPress.org) does not collect statistics like this. Stats are collected when using s2Member Pro only.