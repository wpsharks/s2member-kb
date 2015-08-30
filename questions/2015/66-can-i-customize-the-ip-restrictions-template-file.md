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

Yes. Please make a copy of this file:

```text
/s2member/includes/templates/errors/ip-restrictions.php
```

_See also: [source code on GitHub](https://github.com/websharks/s2member/blob/000000-dev/s2member/includes/templates/errors/ip-restrictions.php)_

and place it into a new file of your own here:

```text
/wp-content/ip-restrictions.php
```

How you can customize `/wp-content/ip-restrictions.php` in whatever way you like.

You can use PHP, WordPress, and s2Member functionality in this template file; i.e., `<?php ?>` tags can be used in this template if you need them.

See also: [Hacking s2Member® Plugin w/ Hooks/Filters for WordPress](https://github.com/websharks/s2member-kb/issues/150)
