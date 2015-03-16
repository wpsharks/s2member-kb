---
title: Mod Security (Odd 403, 503, 500 Errors)
categories: tutorials
tags: troubleshooting
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/153
---

## Mysterious 503/403 (Access Denied) Errors?

#### Mod Security for Apache is the Likely Cause

We've just taken a closer look at some of the most popular configurations for [ModSecurity, an Open Source Web Application Firewall](https://www.modsecurity.org/). For instance, we looked at the default ruleset that many hosts use from [this source](https://www.owasp.org/index.php/Category:OWASP_ModSecurity_Core_Rule_Set_Project). Unfortunately, there are _many_ Mod Security rules that can produce false positive results, and we've also found that each host runs with a little bit different combination of rules, based on what they consider to be most important to their clients; and perhaps tailored to the most common software applications they host for their clients.

In short, there's really no way for s2Member to work around everything Mod Security looks at from one host to another. If you're running Mod Security and you plan to continue to run it, you may need your hosting company or system administrator to tweak things for the applications that you run; e.g., by removing paranoid rules from your Mod Security configuration.

In the [Core Rule Set Project](https://www.owasp.org/index.php/Category:OWASP_ModSecurity_Core_Rule_Set_Project) we found several rules that would negatively impact even a default WordPress installation—even counting points against cookies set by the core WordPress framework. Anyway, you get the picture, paranoid!

## Known Problematic Areas In s2Member

- URL: `http://example.com/?s2member_register=[encrypted data string appears here]`
- URL: `http://example.com/?s2member_sp_access=[encrypted data string appears here]`
- URL: `http://example.com/?s2member_paypal_notify=[followed by GET/POST data from PayPal]`
- URL: `http://example.com/?s2member_paypal_return=[followed by GET/POST data from PayPal]`
- For that matter, any URL that contains: `?s2member_` and/or `?s2member_pro_` could be considered suspect under a paranoid Mod Security configuration.
- Also, some data stored in cookie names starting with: `s2member_` and/or `wordpress_`.

I don't personally care for Mod Security _(I think it produces too many [false positives](http://www.modsecurity.org/blog/archives/2007/02/handling_false.html) and too many headaches)_. If configured properly it _can_ be useful. The problem? It seldom is. That being said, I do understand that many hosts use this as a way to further protect the integrity of their servers. Given the degree of complexity associated with heuristic rule sets for Mod Security, all we can do with s2Member is follow [best practices](http://stackoverflow.com/questions/3024123/how-to-write-mod-security-friendly-php-code) when it comes to what data we include in GET/POST/COOKIE/HEADER data (e.g., no HTML in query strings, no function/parameter names, no SQL keywords, etc).

Beyond that, if you are still experiencing what are seemingly random 403 errors (possibly associated with cookies, headers, query string variables, etc), please follow the instructions below.

## Disabling Mod Security

Try adding `SecFilterEngine Off` and `SecFilterScanPOST Off` to an `.htaccess` file in the web root. Many hosts allow this to be disabled on a per-user basis. Some users are allowed to do this by default on WHM/cPanel-based servers.

If you run your own dedicated server and you want to save yourself headaches associated with Mod Security, you can disable it inside your `httpd.conf` file with something like this:

```apache
# Mod Security v1.x.
# May work in .htaccess too, on some hosts.
<IfModule mod_security.c>
	SecFilterEngine Off
	SecFilterScanPOST Off
</IfModule>
```

```apache
# Mod Security v2.x.
# Will NOT work in .htaccess, use httpd.conf.
<IfModule mod_security2.c>
	SecRuleEngine Off
</IfModule>
```

_**Warning:** This solution is a tradeoff; i.e., security vs. usability. Please use this solution at your own risk. See also: [this discussion thread](http://wordpress.org/support/topic/disable-mod-security)._

## Disabling Specific Mod Security Rules

If you run your own dedicated server and you want to keep Mod Security, but remove certain rules that are getting in your way (e.g., rules causing a problem for s2Member and/or other applications you run), check your Apache `error.log` file for Mod Security errors. Look for the rule ID associated with each of them. Then remove rule IDs that are causing problems, using your `httpd.conf` file.

```apache
# Mod Security v2.x only.
# Will NOT work in .htaccess, use httpd.conf.
<IfModule mod_security2.c>
	SecRuleRemoveById 960024 981173 981212 960032 960034
</IfModule>
```

_**Warning:** This solution is a tradeoff; i.e., security vs. usability. Please use this solution at your own risk. See also: [this discussion thread](http://wordpress.org/support/topic/disable-mod-security)._

## Shared Hosting Suggestions for Mod Security

<div class="li-margins"></div>

- If you're on shared/managed hosting, ask your hosting company to disable Mod Security. Or, ask them to whitelist the s2Member application by disabling Mod Security for URLs that contain `?s2member_` in their query string, or are otherwise associated with your WordPress installation.
- As yet another alternative, ask them to whitelist specific URLs that are causing problems for you. Hosts that run Mod Security are familiar with these requests, because Mod Security _is_ so very picky. All you need to do is provide your host with the full URL that is failing (including any query string variables that appear after the `?` mark in the URL) and/or point them to this article.
- Or, ask your host to back down on the paranoia a bit overall with respect to Mod Security and/or the [PHP Suhosin](http://www.hardened-php.net/) extension, which is yet another paranoid module (under certain configurations).

If you continue to have trouble, consider using a host that does _not_ use Mod Security, or one that has a good flexible configuration; one which does not inhibit the functionality of trusted PHP applications and plugins for WordPress. Some hosts that just recently started using Mod Security, or have recently upgraded to Mod Security v2.x may still need time to work the kinks out of their default configuration. Try to be patient with your hosting company, but don't hang around forever waiting for a miracle either. We recommend [MediaTemple® (gs)](http://www.s2member.com/r/mediatemple/) as a highly flexible solution in this regard.

## Other Related Articles (Suggested Reading)

- [How To Fix WordPress and Mod Security 2](http://www.binarymoon.co.uk/2011/05/wordpress-mod-security-2/)
- [How can I disable mod_security in .htaccess file?](http://stackoverflow.com/questions/12928360/how-can-i-disable-mod-security-in-htaccess-file)
- [Avoiding Mod Security False Positives with White-listing](http://resources.infosecinstitute.com/avoiding-mod-security-false-positives-white-listing/)
- [How To Set Up mod_security with Apache on Debian/Ubuntu](https://www.digitalocean.com/community/tutorials/how-to-set-up-mod_security-with-apache-on-debian-ubuntu)
- [Are these mod_security rules safe to disable?](https://www.digitalocean.com/community/questions/are-these-mod_security-rules-safe-to-disable)