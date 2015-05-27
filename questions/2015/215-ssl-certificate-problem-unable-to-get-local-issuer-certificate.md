---
title: SSL certificate problem: unable to get local issuer certificate?
categories: questions
tags: error-messages,troubleshooting
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/215
toc-enable: false
---

If you see this error message in your s2Member log files (i.e., in your `s2-http-api-debug.log` file), it indicates there was an HTTPS communication failure. This points to a larger issue that can lead to a _lot_ of unexpected behavior. Therefore, it's important to identify the underlying cause and get this fixed ASAP.

## The error message:

```
SSL certificate problem: unable to get local issuer certificate.
```

_This actually occurs within the [WP_Http class in the WordPress core](https://codex.wordpress.org/HTTP_API). It occurs as a result of s2Member attempting to connect to a URL over the `https://` protocol; where that communication fails on your server, because WordPress was unable to verify SSL certificate authenticity; i.e., the SSL certificate used by the URL that WordPress was connecting to could not be verified._

## What `https://` URLs does s2Member connect to?

- s2Member connects to remote APIs that you've integrated with; e.g., PayPal, Authorize.Net, Stripe, ClickBank, MailChimp, GetResponse, AWeber, etc.
- If you're running Pro-Forms, s2Member will also connect to its own API (runs on your server); i.e., a connection that occurs from your site, to your site. If your Pro-Form is being served over `https://` (recommended), then any behind-the-scenes communication with s2Member's own API will also occur over `https://`.

## Why does `https://` (SSL) communication fail?

#### Here are three of the most common causes:

1. Missing root CA required for **local** verification. If the SSL certificate that you purchased for your site requires a root CA (Certificate Authority) that is not included with the current copy of WordPress you're running, this problem can arise.

  The cURL extension (used by WordPress for remote communication) must be able to verify the SSL certificate for your site. If your copy of WordPress is not equipped with a root CA bundle that can perform a lookup on your own SSL certificate, you will have problems.

  ### Ways to fix this issue.

  1. Contact hosting company and request assistance; i.e., ask them to update the certificate bundle that your installation of WordPress uses.

  2. Or, simply disable SSL verification for your own site; i.e., trust that your own site is secure. This is accomplished by creating the following file in your installation of WordPress.

  Create this directory and file: `/wp-content/mu-plugins/local-ssl-no-verify.php`

    ```php
    <?php
    add_filter('https_local_ssl_verify', '__return_false');
    ```

2. Missing root CA required for **remote** verification.

  The cURL extension (used by WordPress for remote communication) must be able to verify the SSL certificate for any remote site that s2Member connects to. If your copy of WordPress is not equipped with a root CA bundle that can perform a lookup on the SSL certificate for Stripe, PayPal, Authorize.Net, ClickBank, MailChimp, etc... you will have problems.

  ### Ways to fix this issue.

  1. Contact hosting company and request assistance; i.e., ask them to update the certificate bundle that your installation of WordPress uses.

  2. Or, (**NOT recommended**, due to security issues) disable SSL verification for remote sites; i.e., trust they are secure. This is accomplished by creating the following file in your installation of WordPress.

  Create this directory and file: `/wp-content/mu-plugins/ssl-no-verify.php`

    ```php
    <?php
    add_filter('https_ssl_verify', '__return_false');
    ```

3. General connectivity issue; i.e., your server is under a heavy load. Or, the third-party service API that s2Member is connecting to is under heavy load. If you see this error _rarely_, it is not cause for great concern, but still worth investigating. If it appears daily, or in repetition, it's time to start running extensive tests and/or ask your hosting company for assistance.