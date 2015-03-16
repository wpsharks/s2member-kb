---
title: Can I customize the IP Restrictions template?
categories: questions
tags: restriction-options, mu-plugins-hacks
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/66
---

> Can I customize the IP Restrictions template file?
> I am playing with the IP address restrictions system,which seems to work well.
Is there any way for me to customize the template? Can I redirect to a WP page so that the customer will see something pretty?

Yes. Please make a copy of this file: `/s2member/includes/templates/errors/ip-restrictions.php` and place it into a new file: `/wp-content/ip-restrictions.php`. There you can customize it further on your own, and without impacting the core files that come with the s2Member application.

You will have full access to all PHP/WordPress/s2Member functionality in this template file.

See also: [Hacking s2Member® Plugin w/ Hooks/Filters for WordPress](https://github.com/websharks/s2member-kb/issues/150)
