---
title: Cloudbleed Bug @ CloudFlare: Steps You Should Take
categories: questions
tags: security
author: jaswsinc
github-issue:
github-issue: https://github.com/websharks/s2member-kb/issues/325
---

<img src="https://s2member.com/wp-content/uploads/2017/02/cloudbleed.png" alt="Cloudbleed" style="float:right; width:128px; border:1px solid #333; border-radius:.25em;" />

If you haven't already heard, [Cloudbleed](https://www.wordfence.com/blog/2017/02/cloudflare-data-leak/) is the latest Internet superbug. It has impacted thousands of sites, and potentially millions of Internet users. The Cloudbleed bug was discovered by [Tavis Ormandy](https://twitter.com/taviso), a young researcher at Google's Project Zero, who wrote the following while investigating the depth of this problem:

---

> We keep finding more sensitive data that we need to cleanup. I didn't realize how much of the internet was sitting behind a Cloudflare CDN until this incident. The examples we're finding are so bad, I cancelled some weekend plans to go into the office on Sunday to help build some tools to cleanup. I've informed cloudflare what I'm working on. I'm finding private messages from major dating sites, full messages from a well-known chat service, online password manager data, frames from adult video sites, hotel bookings. We're talking full https requests, client IP addresses, full responses, cookies, passwords, keys, data, everything.

Source: <https://bugs.chromium.org/p/project-zero/issues/detail?id=1139#c5>

---

### Will the Cloudbleed bug impact my WordPress site?

The first question you should ask: _"Am I using CloudFlare?"_.

<span style="font-style:italic; color:green;">If you aren't, then Cloudbleed should have NO impact on your WordPress site.</span>

<span style="font-weight:bold; color:#980000;">If you are (or were) using CloudFlare</span>, or if the hosting company that handles your site does, you are potentially affected by this bug. While [CloudFlare has stated](https://blog.cloudflare.com/incident-report-on-memory-leak-caused-by-cloudflare-parser-bug/) that only a few thousand sites were 'affected' by this bug, we feel they are slightly downplaying the larger impact. Why? Because the so-called 'affected sites' that were leaking information from the CloudFlare network are not the end of the story.

The sites that were officially 'affected' were leaking data from all over the CloudFlare network, and research still seems to be underway in an effort to determine just how bad it all was. For the moment, I think we should assume that even if your site isn't on one of the [affected lists](https://github.com/pirate/sites-using-cloudflare/blob/master/README.md) that are now circulating the web, any of the affected sites may have leaked information from **your** site, assuming your site was using CloudFlare services from October 22nd, 2016 (late last year), up until just a couple days ago.

### Will I be impacted by Cloudbleed personally, even if I have never used CloudFlare?

Aside from WordPress, s2Member, Comet Cache, or anything to do with services you use at CloudFlare, everyone has potentially been affected by Cloudbleed. Cloudbleed caused thousands of sites to leak data from all over the web. Therefore, your own personal information may (may) have been leaked at some point by a website other than your own; i.e., a site using CloudFlare.

How is that the case? Well, if you consider that most of us log into various sites using our Twitter, Facebook, GitHub, and other social networking accounts. And, if you consider there were many sites leaking information going back to October of last year. There's a chance that your own personal credentials may have been leaked inadvertently by sites that were using CloudFlare services. _Yes, an oh s*** moment!_

Also, as I understand it, even if you didn't interact with any of the so-called 'affected' sites, if you interacted with _any_ site on the CloudFlare network, some of your personal information may have been leaked through CloudFlare by the affected sites. Realizing this, you can see that the probability rises well beyond the few thousand officially affected sites. It extends to 5+ million sites using CloudFlare services. So who knows how much information CloudFlare spilled out for all the world to see. Some of it was even indexed by Google and other search engines.

---

### What steps should I take to secure my WordPress installation?

I suggest reading [this article](https://www.wordfence.com/blog/2017/02/cloudflare-data-leak/) posted by WordFence. To summarize some of their suggestions, and add a few of our own, here is a checklist that you should follow if you're running WordPress + CloudFlare.

<div class="li-margins"></div>

1. Change all of the security salts in your `wp-config.php` file as suggested by WordFence. This will effectively log all users out of their account and force them to establish a new session with your site. WordPress uses the security salts in your `wp-config.php` file to encrypt authentication cookies, which may have been exposed by the Cloudbleed event. So changing the keys, forcing everyone to log out and then back in again, is an excellent first step. Your security salts will appear in lines that resemble the following.
  
  _**Tip:** You can use [this tool](https://api.wordpress.org/secret-key/1.1/salt/) provided by WordPress to generate new keys._
  
  ```
  define('AUTH_KEY',         '<}|ARj5ZRB*{nP,;E[gw|M/Y1FjYk)2RN&[Rt;Sr=9GfO{:!@}[!?JzqhIc*y#lR');
  define('SECURE_AUTH_KEY',  'm1.VmY.{E-a$,s1=NyiqH0W#~|BDpDd*9-{I!PP</!z)rn-|:Xae$~iM^6q(e;q;');
  define('LOGGED_IN_KEY',    'p|jhwjhcf:ssva/}PHt<Q/s8@-%*%LeP.w*x.P]Lx,ttp}}j6m_.-f<!qvfN8qI1');
  define('NONCE_KEY',        'bXUwe!b-3GST~|KiWul?<dfH=V9,S:*`OJR*9@sPli0!DV1>cY:TGee~#[,jXcI%');
  define('AUTH_SALT',        'tE{K~NoAj@pnSWQX`?2A5V78FRIJ~:5`U1Qbp>O(k^yxJ1kzju[yKVfmfZ`T*@)j');
  define('SECURE_AUTH_SALT', 'ef*R+>|Cw]l}>}0]<A{/*?CWRG)yZa@#.3O&Ip*y3o e[zv#,2-FzYZJh*wEYqrq');
  define('LOGGED_IN_SALT',   'Cqf<nu;G+]iu8&,m%Z3h]$-[dpi7r;;vMWTE<RZU&v*F}S(p!-2(}1l>DF5WLB9g');
  define('NONCE_SALT',       '#;EyCBMQf|M O]]Nnx/<g~9a%: +V)0bXc09WnkB~l++Wjh*LL_.ThR,}-_OQ`,m');
  ```

2. Next, change your own WordPress administrator password, and ask all of your team members to do the same thing; i.e., force them to do so, or do it for them. Anyone with administrative, editor, author, or contributor access to your site is potentially a higher risk. If any of their information was leaked, you'll be thwarting problems by changing their authentication credentials.

3. Review your theme configuration options, and review all plugin configuration options, for each plugin that you have active (or _had_ active during the Cloudbleed event, which started in October of last year). You'll want to look for any configuration options that might be used to form the basis of a checksum, hash, or to authenticate users via cookies. In some cases it could be worth your time to seek advice from the original theme/plugin developer. Generally speaking, it's a good idea to change _all_ security salts in WordPress, including any that are associated with themes/plugins you are running; i.e., Better to be safe than sorry — for your benefit and for the benefit of your users.

  **In the case of s2Member,** you should consider changing your s2Member Security Encryption Key.  
  See: **WP Dashboard → s2Member → General Options → Security Encryption Key**  
  _**Warning:** BEFORE you do this, see the section below explaining the impacts of changing your s2Member Security Encryption Key._
  
  If you're using the s2Member Pro Remote Operations API, you should also change your **Pro Remote Operations API Key**.  
  See: **WP Dashboard → s2Member → API / Scripting → Pro API For Remote Operations**
  
4. If you're using a caching plugin for WordPress (e.g., **Comet Cache**, WP Rocket, W3 Total Cache, WP Super Cache), you should immediately wipe the entire cache directory and start fresh. Why? Because there is always the chance that your site is on the affected list. If it is, you may have data that was leaked from other sites in your cache directory, which was put there by CloudFlare via the Cloudbleed bug. As a courtesy to all site owners using CloudFlare, please clear your cache and start fresh.

---

### s2Member Security Encryption Key

We suggest reading the details below, and then consider changing this.  
See: **WP Dashboard → s2Member → General Options → Security Encryption Key**

Your s2Member Security Encryption Key is used throughout s2Member's source code for many different things. Most uses of this key are related to transactional processing within a particular session. So changing the key won't really impact these scenarios in any significant way. Your Security Encryption Key is simply there to enhance security of data that is being transmitted by a user to the s2Member software, between s2Member and a payment gateway, or between s2Member and itself when calls are made to it's own API.

Since most uses of this key are session-based, changing the key will help secure new sessions, and will not impact old sessions that are already terminated. A 'session' being most commonly represented by an HTTP exchange that takes place within a 1-2 second window of time. Once the exchange is over, the key can change with no repercussions. However, there _are_ exceptions, as noted below.

### BEFORE changing your s2Member Security Encryption Key

**WARNING:** There are a few cases when use of your Security Encryption Key is more long-term. These cases include: Specific Post/Page Access Links, Registration Access Links, the `s2member_encrypt()` and `s2member_decrypt()` functions, the s2Member Pro Remote Operations API; and it can also have a long-term impact on IPN communication, because some data analyzed by s2Member includes a checksum that depends on your key.

<div class="li-margins"></div>

- **Specific Post/Page Access Links:** If you sold access via s2Member's [Specific Post/Page Access](https://s2member.com/kb-article/understanding-specific-postpage-access-restrictions/) functionality, you have customers out there with email receipts that contain a link which grants them access to specific Posts/Pages you've sold them. Changing your Security Encryption Key will render all of their links invalid/expired. It will not impact new transactions, but it will nullify those from the past with the old key.

  Therefore, if you're using Specific Post/Page Access in s2Member, it's worth weighing the ups/downs associated with changing your Security Encryption Key. We realize this is a tough call, but it's one you'll need to make.
  
  You might be thinking, _"Do I move forward knowing there is a chance it was exposed, but figure it was not and call it day? Or do I change my s2Member Security Encryption Key as a precaution and deal with customers potentially complaining?"_

  My suggestion is that you change it. Then, as a workaround, send your customers new links if they write in, which you can generate with s2Member. For example, if you're using Stripe, see: **WP Dashboard → s2Member → Stripe Pro-Forms → Specific Post/Page Access Links**
  
- **Registration Access Links:** This is of lesser concern. First off, Registration Access Links only apply to 'Button' integrations in s2Member, they are not used by Pro-Forms whatsoever. Also, even if you are using a 'Button' integration, most people who receive a Registration Access Link via email will follow that link and complete registration in a timely fashion. Unless you have users who have not yet completed registration, there's nothing to worry about.

  However, it's still worth noting that any Registration Access Links that are yet unclaimed via email, will become invalid/expired when you change your s2Member Security Encryption Key. As a workaround, when/if a customer complains, you can generate new links with s2Member. If you're using PayPal Buttons, see: **Dashboard → s2Member → PayPal Buttons → Member Registration Access Links**

- **`s2member_encrypt()`** and **`s2member_decrypt()`**: These are two utility functions that come with the s2Member software. Most site owners running s2Member will never use them, but if you're one of the tech-savvy developers who have, be aware that changing your s2Member Security Encryption Key will prevent you from being able to call `s2member_decrypt()` as expected; i.e., you won't be able to decrypt data that was previously encrypted with the old key.

- **Pro Remote Operations API:** This is an s2Member Pro feature, and the default API Key that is provided by s2Member is based (in part) on your Security Encryption Key in s2Member. Changing your s2Member Security Encryption Key will require you to also change your s2Member Pro Remote Operations API Key. To make this additional change, see: **Dashboard → s2Member → API / Scripting → Pro Remote Operations API**

- **IPN Communication:** This is perhaps the most alarming warning above, but the truth is there is very little for most site owners to worry about. The current release of s2Member uses your Security Encryption Key to exchange data in IPNs (i.e., HTTP-based) sessions that occur within a 1-2 second window of time. The key, at this time, is not used for any long-term storage of IPN data. The warning about long-term use of the key with respect to IPN data is designed to encourage site owners not to change the key unless there is a really good reason for doing so. The Cloudbleed bug is a good reason to change your key. Other than the exception I'll cover next, you can safely change your s2Member Security Encryption Key without causing any long-term repercussions in IPN data exchanges.

  _**Exception:** There is one case when changing your Security Encryption Key will cause a total failure of IPN communication. That's with the optional Proxy Key (for 3rd-party integrations) that s2Member provides for special PayPal integrations. This is a feature that is used rarely by just a few s2Member site owners. To learn more about this optional Proxy Key (for 3rd-party integrations), see:_
  
  _**Dashboard → s2Member → PayPal Options → PayPal IPN Integration**_  
  _and then click the '(optional, for 3rd-party integrations)' link._
  
  _What you need to know is that in this 3rd-party integration URL, you will find `&s2member_paypal_proxy_verification=xxxx...`. This value is based (in part) on your Security Encryption Key in s2Member. If you change your Security Encryption Key in s2Member, and you have used this Proxy Key in a 3rd-party integration, you will also need to update the URL in that 3rd-party integration with the new value; i.e., copy the new URL that is generated by s2Member automatically, once your s2Member Security Encryption Key setting has been updated._
  
---

### What steps should I personally take, even if I have never used CloudFlare?

Aside from WordPress, s2Member, Comet Cache, or anything to do with services you use at CloudFlare, everyone has potentially been affected by Cloudbleed. Following the Cloudbleed event, my friendly suggestion is that _everyone_ using the Internet should change all of their passwords, for everything they use. I would also consider doing that again and again every few months as a precaution; i.e., to reduce the chance you'll be affected by the next Internet super-bug.

---

### Does s2Member.com use CloudFlare? What about CometCache.com?

Yes. We (like so many others) rely upon CloudFlare for vital services. We have been using CloudFlare for some time now, and while Cloudbleed is very concerning, and generally a PITA, we will continue to do so; i.e., We still love CloudFlare, even if they do deserve a nice slap in the face.

_**Note:** CloudFlare has told us that none of our sites were among those officially affected. Still, as a precaution we have taken all the same steps we are suggesting to others, and we have logged everyone out of their accounts following the Cloudbleed event. We are also encouraging all users to reset passwords for all sites and services they use online, and that includes your s2Member.com and/or CometCache.com passwords as well._

#### Do I need to change my s2Member or Comet Cache License Keys?

No, you don't need to update the license keys for any of our software. Just be sure to log into your s2Member.com and/or CometCache.com accounts and update your Profile; i.e., change your password as a security precaution.