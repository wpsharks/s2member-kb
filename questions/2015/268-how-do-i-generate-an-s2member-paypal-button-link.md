---
title: How do I generate an s2Member PayPal Button link?
categories: questions
tags: shortcodes, paypal
author: patdumond
github-issue: https://github.com/websharks/s2member-kb/issues/268
---

You can use a link instead of a button for PayPal using the `output=` attribute of s2Member's PayPal button shortcode. You can use the generated link in any `<a></a>` anchor element. You might want to do this if you are building a pricing table or a landing page. A link might just "look better" in your particular application.

1. Generate the desired shortcode using **WordPress Dashboard →s2Member®(Pro) → PayPal Buttons**.
1. Copy the generated shortcode to a new WordPress page.
1. Change `output="button"` to `output="url"` in the shortcode. 
1. Publish your new page.
1. Copy or note the URL to your newly published page.
1. Log out of WordPress - **this is important**.
1. Navigate to your newly published page. 
1. Copy the entire URL displayed there and use it to create your link.

That's all there is to it. Short, sweet, and easy with s2Member.