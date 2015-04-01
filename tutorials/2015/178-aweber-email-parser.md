---
title: AWeber Email Parser
categories: tutorials
tags: aweber, api-list-servers
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/178
toc-enable: false
---

In the latest versions of s2Member you can integrate with AWeber's API (recommended) instead of through an Email Parser. However, if you decide to use an AWeber Email Parser instead, please don't use the built-in PayPal Email Parser that AWeber provides. Instead, s2Member would really prefer that you use a Custom Email Parser, specifically for s2Member (as seen below).

See: **Dashboard → s2Member → API / List Servers → AWeber Integration**

## AWeber Email Parser For s2Member

- **Description:** `s2Member Email Parser`
- **Trigger Rule:** `s2Member Subscription Request\n` (match on: **Body**)
- **Rule 1:** `\nEMail Address: *(.+?)\n` (match on: **Body**, store in: **Email**)
- **Rule 2:** `\nFull Name: *(.*?)\n` (match on: **Body**, store in: **Name**)
- **Rule 3:** `\nAd Tracking: *(.*?)\n` (match on: **Body**, store in: **Ad Tracking**)
- **Rule 4:** `\nRole: *(.*?)\n` (match on: **Body**, store in: **Misc**)

---

![](https://camo.githubusercontent.com/df16ccea55ba07b5e7554b7622e6ba7ad90423d8/687474703a2f2f7777772e7072696d6f7468656d65732e636f6d2f666f72756d732f646f776e6c6f61642f66696c652e7068703f6d6f64653d766965772669643d353637)

---

## Running Tests Against the s2Member Parser

You can run tests (inside your AWeber account) against your Custom Email Parser using this message body (as seen below). Be sure to leave the `Fake: header` and double line break in there during live testing. AWeber provides a box where you can paste this in to test your Email Parser.

```text
Fake: header


s2Member Subscription Request
s2Member w/ PayPal Email ID
Ad Tracking: s2Member-test
EMail Address: xxxxx
Buyer: xxxxx
Full Name: xxxxxx
First Name: xxxxx
Last Name: xxxxx
IP Address: xxxxx
User ID: 9
Login: xxxxxxxx
Role: subscriber
Level: 0
CCaps:
- end.
```

---

![](https://camo.githubusercontent.com/f57b619f6ea09164bcf55dec2f5f655ad7d7e48f/687474703a2f2f7777772e7072696d6f7468656d65732e636f6d2f666f72756d732f646f776e6c6f61642f66696c652e7068703f6d6f64653d766965772669643d353638)
