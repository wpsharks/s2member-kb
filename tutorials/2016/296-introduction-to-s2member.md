---
title: Introduction to s2Member
categories: tutorials
tags: s2member-users-guide, pro-forms, shortcodes
author: patdumond
github-issue: https://github.com/websharks/s2member-kb/issues/296
---

In this introductory article, you’ll be introduced to s2Member’s core concepts, uses for s2Member, and some of s2Member’s shortcodes. 

*This article is part of the [s2Member User's Guide](http://s2member.com/kb/kb-tag/s2member-users-guide/), a series of articles that cover the fundamentals of using s2Member.*

## Exactly What IS s2Member?

_s2Member_ is a powerful _WordPress_ plugin, actually **two** of them (the free _s2Member Framework_ and the _Pro Add-on_), for turning your website into a private online club or community. It does this by both providing free and paid registration capabilities and restricting your content. _s2Member_ builds upon _WordPress's_ existing user database, authentication, login, and registration system, and the _WordPress_ concept of _[User Roles and Capabilities](https://www.google.com/url?q=https://codex.wordpress.org/Roles_and_Capabilities&sa=D&ust=1459969031030000&usg=AFQjCNGgCWiz32Dp4sS7bis6KgaDUI1rag)_. It then uses those _User Roles and Capabilities_ to protect your content: displaying it to only the audience you have chosen for each Post, Page, or File Download on your site.

All registered _Members_ of your website are _WordPress_ **Users** with an assigned _s2Member Role_. In the free _[s2Member Framework](https://s2member.com/register/?s2-ssl=yes)_, you can have Members with levels 1 - 4 (plus Level 0 _Free Subscribers_ if you want them). In _[s2Member Pro](https://s2member.com/checkout/?type%3Dsingle%26s2-ssl%3Dyes&sa=D&ust=1459969031032000&usg=AFQjCNGUQH1QrcEi7p4_tKpOskO6F7QvMw)_, you can have as many Membership levels as you need.

In addition to _s2Member User Levels_ you can sell and protect content using what we call _Custom Capabilities_. _Custom Capabilities_ are available in both the _s2Member Framework_ and _s2Member Pro_. You can even sell access to content without requiring user registration at all, with _Buy Now_ buttons (_s2Member Framework_ and _s2Member Pro_) and [_Pro-Forms_](http://s2member.com/kb-article/s2member-pro-forms/) (_s2Member Pro_ **only**) which provide time-limited access to specific Posts and Pages.

## How Have Others Used s2Member?

_s2Member_ is arguably the most flexible Membership plugin available for _WordPress_. You can use _s2Member_ to build sites based completely on free registrations while still taking advantage of _s2Member User Levels_. You can have **no** free registrations at all and require payment from all Members: using one level or many. Or you can combine free and paid registrations for maximum flexibility between making your content available to the public and restricting the _best_ content to paid Members only.

Another way of providing options for your Members is in the length of time each membership lasts. You decide how long each subscription lasts. You also decide whether that particular subscription type is a one-time sale or a _recurring subscription_. Both one-time sales and recurring subscriptions can have a set subscription period or be a _lifetime_ membership that never expires. As long as your Members keep paying their recurring subscription, they never need to fill out another subscription form. _s2Member_ and your payment gateway handle renewals silently on the back-end.

You can also use _s2Member_ to protect access to downloadable files and even streaming video. _s2Member_ can even protect content hosted by Content Data Networks (CDN) like _[Amazon CloudFront](https://aws.amazon.com/cloudfront/&sa=D&ust=1459969031038000&usg=AFQjCNGNEejPuYM-qPc8lRqcLQWtmhx_vQ)_ or _MaxCDN_. _s2Member_ can limit the number of downloads per user during a given time period.

## How Does s2Member Use Shortcodes?

_s2Member_ makes it easy to create a powerful custom membership site by using shortcodes. Sales forms are created by generating shortcodes for either _Buttons_ (available with both _s2Member Framework_ and _s2Member Pro_) or _Pro-Forms_ (only available with _s2Member Pro_). You simply fill out a form listing all of the options available, click a button, and you have a shortcode you can copy and paste into a _WordPress_ Page (or Post, if you prefer). Instant sales (and registration) forms!

_s2Member_ also features many other shortcodes for further customizing your membership site. These include:

[[[s2Member-List /]]](http://s2member.com/kb-article/s2member-list-shortcode-documentation/) for displaying a highly customizable list of your site's Members. **NOTE: This shortcode requires _s2Member Pro_**.

[[[s2If][/s2If]]](http://s2member.com/kb-article/s2if-simple-shortcode-conditionals/) for protecting parts of Posts and Pages.

[[[s2Member-Summary /]]](http://s2member.com/kb-article/s2member-summary-shortcode-documentation/) for displaying a summarized profile for the currently logged-in user on any Post or Page. This shortcode can even display a login box if the current user is not logged in when they access the Post or Page. **NOTE: This shortcode requires **_s2Member Pro_**.

[[[s2Member-Login /]]](http://s2member.com/kb-article/s2member-login-shortcode-documentation/) will display a login box on any Post or Page. It will optionally display a summarized profile for the current user if they are already logged in when accessing the Page. **NOTE: This shortcode requires **_s2Member Pro_**.

[[[s2Eot /]]](http://s2member.com/kb-article/s2eot-shortcode-documentation) can be used to display a user's subscription _End of Term_ (EOT).

[[[s2Get /]]](http://s2member.com/kb-article/s2get-shortcode-documentation) is a shortcode version of the _s2Member API_ function get_user_field() which can be used in customizing PHP template files.

[[[s2MOP /]]](http://s2member.com/kb-article/s2mop-shortcode) can be used to enhance your _Membership Options Page_ (MOP). The MOP is the Page you designate in _s2Member_ to display your membership options. This is the Page where Members and Visitors will be redirected if they try to access parts of your site that are restricted above their access level. **NOTE: This shortcode requires _s2Member Pro_**.

[[[s2Drip /]]](http://s2member.com/kb-article/s2drip-shortcode) allows you to drip website content to your Members. Content dripping is the gradual, pre-scheduled release of premium content to paying Members. **NOTE: This shortcode requires _s2Member Pro_**.

[[[s2Stream /]]](http://s2member.com/kb-article/s2stream-shortcode-documentation) makes it easy to set up protected streaming video links on your membership site.

## What If I Want to Customize s2Member with Code?

If you know a little, or a lot, about programming with PHP you can really get creative with your s2Member customizations. You'll need a plugin such as [ezPHP for WordPress](http://s2member.com/kb-article/ezphp-for-wordpress) to use PHP in Posts, Pages, or Text Widgets. You can also use PHP and HTML to create custom templates for buttons, forms, and shortcodes like `[s2Member-List /]`. You can also dig into the _s2Member API_ for custom tracking, mailing list server integration, notifications, and complex scripting.
