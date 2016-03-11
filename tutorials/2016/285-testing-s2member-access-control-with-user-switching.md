---
title: Testing s2Member Access Control with User Switching
categories: tutorials
tags: s2if, conditional-tags, membership-levels
author: renzms
github-issue: https://github.com/websharks/s2member/issues/834
---

A common task while setting up and managing an s2Member site is to test your specific membership levels and/or Custom Capabilities to make sure that content is appearing properly for the intended audience. The common solution to this problem can be tedious to some as it involves creating a test user (or multiple test users), and then logging out and back in as the user to view each page. The method described in this article allows site owners easily to view a page/post as one of their subscribers (or as a specific test user that you may have set up) for testing different membership levels and/or Custom Capabilities.

## The User Switching Plugin

Using the [User Switching](https://wordpress.org/plugins/user-switching/) plugin, you can easily test and switch between different users with different membership levels or Custom Capabilities. The plugin allows you to instantly switch between user accounts in WordPress by simply clicking to swap users. You will be logged out of one account and logged into another as soon as you click to switch. This is a great and easy method for test environments where you would need to switch between multiple accounts by logging out and logging in repeatedly.

Here are some features of the plugin as highlighted by the developers of the plugin:
> - Switch user: Instantly switch to any user account from the Users screen.
- Switch back: Instantly switch back to your originating account.
- Switch off: Log out of your account but retain the ability to instantly switch back in again.
- It's completely secure (see the Security section below).
- Compatible with WordPress, WordPress Multisite, BuddyPress and bbPress.


After installing and activating the plugin, go to the **Users** section of your WordPress Dashboard, here you can switch between different users by hovering over a user and clicking `Switch To`. For this example, first we will create 4 users for 4 different membership levels (Levels 1 - 4) , you may create as many users as needed for testing with different membership levels and/or Custom Capabilities.

### How to Use the User Switching Plugin

Once you've installed the [User Switching](https://wordpress.org/plugins/user-switching/) plugin, go to **WordPress Dashboard → Users**  and create one or more test users with the appropriate s2Member Level and/or Custom Capabilities. From the users list, you will see a new `Switch To` link underneath each user. By clicking the link, you will instantly switch to that user account. You can switch back any time to your main account by clicking the `Switch back` link on any WordPress Dashboard screen or in the WordPress Admin toolbar.

1. Go to **User → Add New User**, for this example we will add a user with username `Tester 1`. You can add any valid email if you wish, but no need to add a password or email the password to user as we will be using **User Switching** to switch users, and not actually logging in/logging out of each user/admin account. 

2. Then choose which membership level the test account should have, in this case `s2Member Level 1`.

     ![Add New Test User](https://cloud.githubusercontent.com/assets/13220018/12117770/db437708-b3fd-11e5-8aa3-dc1acc7ace7b.jpg)

3. If you wish to test Custom Capabilities, add the corresponding value of your Custom Capabilities to the **Custom Capabilities** field below under the **s2Member Configuration & Profile Fields**

     ![Add New Test User](https://cloud.githubusercontent.com/assets/13220018/12117912/902e8ba8-b3fe-11e5-83c0-de9aa32f582b.jpg)

4. We have now created 4 test users with 4 different Membership Levels.

     ![List of Test Users](https://cloud.githubusercontent.com/assets/13220018/12118005/19bb70ca-b3ff-11e5-8b9e-54bdcd6fea6f.jpg)

5. To switch to a user, hover over the username and click `Switch To`.

     ![Switch To User Link](https://cloud.githubusercontent.com/assets/13220018/12118129/c9bb74de-b3ff-11e5-8bcc-c6c400803db3.png)

6. To switch back, you can switch back via the Dashboard Notification or the Admin Bar.

     ![Switch Back to Admin Link](https://cloud.githubusercontent.com/assets/13220018/13573978/1c73b82e-e4bd-11e5-9c99-e9a2654c61d5.png)

You can verify if your shortcode for specific content is working properly by having two tabs/windows open: one for switching users and one for viewing content. Test by refreshing the tab/window for viewing and in the other tab/window switch users via the **Users** area in the WordPress Dashboard. You can now easily test your shortcode without having to log in and out of your site or remember different user passwords!

### Is User Switching Safe?

Yes, the User Switching plugin is safe. Here are a few common concerns: 

- _Is the User Switching plugin safe?_
- _Do you need to know users passwords?_
- _Can others users view my passwords?_
- _Can other users of my site switch user accounts?_

Here's what the User Switching plugin developers have to say about the plugins security:

> - Only users with the ability to edit other users can switch user accounts. By default this is only Administrators on single site installs, and Super Admins on Multisite installs.
- Passwords are not (and cannot be) revealed.
- Uses the cookie authentication system in WordPress when remembering the account(s) you've switched from and when switching back.
- Implements the nonce security system in WordPress, meaning only those who intend to switch users can switch.
- Full support for administration over SSL (if applicable).

Source: https://wordpress.org/plugins/user-switching/

For more information please see:

- [`[s2If /]` Simple Shortcode Conditionals](https://s2member.com/kb-article/s2if-simple-shortcode-conditionals/)
- [How do WordPress Roles/Capabilities work?](https://s2member.com/kb-article/how-do-wordpress-rolescapabilities-work/)
- [Video: Custom Capabilities for WordPress](https://s2member.com/kb-article/video-custom-capabilities-for-wordpress/)


## Other ways of simulating logins

It's also possible to [use an MU Plugin to switch users](https://gist.github.com/raamdev/50532716369782f89b1e), however for security reasons we recommend using the User Switching plugin described above.
