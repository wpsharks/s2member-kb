---
title: Double Opt-In Checkbox Config.
categories: tutorials
tags: api-list-servers
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/179
---

## MailChimp, AWeber, and GetResponse

See: **Dashboard → s2Member → API / List Servers**

In this article I'll discuss the Double Opt-In Checkbox that can be configured to display in registration/checkout forms. How to configure it, what's possible, etc.

See: **Dashboard → s2Member → API / List Servers → Double Opt-In Checkbox**

---

Ordinarily, the checkbox is presented to a potential subscriber in order to get their permission to send them a confirmation email. And, so they are prepared for it come. However, it can also be disabled completely.

---

![](http://cdn.websharks-inc.com/s2member/uploads/2014/01/Selection_112.png)

---

## Double Opt-In Checbox Options

All of these options are presented under the assumption that your list server will require a double opt-in procedure. It’s very unusual that a list server would agree to allowing a single opt-in from my experience. If you can swing it though (and there are times when this is possible), then the checkbox would still be used (recommended); because it would serve as the single opt-in.

---

#### Yes – the box must be checked (checked by default). {.no-b-margin}
#### Yes – the box must be checked (unchecked by default). {.no-t-margin}

Both of these options mean the same thing. The only difference is that the box is either checked by default (or not). Both of these settings tell s2Member that it _should_ connect with your list server if the box is checked.

Both of these options also assume that this connection (via the API) is going to result in a confirmation email being sent to the potential subscriber. If you find a way to circumvent this (e.g., by getting permission from your list server to do so), then this simply means that a subscriber would be added to the list (with no confirmation) if the box is checked.

---

#### No, no not display (or require) the checkbox.

This tells s2Member that your list server integration is not dependent upon the checkbox. In short, all new registrants receive the confirmation email, because the checkbox is actually not in use at all. So checked or unchecked; it does not matter; the checkbox is not even being used. In a case like this, there is only a single opt-in (the confirmation email). If you find a way to circumvent the confirmation email (by getting permission from your list server to do so), this would be a blind subscription (no opt-in at all).
