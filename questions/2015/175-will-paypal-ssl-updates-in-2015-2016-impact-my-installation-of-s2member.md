---
title: Will PayPal SSL updates in 2015-2016 impact my installation of s2Member?
categories: questions
tags: paypal, troubleshooting
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/175
toc-enable: false
---

In the early part of 2015, PayPal sent a notice to merchants informing them they might have to take action. PayPal plans to upgrade various SSL certificates on their side. PayPal explained that over the course of 2015 and 2016, they would be taking steps towards strengthening their SSL certificates across all of their sites.

## PayPal writes...

> The changes include upgrading the signing algorithm and version of the root certificate we support. This effort will allow PayPal to further protect our valued customers from current and future security threats.

## Does This Impact s2Member or s2Member Pro?

No, not really. These changes are occurring on PayPal side of things. s2Member and s2Member Pro both communicate with PayPal through the [`WP_Http`](https://codex.wordpress.org/HTTP_API) class. This is a part of the WordPress core, and it is designed to support SSL communication.

However, **you should check your webserver** for compatibility with the new SHA-256 certificate technology. This will be required by most web services in 2015.

We suggest that you contact your hosting company to inquire about compatibility with remote HTTPS communication through the `WP_Http` class, and ask them to be sure their servers will support the new SHA-256 certificate technology. There are high odds that your server will not need to be updated, but it is a great idea to check on this ahead of time, just in case!

---

## Full Email Sent By PayPal

> Because we support our merchants in helping them grow their business, we continue to make significant investments and improvements to our infrastructure. These improvements sometimes require us to perform necessary service upgrades.

> Please read below as we explain what the change is, and what action may be required by you.*

> What’s happening?

> Over the course of 2015 and 2016, PayPal will be working towards upgrading various SSL certificates. The changes include upgrading the following:

> The version of the VeriSign Trusted Root Certificate used to establish secure connections to PayPal.

> The signing algorithm of certificates (from SHA-1 to SHA-256).

> Why is this happening?

> We’re taking measures to address industry-wide security concerns which aren’t unique to PayPal. When implemented, these measures can help us improve the security and reliability of our PayPal integrations and help guard against current and future security threats.

> When is this happening?

> We’ve published the schedule of our service upgrade plan. Please check our 2015-2016 SSL Certificate Change microsite for the most recent updates as published schedules may change. Our efforts to upgrade SSL certificates for our production endpoints are scheduled to start in May 2015, and will continue into next year.

> Please note – The Sandbox environment is ready for testing. Testing in the Sandbox environment is one of the best ways to make sure your integration works.

> What do I need to do?

> For information regarding the important details of these upgrades, how it may impact your integration, and what you must do to future-proof your integration, please refer to the Merchant Security System Upgrade Guide on the microsite.

> *Please note – If you’re impacted by this upgrade, you may be required to implement these changes prior to the dates listed on the microsite. Otherwise, you may not be able to process payments through your current integration with PayPal. In addition, if you’re integrated with a third party, please check with them on any additional steps you may need to take.

> Questions can be directed to our Merchant Technical Services team on our Technical Support website. Click here for more information.

> Thanks for your patience as we continue to improve our services.

> Was this email helpful? Please click here to let us know how we're doing at keeping you informed.