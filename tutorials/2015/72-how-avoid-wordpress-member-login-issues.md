---
title: How to Avoid Login Issues
categories: tutorials
tags: pro-login-widget, wp-login
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/72
---

### Understanding Member Login Differences

Some site owners don't realize that all browsers consider variations in your domain as different. That is, every browser sees each of these four URLs (below) as slightly different destinations. Therefore, logging into your account on one of these, and then being redirected to a slightly different variation, may result in the user **not being logged-in** as you might expect.

```
1. http://example.com/			:: http scheme, no sub-domain.
2. https://example.com			:: https scheme, different protocol.
3. http://www.example.com/		:: different sub-domain; i.e. www
4. https://www.example.com/		:: different sub-domain and protocol.
```

If I visit `http://example.com/` and I enter my username/password, I am logged-in at `example.com` (no `www`); and over the `http://` protocol. However, if you post links on your site that point to `https://example.com/` or `www.example.com` (with the `www`), the user **may not be logged-in there**.

#### Sub-Domains: `www` vs. without `www`

Your domain name has a root. It's the domain without anything in front of it; e.g. `example.com`. While most people tend to think of `example.com` and `www.example.com` as the same, they are in fact not the same. The `www.` prefix is not a magic mirror, it's just another sub-domain.

So a `www.` prefix indicates a sub-domain like any other; e.g. `a.example.com`, `b.example.com`, `c.example`, `www.example.com`. All of these are sub-domains; i.e. not quite the same as your root, which is: `example.com`. When it comes to WordPress and the way WordPress sets login cookies, these are all _completely_ different, because WordPress sets a logged-in cookie for the current domain. If the current domain (in the address bar of your browser) is a sub-domain, your logged-in cookie is valid for the sub-domain only; i.e. **not functional at `example.com`**.

Therefore, if a user logs into your site at `www.example.com`, but you allow your site to be accessed with or without the `www.` prefix, this can lead to many issues. Most site owners that understand this will work to adjust their server configuration so it forces one variation to be used across the entire site. See: http://davidwalsh.name/no-www for some quick examples of this.

#### HTTPS vs. HTTP (Subtle Differences)

In browsers like Google Chrome, Safari, Firefox, Opera, and _another I dare not mention_; it is possible for WordPress to set a cookie that is only available over the `https://` protocol (i.e. a secure "https only" cookie). See: http://en.wikipedia.org/wiki/HTTP_cookie#Secure_cookie

In WordPress, if a user logs into the site over `https://`, WordPress will generally set the cookie as "https only". This is done as an added layer of security. WordPress assumes this is what you'd want whenever you ask users to log into the site over `https://`.

##### What impact does this have on my site?

1. It means that a user logging into the site over `http://`, _will_ be able to access the site over `https://` also. There's no issue with this, because WordPress only makes the cookie "https only" if the login occurred over `https://` to begin with. A cookie that is not "https only" can be read from either protocol without issue.

2. **Important:** ... if a user logs into the site over `https://`, where the form action is something like `https://example.com/wp-login.php`, there is a good chance they will **not** be thought of as logged-in on the `http://` protocol.  Their logged-in cookie is only good over SSL in this case.

  Therefore, visiting `http://example.com/` after logging in from `https://example.com/` will lead to confusion. This is because WordPress sets the cookie in such a way that it is only accessible over SSL; i.e. on the original protocol they logged into the site with: `https://`.

---

### How to Avoid WordPress Member Login Issues

#### Decide on a Domain Variation for WordPress

Decide early-on which domain variation you're going to use, and make sure that your installation of WordPress® is configured to match what you intend to use. Check your Dashboard under: `Settings -> General`. All of the URLs configured in that panel need to match what you intend to use.

#### Remain Consistent when Building WordPress Links

Be consistent in the way you link to pages on your site. Please do not create links on your site that use different variations of your domain. That could result in a visitor logging in on one variation, but clicking links on your site that land them on another variation (where they may not be recognized as a logged-in member). If you've already done some of this in error, you can mass update Posts/Pages using a tool like [Search Regex for WordPress](https://wordpress.org/plugins/search-regex/).

### Avoiding Sub-Domain Cookie Conflicts

By default, WordPress will set all cookies for the current domain. If the current domain is `www.example.com`, the cookie will not work on `example.com` or at `sub.example.com`. However, you can tell WordPress to use a specific root domain instead, so that when WordPress sets a cookie, it will be valid for the current domain, and also for any/all sub-domains that you might be using.

In your `/wp-config.php` file, you can add:

```php
define('COOKIE_DOMAIN', '.example.com');
```

If you have WordPress installed in a sub-directory, you might also want to consider changing the `COOKIEPATH` to the root of your site. By default, WordPress will set cookies where they are only valid under the current WordPress installation path. So for instance, if you have WordPress installed at: `example.com/wordpress/`, a user visiting `example.com/page/` will not be logged into the site, because the cookie is not valid under this path.

To change the default WP behavior, so that a cookie is valid across all paths in the domain, you can add the following line to your `/wp-config.php` file.

```php
define('COOKIEPATH', '/');
```