---
title: Why are SSL and non-SSL pages logging-out my members?
categories: questions
tags: login-registration,troubleshooting
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/12
---

> When a logged-in member visits a page on the site that is SSL-secured and then visits a non-SSL page, they are asked to login again. Why is this happening?

This issue is actually not unique to s2Member--it's actually a WordPress issue. The problem here is that WordPress sees a session authenticated via SSL and a session authenticated without SSL as two separate sessions. If you login with SSL enabled (i.e., the login URL includes `https://`), and then try to access a protected page using a non-SSL URL (i.e., `http://`), WordPress will consider that new request as coming from someone who _has not yet authenticated_. 

This is just a reality with how SSL works (it's a security feature built into the protocol, into the web servers, and into all web browsers).

There is a related KB article that talks about issues with mixing `www.yourdomain.com` with `yourdomain.com` (no-www). See: [Avoiding Login Issues](http://s2member.com/kb-article/how-to-avoid-login-issues/). The problem described in that article is essentially the same as using URLs with and without SSL: the web browser and the web server see the two variations of the URL as _separate sessions_, and therefore unless you're authenticated with both versions, you'll end up being logged in on some pages and not logged in on others.

The solution is to stick with one and avoid mixing the two wherever possible. You probably want to stick with SSL once someone has logged in--i.e., all your protected pages should require SSL. On the s2Member side of things, you can ensure that every single protected page is served via SSL by adding a Custom Field to the post/page with the name `s2member_force_ssl` and a value of `yes` (see attached screenshots).

---

![](https://cloud.githubusercontent.com/assets/53005/5545251/b935624e-8aea-11e4-9903-c8eb045f2c3d.png)

---

![](https://cloud.githubusercontent.com/assets/53005/5545250/b9338e6a-8aea-11e4-8759-37a048928d5f.png)

---

For the rest of your WordPress installation, the WordPress Codex has an article on configuring [Administration over SSL](http://codex.wordpress.org/Administration_Over_SSL) for WordPress. This includes enforcing logins over SSL.

You may also want to check your WordPress configuration (see: **Dashboard → Settings → General**) and make sure that the WordPress URL is using the correct `https://` URL.

Finally, if you're still having trouble, there are WordPress plugins out there that help you force SSL site-wide: https://wordpress.org/plugins/search.php?q=force+ssl

If you need more help getting your WordPress installation working site-wide with SSL, the [WordPress Support Forum](http://wordpress.org/support/) is a great place to find help with that.