---
title: Can I use Custom Capabilities to determine the subscribers' MailChimp List?
categories: questions
tags: api-list-servers
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/204
toc-enable: off
---

**Question:** Is it possible to specify the MailChimp List ID based on the Custom Capability being purchased by a new member?

**Answer:** No, this is not possible at the moment. We also don't recommend trying to do it that way, because that creates a nightmare when you think about trying to have a MailChimp List for every Custom Capability (or Custom Capability combination). 

Instead, we recommend that you setup Merge Fields (see: [Can I add custom mail merge fields?](http://s2member.com/kb-article/can-i-add-custom-mail-merge-fields/)) to send the Custom Capability information to MailChimp so that they're stored on the subscribers profile over there. That way you can then filter groups of subscribers on MailChimp based on the Custom Capabilities that certain users purchased.

By setting up Merge Fields, your subscribers on the MailChimp side will include the Custom Capabilities the user signed up with (in a Merge Field that you create on MailChimp), so that you can then build MailChimp Groups that are filtered by that specific Merge Field (the one that contains the Custom Capabilities) and then send campaigns to that segment if your subscribers. 

See also: [MailChimp KB: About Segments and Groups](http://kb.mailchimp.com/lists/groups-and-segments/about-segments-and-groups).
