---
title: Configuring CAPTCHA Anti-Spam Security
categories: tutorials
tags: captcha-anti-spam-security, shortcodes, pro-forms
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/55
---

s2Member Pro Forms for Stripe, PayPal Pro, and Authorize.Net (including Free Registration Forms) can be configured with s2Member to use Google's reCAPTCHA™ service (which is free). Simply add the `captcha="clean"` attribute to your Pro-Form shortcode. Very easy.

s2Member comes with a default set of reCAPTCHA™ Keys, both Public and Private. If you leave the default configuration (i.e., leave the `reCAPTCHA™ Public Key` and `reCAPTCHA™ Private Key` fields empty), s2Member will simply use its own default set of Keys for reCAPTCHA™. However, if you're using s2Member Pro Forms, we do suggest that you acquire your own set of reCAPTCHA™ Keys (_it's free_). It's better to have your own set of Keys, specifically for your domain. 

This tutorial will walk you through acquiring your own set of Public/Private Keys for the reCAPTCHA™ service.

### Step 1: Acquire Public/Private reCAPTCHA Keys

Visit the [reCAPTCHA Admin Page](http://www.s2member.com/recaptcha-create-keys) and sign in with your Google Account if prompted. (If you don't have a Google Account, you can create a free account.)

You will then see a page that contains a box titled **Register a new site**:

![2015-01-21_19-26-24](https://cloud.githubusercontent.com/assets/53005/5848195/d632a4f4-a1a3-11e4-9de8-74b7f662c651.png)

- Fill in the **Label** with something applicable, such as the name of your site.
- Fill in the **Domains** box with your domain name (e.g., `www.example.com`, or `example.com`)
- Click the **Register** button

The following page will display your **Site key** and your **Secret key**:

![2015-01-21_19-28-51](https://cloud.githubusercontent.com/assets/53005/5848233/2ceb5840-a1a4-11e4-8621-61713fc8e9bc.png)

Copy these and note them down somewhere. We will use these in the next step, _Configuring s2Member with your reCAPTCHA Keys_.

### Step 2: Configuring s2Member with your reCAPTCHA Keys

Now that you have your own Public (aka "Site key") and Private (aka "Secret key") reCAPTCHA keys, visit `Dashboard → s2Member (Pro) → General Options → CAPTCHA Anti-Spam Security` and fill the new keys into the `reCAPTCHA™ Public Key` and `reCAPTCHA™ Private Key` fields. Then click the **Save All Changes** button at the bottom.

![2015-01-21_19-09-47](https://cloud.githubusercontent.com/assets/53005/5848100/ca595c28-a1a2-11e4-947a-c6dbbc487f86.png)

That's it! Your s2Member plugin is now configured with your own set of reCAPTCHA keys!
