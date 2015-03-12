---
title: How do I sell products using the Stripe Bitcoin integration?
categories: questions
tags: 
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/112
---

**Question:** How do I sell products using the Stripe Bitcoin integration?

**Answer:** To sell products using the Stripe Bitcoin integration, you first need to [enable the live Bitcoin API on your Stripe account](http://www.s2member.com/r/stripe-bitcoin-enable/). Once you've done that, you can start accepting Bitcoin on your site using s2Member's Pro-Forms.

If you always want Bitcoin to be an option when checking out with Stripe, you can enable it globally from `s2Member ⥱ Stripe Options ⥱ Stipe Account Details → Accept Bitcoin via Stripe?`. Otherwise, you can enable it on an individual Pro-Form-basis by adding the `accept="bitcoin"` attribute to the shortcode.

Note that Stripe Bitcoin currently only supports Buy Now (i.e., non-recurring) transactions. In the example below, we'll be using a Specific Post/Page (Buy Now) Pro-Form to sell access to a specific WordPress Post/Page.

---

1. We'll start by generating a Specific Post/Page (Buy Now) Pro-Form shortcode in `s2Member ⥱ Stripe Pro-Forms ⥱ Stripe Specific Post/Page (Buy Now) Forms`. Let's create one to sell 3 days of access to a page for $0.50:

     ![2015-02-23_23-26-06](https://cloud.githubusercontent.com/assets/53005/6343281/f1a5ed52-bbb3-11e4-8e32-8604c6305a9f.png)

1. Now copy the generated Pro-Form shortcode to a Post or Page. This will be your "checkout" page. If you don't have Stripe Bitcoin enabled globally in `s2Member ⥱ Stripe Options ⥱ Stipe Account Details → Accept Bitcoin via Stripe?`, you'll want to add `accept="bitcoin"` to the shortcode as shown below:

     ```
[s2Member-Pro-Stripe-Form accept="bitcoin" sp="1" ids="193" exp="72" desc="3 Days Access to Restricted Page" cc="USD" custom="raam.websharks-inc.net" ra="0.50" coupon="" accept_coupons="0" default_country_code="US" captcha="0" /]
     ```

1. Now when a visitor visits that page, they can fill in their details and then click "Add Billing Method":

     ![2015-02-23_23-22-54](https://cloud.githubusercontent.com/assets/53005/6343313/77aafb4a-bbb4-11e4-8a52-7a00c2dab53a.png)

1. They will then be presented with a Stripe dialog that allows them to select the "Bitcoin" payment option. This generates a Bitcoin address where the buyer can send the USD equivalent in Bitcoins to make their payment. If they have a mobile device, they can click the "Scan" button to view the QR code and use that to easily send Bitcoin via their mobile device.

     ![2015-02-23_22-58-29](https://cloud.githubusercontent.com/assets/53005/6343335/d554b600-bbb4-11e4-9c18-7cad74a59b64.png)

1. It can take anywhere between 5-10 minutes for Stripe to confirm receipt of the Bitcoin once it has been sent. Once the Bitcoin has been sent, the buyer can hover their mouse over the circle icon to the right of the payment amount to view how many minutes are remaining before Stripe confirms the payment.

1. Once Stripe confirms receipt of the Bitcoins, the dialog will close and the Bitcoin address where the Bitcoins were sent is shown below the "Add Billing Method" box; this confirms Stripe has received Bitcoin payment and the buyer can now click "Submit Form" to complete the checkout:

     ![2015-02-23_23-02-00](https://cloud.githubusercontent.com/assets/53005/6343363/631d3f34-bbb5-11e4-8420-cef959e52d26.png)

1. If this is a Stripe Specific Post/Page (Buy Now) form, access to the restricted page will be provided immediately on the following screen, where the buyer will see a "click here to proceed" message. They will also be sent an email with a copy of the link to access the restricted page for the length of time purchased.

     ![2015-02-23_23-03-29](https://cloud.githubusercontent.com/assets/53005/6343378/a539d594-bbb5-11e4-9112-f60982f8b6a9.png)