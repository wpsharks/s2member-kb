---
title: '[s2Member-Profile /] Shortcode'
categories: features
tags: s2member-profile
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/195
---

The `[s2Member-Profile /]` Shortcode makes it easy for users to edit/update their profile upon logging into your site. See: **WordPress Dashboard → s2Member → General Options → Member Profile Modifications** for additional details and other options. 

The `[s2Member-Profile /]` shortcode generates a Profile Editing form that allows users to update their name, email address, password, and any custom fields that you've configured. This shortcode is generally placed on a separate page called "Edit Profile", or simply "Profile", and then linked to from a convenient location after the user logs in.

![2015-04-22_19-17-19](https://cloud.githubusercontent.com/assets/53005/7287593/4782f11e-e924-11e4-8e79-a1934f57ebab.png)

![2015-04-22_19-16-40](https://cloud.githubusercontent.com/assets/53005/7287582/20eb94fc-e924-11e4-9b36-b693b17a3591.png)


## Can Administrators Update User Profiles?

Absolutely. Users can be edited/updated in various ways from your WordPress Dashboard at any time you like. See: **Dashboard → Users**. Find (or search for) a specific user and click **[Edit]** to access their WordPress profile, along with all of the editable fields provided by s2Member.

### s2Member User Configuration

When s2Member is enabled, each user account inside your WordPress Dashboard will contain additional s2Member-specific configuration. These fields are automatically populated with information related to the members account, such as their IP address when signing up, their transaction ID if they purchased something, etc. You can also tell s2Member to perform certain actions from here, such as resetting the user's password and resending the welcome email.

![2015-04-22_19-03-13](https://cloud.githubusercontent.com/assets/53005/7287419/6279f988-e922-11e4-9398-1addd39cf379.png)

### s2Member Profile Fields

If you've created Custom Registration/Profile Fields (see **WordPress Dashboard → s2Member → General Options → Registration/Profile Fields & Options**), these will also appear when editing the users account inside your WordPress Dashboard. As an administrator, you can modify any of these Custom Registration/Profile Fields by editing the users account and updating the fields. 

Custom Registration/Profile Fields can be configured to show up during registration, only after registration, or not at all (hidden from the user and only visible to the site owner). Examples of such fields may include the member's primary domain, if your site is selling a software application like s2Member, or a Terms and Conditions checkbox to show that the member has agreed to the Terms and Conditions.

![2015-04-22_19-02-20](https://cloud.githubusercontent.com/assets/53005/7287451/ae361294-e922-11e4-8b7b-76e7df8eb5ca.png)