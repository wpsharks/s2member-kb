---
title: Why are my Custom Registration Fields not appearing on the Pro-Form?
categories: questions
tags: login-registration, registration-profile-fields, pro-forms, troubleshooting
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/48
toc-enable: false
---

When you create a Custom Registration/Profile Field with s2Member (see: **Dashboard ⥱ s2Member ⥱ General Options ⥱ Registration/Profile Fields & Options ⥱ Add New Field**), you will need to make sure that **Applicable Membership Levels** is set to the same Membership Level as your Pro-From. 

For instance, if you're using Level 1 Pro-Forms, set this to `1`. If you want the Custom Registration Field to show up on all Pro-Forms, set this to `all` (the default). 

You'll also want to verify that the **Allow Profile Edits** option is set to the appropriate setting.

![2015-01-20_18-09-28](https://cloud.githubusercontent.com/assets/53005/5828209/84039b0e-a0cf-11e4-8f27-4ff263b024ef.png)

#### I'm still not seeing my Custom Registration Fields!

Keep in mind that Pro-Forms presented to logged-in users will not display Custom Registration Fields. If you want logged-in users to modify Custom Registration Fields, you can use the `[s2Member-Profile /]` shortcode. Please see: **Dashboard ⥱ s2Member ⥱ General Options ⥱ Member Profile Modifications**.