---
title: How do I enter a Pro Form Coupon Code?
categories: questions
tags: pro-forms, pro-coupon-codes
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/36
toc-enable: false
---

> I changed my Pro Form Shortcode to include `accept_coupons="1"` on the form, I also get the fact that you will need to place the coupon discount in coupon code configuration, such as `SAVE-10|10%` ... what I am struggling with is where to input the code!

---

### Expected Coupon Code Input Field in a Pro Form

![](https://cloud.githubusercontent.com/assets/1563559/5762149/a08029ce-9c8c-11e4-97d0-3d6a8077644b.png)

---

### Troubleshooting the Coupon Code Field

If you are not seeing the Coupon Code field in your Pro Form, here are some possible reasons

<div class="li-margins"></div>

- When you set `accept_coupons="1"`, does that conflict with another attribute with the same name? Most Pro Form shortcodes already include `accept_coupons="0"`. So what you should do is change the existing shortcode attribute to `accept_coupons="1"` to enable Coupon Codes. Adding a new attribute (now two attributes with the same name) could create a conflict within the WordPress shortcode parser. It's a good idea to double-check this.
- When you visit your site in Google Chrome and you open the Developer Console (**Google Chrome → View → Tools → Developer → JavaScript Console**) do you find that there are any JavaScript errors produced by another theme/plugin that you are running? If so, this can result in broken s2Member Pro-Forms that do not display the Coupon Code field. Work to resolve the JavaScript errors in other plugins and that will allow all of the JavaScript provided by s2Member to function properly. You should then see the Coupon Code field display as expected.
- If you've configured any of your Coupon Codes in a such a way that they are only valid on specific Posts/Pages (as seen in the screenshot below), please be sure that you are in fact on that specific Post/Page within WordPress when running your tests.

  ![](https://cloud.githubusercontent.com/assets/1563559/5762284/84e584e2-9c8d-11e4-9f6c-f1fa610b45ce.png)
