---
title: Generating Member Registration Access Links
categories: tutorials
tags: pro-forms, paypal
author: patdumond
github-issue: https://github.com/websharks/s2member-kb/issues/320
---

In this article, we introduce the shortcode generator for creating replacement registration access links. s2Member sends these links to your Customers after they pay for a Membership subscription on your site. If they need the link re-issued, you can create it in this Dashboard panel. You may never need this tool, but it is available to help you with customer service issues. 

*This article is part of the [s2Member User's Guide](http://s2member.com/kb/kb-tag/s2member-users-guide/&sa=D&ust=1470238793494000&usg=AFQjCNG1q04lm4O1PV4kb07x1Gin-dmEew), a series of articles that cover the fundamentals of using s2Member.*

See **WordPress Dashboard → s2Member (Pro) → PayPal Pro-Forms → Member Registration Access Links**

![s2Member - Member Registration Access Links](https://cloud.githubusercontent.com/assets/53005/18335989/ae1f2b58-7551-11e6-81a6-27955f5ec5e1.png)

s2Member Pro-Forms consolidate the Registration and Checkout process into a single-step solution. However, you can use this shortcode generator to create a replacement *Registration Access Link* for customer service. A Customer might be distracted and close their browser before completing the Registration Form after returning to your website from the payment gateway. Alternatively, you might sell a Membership offline and need to send your new Member a link to complete Registration instead of creating a User account manually (see **WordPress Dashboard → Users → Add New**).

## Member Registration Access Link Form Fields

- **Paid Membership Level**: Select the appropriate Membership Level from the drop-down box. 
- **Paid Subscr. ID**: Enter the Paid Subscriber ID from your payment gateway. This field is crucial, without this ID s2Member cannot link the User Account on your WordPress site with a Recurring Subscription at the payment gateway. 
- **Custom String Value**: In most cases, the default value entered here works fine. This Custom String Value must **always** start with your domain name. You can also add pipe-delimited ( | ) custom values after your domain if needed.
- **Custom Capabilities**: This is optional. Type in a comma-delimited list of Custom Capabilities (CCAP) you would like included with this Membership. You can use CCAPs to set custom content restrictions for your website.
- **Fixed Term Length (for Buy Now transactions)**: If the Customer purchased Membership through a one time (Buy Now) transaction, you should enter a Fixed Term length in this field. This information ensures that s2Member can revoke the Member’s Membership Level Access at the appropriate time. This data is numeric value followed by a space and then a single letter representing the period. 

    - `D – Day` (For example, `30 D` for 30 days)
    - `W – Week` (For example, `2 W` for 2 weeks)
    - `M – Month` (For example, `6 M` for 6 months)
    - `Y – Year`  (For example, `1 Y` for 1 year)
    - `L - Lifetime` (For example, `1 L` for a Lifetime Subscription)

Once you have filled in all the form fields, click the **Generate Access Link** button and then send the Access Link to your new Member via email.