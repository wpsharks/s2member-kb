---
title: Integrating MailChimp
categories: tutorials
tags: api-list-servers
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/208
---

s2Member can be integrated with MailChimp. MailChimp is an email marketing service. MailChimp makes it easy to send email newsletters to your Customers, manage your MailChimp subscriber lists, and track campaign performance.

Although s2Member can be integrated with almost _any_ list server, we highly recommend MailChimp, because of their powerful API. In future versions of s2Member, we plan to build additional features into s2Member that work with, and extend MailChimp services.

For now, we've covered the basics. You can have your Members automatically subscribed to your MailChimp marketing lists (i.e., newsletters / autoresponders). You'll need a [MailChimp account](http://www.s2member.com/mailchimp), a [MailChimp API Key](http://www.s2member.com/mailchimp-api-key), and your MailChimp List IDs (described below).

---

## Step 1: Creating An API Key

You can add an API Key to your MailChimp account here: <https://us1.admin.mailchimp.com/account/api/>

See also: [About MailChimp API Keys](http://kb.mailchimp.com/accounts/management/about-api-keys)

### Giving Your API Key to s2Member

See: **Dashboard → s2Member → API / List Servers → MailChimp Integration**

![2015-05-14_09-28-53](https://cloud.githubusercontent.com/assets/1563559/7637608/b21cf706-fa1b-11e4-92f1-8317dd9c7b46.png)

---

## Step 2: Adding Your List IDs

You will find a list of all of your MailChimp List IDs, at MailChimp.com
<https://us1.admin.mailchimp.com/lists/>

You need to locate the List ID(s) you intend to integrate with s2Member. Here is a screenshot that shows where to find your MailChimp List ID for each of the lists that you want to integrate with s2Member.

![2015-05-14_09-25-12](https://cloud.githubusercontent.com/assets/1563559/7637697/4d622d9e-fa1c-11e4-8081-dd1152577a21.png)

### Giving Your List ID(s) To s2Member

See: **Dashboard → s2Member → API / List Servers → MailChimp Integration**

![2015-05-14_09-36-32](https://cloud.githubusercontent.com/assets/1563559/7637775/c0db3fae-fa1c-11e4-8d9d-824672228501.png)

---

## Step 3: Double Opt-in Checkbox Options

See: [Double Opt-In Checkbox Config.](http://s2member.com/kb-article/double-opt-in-checkbox-config/)

---

## Step 4: Configuring MERGE Fields (Optional)

See: [Can I add custom mail merge fields?](http://s2member.com/kb-article/can-i-add-custom-mail-merge-fields/)

---

## Step 5: Enable Automatic List Transitioning (Optional)

When a member is promoted (or demoted), s2Member is capable of automatically moving a Member from a MailChimp List that applies to Membership Level 1 (for example), placing them on the List ID for Membership Level 0 instead. To learn more about this, please see:

**Dashboard → s2Member → API / List Servers → Automate Un-Subscribe/Opt-Outs?**