---
title: How do I generate an s2Member PayPal Button link?
categories: questions
tags: shortcodes, paypal
author: patdumond
github-issue: https://github.com/websharks/s2member-kb/issues/268
---

With s2Member you can generate PayPal Button shortcodes (see **Dashboard → s2Member → PayPal Buttons**) that will generate a PayPal checkout button wherever you place the shortcode. However, if you are building a pricing table or a landing page a link might just "look better" for your particular application. A link would also allow you to create your own buttons that are styled to fit with your theme.

To generate a PayPal button link, you'll need to start by generating the PayPal Button shortcode as you would if you were using the shortcode itself. You'll need to configure the PayPal button to charge the right amount and provide the proper access.

Once you've generated the PayPal Button shortcode, you can use the `output=` attribute of the shortcode to tell s2Member to output a link instead of a button when the shortcode is processed. Then you can use the generated link in any `<a></a>` anchor element. 

1. Generate the desired shortcode using **Dashboard → s2Member  → PayPal Buttons**.
1. Copy the generated shortcode to a new WordPress page.
1. Change `output="button"` to `output="url"` in the shortcode. 
1. Publish your new page.
1. Copy or note the URL to your newly published page.
1. Log out of WordPress - **this is important**.
1. Navigate to your newly published page. 
1. Copy the entire URL displayed there and use that link wherever you need the PayPal checkout to occur.

That's all there is to it. Short, sweet, and easy with s2Member.
