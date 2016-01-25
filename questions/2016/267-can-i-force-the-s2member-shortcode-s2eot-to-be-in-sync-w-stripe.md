---
title: 'Can I force the s2Member shortcode [s2EOT /] to be in sync w/ Stripe?'
categories: questions
tags: stripe, s2eot
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/267
---

This occurs already. There is a bit of a delay at times though. s2Member caches the details that it retrieves from Stripe in order to the determine the NPT (Next Payment Time).

The data that s2Member retrieves from Stripe is cached for 12 hours by default. This prevents a situation where your site is making repeated connections to Stripe for information that is not likely to change very often. If you'd like to reduce the cache time, you can change `DAY_IN_SECONDS / 2` [here](https://github.com/websharks/s2member/blob/150925/s2member/includes/classes/sc-eots-in.inc.php#L93), to something that works better for you.

---

Another way to refresh the cache is to delete all WordPress transients that contain `s2m_eot`.

```sql
DELETE FROM `wp_options` WHERE `option_name` LIKE '%s2m\_eot%'
```

See also: [How can I remove Transients in the WP options table?](http://stackoverflow.com/questions/10422574/can-i-remove-transients-in-the-wp-options-table-of-my-wordpress-install)