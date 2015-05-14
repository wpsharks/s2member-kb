---
title: Login Redirection URL is not working at all, why?
categories: questions
tags: login-welcome-page, troubleshooting
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/209
toc-enable: false
---

> What would cause free subscribers to be taken to the WordPress dashboard after login and paid members to go to the home page. Neither going to a login welcome page?

Definitely unexpected behavior. Here are some thoughts that come to mind, but these are all just guesses. It could be any number of things. The way to go about debugging something like this, is to isolate s2Member in a clean installation. See: [Testing in a Clean WordPress Installation](http://s2member.com/kb-article/testing-in-a-clean-wordpress-installation/).

## Possible Causes Of Login Redirection Problems

- Theme or plugin conflict; i.e., another plugin (or your theme) behaves in ways that conflict with s2Member. See: [Testing in a Clean Installation](http://s2member.com/kb-article/testing-in-a-clean-wordpress-installation/)

- The login form you are using to run tests, includes the `redirect_to` variable that is ultimately passed over to the `/wp-login.php` handler (part of the WordPress core). Whenever anyone logs in, if the login request includes a specific `redirect_to` location, that will override the default Login Redirection URL that you configured with s2Member.

  In other words, if your login form contains something like this, it can lead to confusion.

  ```
  <input type="hidden" name="redirect_to" value="http://yoursite.com/" />
  ```

- Your are using the s2Member Pro Login Widget, and you specified a specific `redirect_to` URL that applies to all users, and this is what you are using to run tests with. Again, this points back to the use of a `redirect_to` value. If this is set to something other than "Login Welcome Page", it can lead to confusion.

  ![2015-05-14_10-28-04](https://cloud.githubusercontent.com/assets/1563559/7638824/f2e349f4-fa23-11e4-814d-80ea480daffc.png)
