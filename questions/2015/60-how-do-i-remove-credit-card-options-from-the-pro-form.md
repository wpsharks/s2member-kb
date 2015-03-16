---
title: How do I remove Credit Card options from the Pro-Form?
categories: questions
tags: pro-forms
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/60
---

Inside your s2Member PayPal Pro-Form shortcode, you will see a shortcode attribute that looks like this: `accept="paypal,visa,mastercard,amex,discover,maestro,solo"`

If you only want to accept PayPal, simply change that to `accept="paypal"`.

If you only want to accept PayPal, VISA, and MasterCard (if you're using PayPal Pro, for example), then you can change that attribute to `accept="paypal,visa,mastercard"`