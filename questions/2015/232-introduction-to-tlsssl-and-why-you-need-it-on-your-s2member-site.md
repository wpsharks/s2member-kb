---
title: Introduction to TLS/SSL and Why You Need It on Your s2Member Site
categories: questions
tags: security, s2member-security-badge
author: patdumond
github-issue: https://github.com/websharks/s2member-kb/issues/232
---

What do words like "cyber-stalking", "identity theft", "credit card fraud", and "packet sniffing" have to do with your website? Hopefully, not much. If you are reading this, however, then you probably either own or manage a membership website. Almost by definition, you collect your members' personally identifiable information on that site. If you are doing that on an unencrypted web page, you are placing your members' data and your website (and livelihood) in jeopardy.  Everytime a user fills out a form on your site their information may be leaving your site in clear text any hacker or "script kiddie" can grab. If you display user information on profile pages or membership directories, that information is unencrypted as well. 

## What is TLS/SSL? 

According to [Wikipedia](https://en.wikipedia.org/wiki/Transport_Layer_Security) (which just recently implemented the HTTPS protocol on all of their websites):

 >Transport Layer Security (TLS) and its predecessor Secure Sockets Layer (SSL) are cryptographic protocols designed to provide communications security over a computer network.

SSL is an out-dated protocol and has been superseded by TLS. However, the term "SSL" is commonly used to describe the protocols implemented by the **HTTPS** protocol on the web. These protocols use certificates and asymmetric cryptography to ensure that your web browser is talking to the site you intended. This is called "authentication." 

Once each side of the connection is sure they know who is on the other end of the link, they negotiate a session key to encrypt all data flow for the duration of the connection. Authentication ensures that the computer on the other end of the connection is PayPal, not some "man in the middle". Encryption ensures the data cannot be read without the session key. 

You can tell you are using `HTTPS` and not plain old `HTTP` by looking at the address bar of your browser. The address of the website should be preceded by `HTTPS` instead of `HTTP`. If you have a valid `HTTPS` connection, you'll see a closed padlock.  If the padlock is not closed or you see another symbol instead of a padlock, hover your cursor over the image, and you'll get more information about the connection. 

![A site secured with HTTPS](https://cloud.githubusercontent.com/assets/53005/9013196/7f8c5bd8-3788-11e5-8719-beaa22e071e9.png)

## Why Use TLS/SSL

### Authentication and Encryption Lower the Risk of Data Theft

Implementing TLS/SSL on your website secures network communication between your site and other sites (such as PayPal or Stripe). It does not prevent your website itself from attack, but it does prevent your users' data from being read while it is traveling "through the ether".  One of the obligations you undertake when you ask people for their personal information is the duty to do everything you can to protect that information from theft by third-parties. Implementing TLS/SSL on your website is part of that obligation. 

### That Little Padlock Engenders Customer Trust

Try googling "how do I know if a website is safe" or "how do I know if a website is secure" and check out as many results as you want. Somewhere on that page you'll see words like "Look for the little green padlock" or "The site has a padlock or unbroken key".  People trust that little green padlock. 

### Implementing HTTPS Can Raise Your Search Engine Rankings (and vice versa)

Google started giving a [slight ranking benefit to websites using `HTTPS` in 2014](http://googlewebmastercentral.blogspot.com/2014/08/https-as-ranking-signal.html).  While Google said this benefit was "very lightweight" and carried less weight than other factors, such as high-quality content, every little bit helps in the never-ending quest for more traffic. Also noteworthy was Google's reasoning for the change and for possibly strengthening the boost in the future. They said they wanted to "encourage all website owners to switch from HTTP to HTTPS to keep everyone safe on the web".  

[SearchMetrics posted in March 2015](http://blog.searchmetrics.com/us/2015/03/03/https-vs-http-website-ssl-tls-encryption-ranking-seo-secure-connection/) that they had begun seeing positive effects in SEO rankings due to HTTPS implementation. 

## How Do I Implement SSL?

You've seen the benefits of using TSL/SSL:

* Securing user's personal information during network transport.
* Engendering user trust with that "little green padlock."
* Giving your Google rankings a boost,

Now you probably want to know how to implement TSL/SSL on your s2Member site. Well, stay tuned for our follow-up article, **How Do I Implement TSL/SSL on my s2Member Site?**