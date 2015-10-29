---
title: Integrating AWeber
categories: tutorials
tags: api-list-servers
author: kristineds
github-issue: https://github.com/websharks/s2member-kb/issues/271
---

AWeber is an email marketing service that can be integrated with s2Member. Although s2Member can be integrated with almost _any_ list server, we recommend using AWeber, MailChimp, or GetResponse.

In this article we're going to explain how to integrate AWeber with s2Member using the API method so that new members are automatically added to your AWeber list(s) and removed or transitioned to another list when they are upgraded, downgraded, or deleted. 

To get started, you will need your [AWeber account](http://s2member.com/AWeber), [AWeber List IDs](https://AWeber.com/users/settings/), and  [AWeber API Authorization code](http://s2member.com/r/AWeber-api-key) for the s2Member application.

---

## Step 1: Creating An API Key

You can add an API Key to your AWeber account here: <http://s2member.com/r/AWeber-api-key>

See also: [About AWeber API Keys](https://help.AWeber.com/hc/en-us/articles/204031016-Does-AWeber-Have-An-API-)

### Giving Your API Key to s2Member

See: **Dashboard → s2Member → API / List Servers → AWeber Integration**

![s2Member AWeber API Key](https://cloud.githubusercontent.com/assets/7514953/10616140/2d9ebb60-7796-11e5-9487-0f8c67c2e49e.png)

---

## Step 2: Adding Your List IDs

You will find a list of all of your AWeber Lists at AWeber.com <https://AWeber.com/users/settings/>

You need to locate the List ID(s) you intend to integrate with s2Member. Click on the _Lists tab_. On that page you'll find a Unique List ID associated with each of your lists. AWeber sometimes refers to this as a _List Name_ instead of a _List ID_. Here is a screenshot that shows where to find your AWeber List ID for each of the lists that you want to integrate with s2Member.

![s2Member AWeber Add List IDs](https://cloud.githubusercontent.com/assets/7514953/10737678/87cf59a2-7c4e-11e5-92ed-885ad2f2f8b4.png)

### Giving Your List ID(s) To s2Member

See: **Dashboard → s2Member → API / List Servers → AWeber Integration**

![s2Member AWeber List IDs](https://cloud.githubusercontent.com/assets/7514953/10616197/88c5623c-7796-11e5-8136-f625f490a52f.png)

---

## Step 3: Double Opt-in Checkbox Options

See: [Double Opt-In Checkbox Config.](http://s2member.com/kb-article/double-opt-in-checkbox-config/)

---

## Step 4: Configuring MERGE Fields (Optional)

See: [Can I add custom mail merge fields?](http://s2member.com/kb-article/can-i-add-custom-mail-merge-fields/)

---

## Step 5: Enable Automatic List Transitioning (Optional)

When a member is promoted (or demoted), s2Member is capable of automatically moving a Member from an AWeber List that applies to Membership Level 1 (for example), placing them on the List ID for Membership Level 0 instead. To learn more about this, please see:

**Dashboard → s2Member → API / List Servers → Automate Un-Subscribe/Opt-Outs?**