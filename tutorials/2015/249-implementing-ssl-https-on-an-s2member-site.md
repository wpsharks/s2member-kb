---
title: Implementing SSL (HTTPS) on an s2Member Site
categories: tutorials
tags:  s2member-security-badge, security
author: patdumond
github-issue: https://github.com/websharks/s2member-kb/issues/249
---

We talked about reasons to secure your site using SSL and HTTPS in [Introduction to TLS/SSL and Why You Need It on Your s2Member Site](http://s2member.com/kb-article/introduction-to-tlsssl-and-why-you-need-it-on-your-s2member-site/). These reasons included lowering the risk of data theft on your site, engendering user trust, and even improving your site's Google rankings. Now we are going to talk about **how** to implement SSL on your s2Member site.

## Purchase an SSL Certificate

You can buy SSL Certificates from your web hosting provider or a third-party seller. Often when you buy the certificate from your web host, installation will be included in the price. Check all your options for the best fit for your technical skills and your wallet. 

An SSL certificate requires a dedicated IP address, which you must purchase from your web hosting provider. You should be able to obtain the dedicated IP address as part of the same transaction with the certificate and installation. 

If you decide to go it alone and buy your certificate from a third-party seller, you'll find SSL certificates for prices ranging from $1.99 to more than $1,500.00 a year. While researching this KBA, I considered buying a certificate from a third-party seller and installing it myself. Then I discovered that my hosting provider doesn't allow users to install the certificates, so I did what I usually do: bought the certificate from them. It was easier and considering the "free" installation, the cost is actually in line with purchasing from a cheaper vendor.

The information I needed to provide for the SSL certificate:
* E-mail address
* Passphrase: 8-20 alphanumeric characters
* Domain name
* Location: City - State - Country
* Organization (This is **not** optional, so if you are an individual you will have to make one up.)
* Company Division (Also **not** optional.)
* Cipher strength (the number of bits used in the keys to encrypt traffic) (The seller may or may not offer you a choice of cipher strength. In 2015, this choice is usually either 2048-bit or 4096-bit. If there is no price difference, and there usually isn't, stronger (more bits) is better.)

## Install the Certificate

You might be able to install your certificate yourself, but a lot of web hosting providers do not allow root-level access to their servers. If you want to install the certificate yourself, most hosting providers that do permit it provide instructions in their Support Knowledge Base.

My hosting provider doesn't allow it and does not charge extra for installation when you buy the certificate through them. So that is the route I took on the test site I used in researching this article. (Don't worry, I have plenty of other uses for the site as well.)

## Set up WordPress for SSL and HTTPS

Once the certificate is purchased and installed, you are ready to set up WordPress and s2Member to work with SSL and HTTPS.  For this article, we are going to assume you want to access your entire site via HTTPS: front-end and back-end. 

There are excellent reasons for picking a protocol and sticking to it on your website, especially when you require users to log in. The most important to your users is that when a user clicks a link on a page reached via **HTTPS** to a page served over **HTTP** (or vice-versa), the browser creates a new session. Your members will be logged out and asked to log in again when switching protocols.

### Step 1: Setting Your WordPress URLs

In your WordPress Dashboard, navigate to **WordPress Dashboard → Settings → General**. Change both the *WordPress Address (URL)* and the *Site Address (URL)* so that it begins with `https` instead of `http`. Click the **Save Changes** button.

![updating-urls](https://cloud.githubusercontent.com/assets/9320495/9689018/ef77183c-5300-11e5-82b5-3d6790a67c04.png)


Setting these URLs so that they have an `https://` protocol will automatically force WordPress into `FORCE_SSL_ADMIN` mode. See [this](https://github.com/WordPress/WordPress/blob/4.3/wp-includes/default-constants.php#L266) WordPress source code line. When `FORCE_SSL_ADMIN` is true, `FORCE_SSL_LOGIN` is [moot](https://github.com/WordPress/WordPress/blob/4.3/wp-includes/default-constants.php#L272-L280).

#### Why Isn't That Enough?

The `redirect_canonical()` function in WordPress will only redirect away from an unencrypted `http://` request when it's a `GET` or `HEAD` request. See [this](https://github.com/WordPress/WordPress/blob/4.3/wp-includes/canonical.php#L44-L46) WordPress source code line. So for that reason, a `.htaccess` entry to force SSL is recommended. Without a server configuration  (or plugin) that forces SSL, WordPress still leaves it possible for HTML markup to be generated with `<form action="http://..." >` and to have that data POSTd over an insecure connection; either by mistake (e.g., a misbehaving theme/plugin) or with malicious intent.

In addition, if there are any files/forms on the site that are outside of WordPress, those would not be covered by `redirect_canonical()` in WordPress, so it is best to have a server configuration that forces SSL in that case also.

### Step 2: Updating Your `.htaccess` File

*Put this at the very top of your WordPress root `.htaccess` file. Or, if you have an existing block that forces a particular `HTTP_HOST` (some sites do that), then put this right after that block.*

```
# BEGIN Force SSL
<IfModule rewrite_module>
  RewriteEngine on
  RewriteBase /
  RewriteCond %{HTTPS} !^on$ [NC]
  RewriteCond %{HTTP:X-Forwarded-Proto} !^https$ [NC]
  RewriteRule .* https://%{HTTP_HOST}%{REQUEST_URI} [R=301,L]
</IfModule>
# END Force SSL
```

#### What If I Can't Edit My `.htaccess` File

Some web hosting providers do not allow access to hidden files such as `.htaccess` to their customers. If that's the case you *should* be able to ask them to make this change for you, but, failing that, there are some WordPress plugins that will do the trick.

* [Easy HTTPS Redirection](https://wordpress.org/plugins/https-redirection/)
* [WP Force SSL](https://wordpress.org/plugins/wp-force-ssl/)

## Set up s2Member for SSL

There are no required steps to take to setup s2Member for SSL. You can add a [custom field to your protected pages](http://s2member.com/kb-article/why-are-ssl-and-non-ssl-pages-logging-out-my-members/) to ensure they are served over SSL, but this is unnecessary if you are serving your entire site over SSL as I suggested above.

## Related Articles

* [s2Member KB: Introduction to TLS/SSL and Why You Need It on Your s2Member Site](http://s2member.com/kb-article/introduction-to-tlsssl-and-why-you-need-it-on-your-s2member-site/)
* [s2Member KB: Why are SSL and non-SSL pages logging-out my members?](http://s2member.com/kb-article/why-are-ssl-and-non-ssl-pages-logging-out-my-members/)
* [s2Member KB: How to Avoid Login Issues](http://s2member.com/kb-article/how-to-avoid-login-issues/) 
* [WordPress Codex: Administration Over SSL](http://codex.wordpress.org/Administration_Over_SSL)
