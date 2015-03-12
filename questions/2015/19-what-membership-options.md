---
title: What is the difference between the Membership Options page and the register page?
categories: questions
tags: membership-options-page, login-registration
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/19
---

In s2Member, the Membership Options Page is a sales page that will list the available membership options that you make available. This will generally include a set of payment buttons generated with s2Member; or perhaps a link to one of your s2Member Pro Forms where checkout is completed for an option the customer chooses.

The "register" page (e.g. `/wp-login.php?action=register`) is a part of the WordPress core and it's used by the lite version of s2Member when integrating with PayPal Standard Buttons. After a customer completes checkout, they are returned to your site and the registration form is how they acquire an account with the access they paid you for.

The register page (e.g. `/wp-login.php?action=register`) is generally not used whenever you have s2Member Pro. Pro Forms wrap the entire checkout process into a single step. Thus, registration occurs during checkout and the customer only needs to complete a single step to gain access.

See also: http://www.s2member.com/kb/customizing-your-lwp/
See also: http://www.s2member.com/kb/pro-forms/
