---
title: Why am I seeing the Pro-Form Billing Address section when I'm only accepting PayPal?
categories: questions
tags: pro-forms, tax-rate-calculations
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/76
---

**Question:** Why am I seeing the Pro-Form Billing Address section when I'm only accepting PayPal? I have my Pro-Form shortcode attribute configured with `accept="paypal"` and I don't need to collect a Billing Address; how do I get rid of that section?

**Answer:** If you have your Pro-Form shortcode configured to accept only PayPal (`accept="paypal"`) and you're still seeing the Billing Address section appear on your Pro-Form, you've most likely configured a Tax Rate in your s2Member configuration (see `s2Member ⥱ PayPal Options ⥱ Tax Rate Calculations (Pro Form)`).

When you are collecting taxes from your customers, s2Member Pro-Forms will _always_ ask for a Billing Address. This is because s2Member can be configured to apply different Tax Rates by country, state/province, or zip code range.