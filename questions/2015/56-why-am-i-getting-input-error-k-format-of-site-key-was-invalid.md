---
title: Why am I getting "Input Error: K: Format Of Site Key Was Invalid"?
categories: questions
tags: pro-forms, captcha-anti-spam-security, troubleshooting
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/56
---

> Why am I getting an error: "Input Error: K: Format Of Site Key Was Invalid" underneath the Security Code section of my Pro-Forms?

If you you're getting an error that says **Input Error: K: Format Of Site Key Was Invalid** on your s2Member Pro-Forms in the **Security Code** section, this indicates a problem with your CAPTCHA Anti-Spam Security configuration.

![input error- k- format of site key was invalid](https://cloud.githubusercontent.com/assets/53005/5847782/47587e92-a19f-11e4-92f5-6ad50b819ba7.png)

To fix this issue, visit **Dashboard → s2Member (Pro) → General Options → CAPTCHA Anti-Spam Security** and make sure the **reCAPTCHA™ Public Key** and **reCAPTCHA™ Private Key** fields are empty (clear them both); then click the **Save All Changes** button at the bottom.

![2015-01-21_18-59-55](https://cloud.githubusercontent.com/assets/53005/5847860/1f93b470-a1a0-11e4-80b5-c3d66e29a9e6.png)

Now you will need to [Configure CAPTCHA Anti-Spam Security with Your Own reCAPTCHA Keys](https://github.com/websharks/s2member-kb/issues/55). Please follow the steps outlined in that KB article.

After following all of these steps, you should no longer be getting the **Input Error: K: Format Of Site Key Was Invalid** error message.
