---
title: Understanding Specific Post/Page Access Restrictions
categories: tutorials
tags: restriction-options
author: renzms
github-issue: https://github.com/websharks/s2member-kb/issues/301
---

**Specific Post/Page Access Restrictions** and **Membership Level Access Restrictions**. These are two different ways to Restrict content using the s2Member software. They are often confused with each other and sometimes misused. In this article I will clarify the differences between the two and explain how to apply each type of Restriction effectively.

## Specific Post/Page Access

**Dashboard → s2Member → Restriction Options → Specific Post/Page Access**

Here you can restrict specific Post/Page IDs. They will be off-limits to the public. Access only becomes available when one of them is purchased via Specific Post/Page Access. This type of Restriction is not connected to any sort of Membership Level or Custom Capability. It absolutely requires that a specific Post (or Page) be purchased by a Customer.

![Diagram](https://cloud.githubusercontent.com/assets/13220018/17164049/1d6e66a8-53f7-11e6-8f21-f8732b3c23c3.png)

## Membership Level Access

Represented by everything else in: **Dashboard → s2Member → Restriction Options**

This is the primary objective for most sites running s2Member. Membership Level Access is what the term indicates. You restrict areas of the site that require Membership so they are off-limits to the public. Others can only access those areas of the site if they have a special WordPress Role; e.g., s2Member Level 1, s2Member Level 2, 3, 4, etc; or a Custom Capability that you configure which grants them access.

Generally speaking, when you become a 'Member', you gain access to more than just a single Post or Page. You gain access to everything that comes with Membership, at the Membership Level you pay for. Of course, Membership Level Access requires that a Member be logged-in too—making this type of Restriction much, much different from 'Specific Post/Page Access'.

![Diagram](https://cloud.githubusercontent.com/assets/13220018/17164053/2071997e-53f7-11e6-8a7f-88c6a7c989d8.png)

## Potential for a Conflict Between Restriction Types

We've established there are two different Restriction Types in s2Member.

If you protect a Post (or Page) using 'Specific Post/Page Access Restrictions', then it absolutely requires that a Customer pay for access to that specific Post or Page—whether they are a 'Member' or not. In short, this is completely independent from Membership.

Conversely, if you protect a Post, Page, Category, Tag, or something else; using Membership Level Restrictions, then it requires that a user be logged-in and have a Membership Role (or Capability) that grants them permission to access that content; i.e., they must be a 'Member'.

So this creates the potential for a conflict between the two. **If you accidentally apply both Restriction types to any area of the site, you will have a problem**. Imagine being a customer who pays for access to a 'Specific Post/Page', but after checkout you are redirected away from what you just paid for. Instead of being granted access, the site says that you _also_ need to be a Member. Not good!

## How To Avoid Restriction Type Conflicts

To avoid Restriction type conflicts, just make sure any Post (or Page) that is going to be sold via s2Member's 'Specific Post/Page Access' functionality, it is not _also_ protected by a Membership Level Access Restriction too—either directly or indirectly.

For instance, if you protect an entire Category or an entire Tag using Membership Level Access Restrictions in s2Member, and then you try to sell 'Specific Post/Page Access' to a Post that has a protected Tag, it's not going to work out the way you want it to. Having a protected Tag means the Post requires Membership Level Access. You can't sell it with 'Specific Post/Page Access'.

Instead, create stand-alone Posts (or Pages) that don't have a Category or Tag that is protected. Also, make sure they don't match a URI that is protected, and make sure they don't require any Custom Capability. Now, you have a Post (or Page) that you can protect and sell with 'Specific Post/Page Access' functionality. You won't run into any conflicts if you do it this way.

You can sell Specific Post/Page Access to anyone. Existing Customers who are already Members can buy and gain access. And, anyone in the public who is not a Member of the site can buy and gain access also. No account required. No login required. If you are a Member, that's fine. If not, that's fine too. Easy, simple. Specific Post/Page Access can be a very effective way to drive sales.