---
title: Implementing SSL (HTTPS) on an s2Member Site
categories: tutorials
tags:  s2member-security-badge, security
author: patdumond
github-issue: https://github.com/websharks/s2member-kb/issues/249
---

In [Introduction to TLS/SSL and Why You Need It on Your s2Member Site](http://s2member.com/kb-article/introduction-to-tlsssl-and-why-you-need-it-on-your-s2member-site/) we talked about the reasons you should secure your site using SSL and HTTPS. These reasons included lowering the risk of data theft on your site, engendering user trust, and even improving your site's Google rankings. Now we are going to talk about **how** to implement SSL on your s2Member site.

## Step 1: Purchase an SSL Certificate

You can buy SSL Certificates from your web hosting provider or a third-party seller. Often when you buy the certificate from your web host, installation of the SSL Certificate will be included in the price. Review all of your options to find the best fit for your technical skill and your wallet.

An SSL certificate requires a dedicated IP address, which you must purchase from your web hosting provider. If you purchase your SSL certificate through your web hosting provider, you should be able to obtain the dedicated IP address as part of the same transaction. 

If you decide to go it alone and buy your certificate from a third-party seller, you'll find SSL certificates for prices ranging from $1.99 to more than $1,500.00 a year. While researching for article, I considered buying a certificate from a third-party seller and installing it myself. Then I discovered that my hosting provider doesn't allow users to install the certificates, so I did what I usually do: I bought the certificate from them. It was easier and considering the 'free' installation, the cost is actually in line with purchasing from a cheaper vendor.

The information I needed to provide to my hosting provider when purchasing the SSL certificate was as follows:

- E-mail address
- Passphrase: 8-20 alphanumeric characters
- Domain name
- Location: City - State - Country
- Organization (This is **not** optional, so if you are an individual you will have to make one up.)
- Company Division (Also **not** optional.)
- Cipher strength (This is the number of bits used in the keys to encrypt traffic. You may or may not be offered a choice of cipher strength but in 2015, the choice is usually either 2048-bit or 4096-bit. If there is no price difference, and there usually isn't, stronger, i.e. more bits, is better.)

## Step 2: Install the Certificate

You might be able to install your certificate yourself, but a lot of web hosting providers do not allow root-level access to their servers. If you want to install the certificate yourself, most hosting providers that do permit users to install SSL certificates provide specific instructions in their Support Knowledge Base.

My hosting provider doesn't allow user-installed SSL certificates and does not charge extra for installation when you buy the certificate through them. So that is the route I took on the test site that I used in researching this article. (Don't worry, I have plenty of other uses for the site as well.)

## Step 3: Set up WordPress for SSL and HTTPS

Once the certificate has been purchased and installed, you are ready to set up WordPress and s2Member to work with SSL and HTTPS. For this article, we are going to assume you want to access your entire site via HTTPS: front-end and back-end. 

While it's entirely possible to use both protocols (HTTP _and_ HTTPS) on your website at the same time, there are excellent reasons for choosing a single protocol (HTTP _or_ HTTPS) and sticking with it throughout your website, especially if you require users to log in to your site. 

The most important reason is that web browsers treat HTTP (insecure) and HTTPS (secure) URLs separately and store sessions for each protocol separately. That means if you login to a site using HTTPS (secure), and then visit an HTTP (insecure) page, the browser will suddenly treat that HTTP (insecure) page as a separate session and the user will appear to be logged out. To avoid this confusion, it's best to stick with one protocol (in this case, HTTPS) and load all pages over HTTPS.

### Step 3a: Update Your WordPress URLs

In your WordPress Dashboard, navigate to **WordPress Dashboard → Settings → General**. Change both the *WordPress Address (URL)* and the *Site Address (URL)* so that it begins with `https` instead of `http`. Click the **Save Changes** button.

![Updating WordPress URLs](https://cloud.githubusercontent.com/assets/9320495/9689018/ef77183c-5300-11e5-82b5-3d6790a67c04.png)

**Advanced Tip:** Setting these URLs so that they have an `https://` protocol will automatically force WordPress into `FORCE_SSL_ADMIN` mode. See [this](https://github.com/WordPress/WordPress/blob/4.3/wp-includes/default-constants.php#L266) WordPress source code line. (When `FORCE_SSL_ADMIN` is true, `FORCE_SSL_LOGIN` is [moot](https://github.com/WordPress/WordPress/blob/4.3/wp-includes/default-constants.php#L272-L280).)

### Step 3b: Update Your `.htaccess` File

_Put this at the very top of your WordPress root `.htaccess` file. Or, if you have an existing block that forces a particular `HTTP_HOST` (some sites do that), then put this right after that block._

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

#### What If I Can't Edit My `.htaccess` File?

Some web hosting providers do not allow you to access or edit hidden files such as `.htaccess`. If that's the case you *should* be able to ask them to make this change for you, but, failing that, there are some WordPress plugins that should do the trick.

* [Easy HTTPS Redirection](https://wordpress.org/plugins/https-redirection/)
* [WP Force SSL](https://wordpress.org/plugins/wp-force-ssl/)

#### Why Isn't it Enough to Update my WordPress URLs?

The `redirect_canonical()` function in WordPress will only redirect away from an unencrypted `http://` request when it's a `GET` or `HEAD` request. See [this](https://github.com/WordPress/WordPress/blob/4.3/wp-includes/canonical.php#L44-L46) WordPress source code line. So for that reason, a `.htaccess` entry to force SSL is recommended. Without a server configuration (or a plugin) that forces SSL across all pages, WordPress leaves it possible for HTML markup to be generated with `<form action="http://..." >` and to therefore have that data `POST`ed over an insecure connection; either by mistake (e.g., a misbehaving theme/plugin) or with malicious intent.

In addition, if there are any files/forms on the site that are outside of WordPress, those would not be covered by `redirect_canonical()` in WordPress, so it is best to have a server configuration that forces SSL in that case also.

## Step 4: Set up s2Member for SSL

There are no required steps to set up s2Member for SSL. You can add a [custom field to your protected pages](http://s2member.com/kb-article/why-are-ssl-and-non-ssl-pages-logging-out-my-members/) to ensure they are served over SSL, but this is unnecessary if you are serving your entire site over SSL as suggested above.

## Related Articles

* [s2Member KB: Introduction to TLS/SSL and Why You Need It on Your s2Member Site](http://s2member.com/kb-article/introduction-to-tlsssl-and-why-you-need-it-on-your-s2member-site/)
* [s2Member KB: Why are SSL and non-SSL pages logging-out my members?](http://s2member.com/kb-article/why-are-ssl-and-non-ssl-pages-logging-out-my-members/)
* [s2Member KB: How to Avoid Login Issues](http://s2member.com/kb-article/how-to-avoid-login-issues/) 
* [WordPress Codex: Administration Over SSL](http://codex.wordpress.org/Administration_Over_SSL)
