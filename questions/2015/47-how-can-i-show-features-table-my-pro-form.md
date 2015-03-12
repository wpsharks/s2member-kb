---
title: How can I Show a Features Table on my Pro-Form?
categories: questions
tags: pro-forms
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/47
toc-enable: false
---

**Question:** How can I show a Features Table or Features List on my Pro-Form?

**Answer:** The s2Member Pro-Forms do not support showing a "features table", but you can include a short description when you generate the Pro-Form. That description will appear at the top of the Pro-Form. 

To add this description, you'll see one of the fields is called "Description" when you generate the Pro-Form shortcode in **Dashboard ⥱ s2Member (Pro) ⥱ PayPal Pro-Forms ⥱ PayPal Pro Forms for Level 1 Access**. 

Note that the `desc=""` attribute is limited to 100 chars. Beyond this, s2Member Pro will throw up a warning in your Pro Form as a reminder that you should limit the number of characters used in this attribute. There is a limit because the description is passed through to the payment gateway, and the payment gateways often have limits as to how long it can be.

If you need a longer description, we recommend adding that above the Pro Form shortcode itself, in whatever way is desired; i.e., with HTML or any other sort of rich text.

#### What about a Features Table?

If you are building a features table and want to link your "Sign Up" buttons to a Pro-Form, we recommend creating a separate "Checkout" page where you place your Pro-Form with Multiple Checkout Options (see the related KB Article: [How do I display multiple checkout options?](https://github.com/websharks/s2member-kb/issues/39)). You can then link each "Sign Up" button on your features list to a specific checkout option on the Checkout page.