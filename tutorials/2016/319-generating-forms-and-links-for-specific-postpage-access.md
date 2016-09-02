---
title: Generating Forms and Links for Specific Post/Page Access
categories: tutorials
tags: pro-forms, restriction-options
author: patdumond
github-issue: https://github.com/websharks/s2member-kb/issues/319
---

This article introduces Pro-Forms and Links for selling **Specific Post/Page Access**. **Specific Post/Page Access** is a very advanced feature of *s2Member Pro* and requires the *s2Member Pro Add-On*. 

For a thorough explanation of how this feature works in s2Member, please see [Understanding Specific Post/Page Access Restrictions](http://s2member.com/kb-article/understanding-specific-postpage-access-restrictions/).

*This article is part of the [s2Member User's Guide](http://s2member.com/kb/kb-tag/s2member-users-guide/&sa=D&ust=1470238793494000&usg=AFQjCNG1q04lm4O1PV4kb07x1Gin-dmEew), a series of articles that cover the fundamentals of using s2Member*.

## Generating Forms and Links for Specific Post/Page Access  

See **WordPress Dashboard → s2Member (Pro) → PayPal Pro-Forms → Specific Post/Page (Buy Now) Forms**

![specific-ppa-forms](https://cloud.githubusercontent.com/assets/9320495/17524041/d852d58e-5e2a-11e6-8475-0958bca2bb7d.jpg)

[Specific Post/Page Access](http://s2member.com/kb-article/understanding-specific-postpage-access-restrictions/) is a very powerful feature of s2Member Pro that allows you to sell access to specific WordPress Posts and Pages. Specific Post/Page Access works independently of *Membership Level Access*. You can sell access to an unlimited number of WordPress Posts and Pages using **Buy Now** functionality (no recurring billing but access is allowed for a particular term). Your Customers do not need a Membership Account with your site to receive access to these Posts and Pages. If they are already a Member, that is fine, but they do not need to be.

In other words, Customers do not need to login to access the Specific Post/Page they purchased. s2Member redirects the Customer to the Specific Post/Page after the Customer successfully checks out. s2Member also sends an email notification to the Customer with a link (see **WordPress Dashboard → s2Member (Pro) → PayPal Options → Specific Post/Page Confirmation Email (Pro-Form)**). Authentication is handled automatically through self-expiring links.

Specific Post/Page Access is like selling a product. Except instead of shipping anything to the Customer, you just give them access to specific WordPress Posts or Pages on your site. These Posts and Pages might contain a download link for your eBook, access to file & music downloads, access to additional support services, or whatever else you can think of to put on a WordPress Post or Page. The possibilities with this are endless, as long as you can deliver your digital product through access to a WordPress Post or Page.

Before you can generate Specific Post/Page Access Pro-Forms, you must configure access restriction rules for Specific Posts/Pages (see **WordPress Dashboard → s2Member (Pro) → Restriction Options → Specific Post/Page Access**). If you need more information on creating the access restrictions see [Configuring s2Member Restriction Options](http://s2member.com/kb-article/configuring-s2member-restriction-options/). Once you have configured restriction rules, you can generate your Form shortcodes here **WordPress Dashboard → s2Member (Pro) → PayPal Pro-Forms → Specific Post/Page (Buy Now) Forms**.

### Specific Post/Page (Buy Now) Form Fields

- The first drop-down box contains a list of Posts and Pages that you have restricted using Specific Post/Page Access Restrictions. If you do not see any Posts or Pages listed here, remember that before you can generate Specific Post/Page Access Pro-Forms, you must configure access restriction rules for Specific Posts/Pages (see **WordPress Dashboard → s2Member (Pro) → Restriction Options → Specific Post/Page Access**). From this first box, you will select the page you want your Customers to be redirected to (and receive a link to via email) after a successful purchase. 
- The second dropdown box also contains a list of Posts and Pages that you have restricted using Specific Post/Page Access Restrictions. From this second box, you will select any additional Posts and Pages you want to package with the Post or Page selected from the first box. 

**Note**: *Make sure the page selected first has links to at least one of the pages selected from the second drop-down box*. You can arrange the links in whatever fashion you like, just make sure your Customer receives links to all of the Posts and Pages in your package. In other words, you can have links to all of the Posts and Pages on the first Post or Page or you can link them in a chain. 

- **I want to charge**: Type the price you want to charge one time and the period you want to allow access to the package. 

**Note**: The text describing the time periods uses words like “days”, “months”, and “years”, but s2Member converts the period sold to **hours** for the shortcode. 

- **Description**: Modify the *Description* text to describe the **Specific Post/Page Access** you are selling as clearly as possible.
- **Check out Page Style**:
    -  This is optional. You can configure [PayPal Custom Payments Page Styles](https://www.paypal.com/customize) from within your PayPal Merchant Account. If you create custom page styles, enter the name of the desired style here.
    - Select the currency you want from the drop-down box.

Once you have filled in all the form fields, click the **Generate Form Code** button and then copy the generated shortcode to a Post or Page you create in WordPress.

## Specific Post/Page Access Links

See **WordPress Dashboard → s2Member (Pro) → PayPal Pro-Forms → Specific Post/Page (Buy Now) Links**

s2Member automatically generates Specific Post/Page Access Links for your Customers after checkout and also sends them a link in a Confirmation Email. However, if you ever need to deal with a Customer Service issue that requires a new Specific Post/Page Access Link you can use this shortcode Generator to create Specific Post/Page Access Links to send your Customer.

![specific-post-page-access-links](https://cloud.githubusercontent.com/assets/9320495/18016410/38d4e588-6b9a-11e6-9d76-74e76ab6bc24.png)

#### Specific Post/Page Access Links Form Fields

See above **Specific Post/Page (Buy Now) Form Fields** for an explanation of the first two drop-down boxes.

- From the third drop-down box select the period after which the Customer’s access expires.

Once you have filled in all the form fields, click the **Generate Access Link** button and then send the Access Link to your Customer via email.
