---
title: How do I reset IP Restrictions for a single user?
categories: questions
tags: ip-access-restrictions, login-registration
author: raamdev
github-issue:
github-issue: https://github.com/websharks/s2member-kb/issues/243
---

A single Username is only valid for a certain number of unique IP addresses (as configured in your **Dashboard → s2Member → Restriction Options → Unique IP Access Restrictions**). Once that limit is reached, s2Member assumes there has been a security breach. At that time, s2Member will place a temporary ban (preventing access).

If you have spoken to a legitimate Customer that is receiving an error upon logging in (ex: 503 / too many IP addresses), you can remove this temporary ban by editing the users account and checking the box that says, _Yes, delete/reset IP Restrictions associated with this Username_ and then clicking the **Update User** button at the bottom.
 
![Reset IP Access Restrictions for a User](https://cloud.githubusercontent.com/assets/53005/8890474/2cf256dc-32d0-11e5-83e5-5b25ad2bc3c3.png)


If the abusive behavior continues, s2Member will automatically re-instate IP Restrictions in the future. If you would like to gain further control over IP Restrictions, please check your Restriction Options panel for s2Member.
