---
title: What metadata does s2Member pass to Stripe?
categories: questions
tags: stripe
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/266
---

## Metadata Passed by s2Member Pro

[Stripe Metadata](https://stripe.com/docs/api#metadata) is available for advanced site owners and 3rd-party services that interact with the Stripe API. The metadata that s2Member pushes over to Stripe is listed below. This information is useful when/if you build applications or integrate with services that might need to access additional details related to coupon codes, tax info, or geo-location. Metadata is almost always accessed through scripts that communicate with the Stripe API. See [official docs here](https://stripe.com/docs/api#metadata).

**See also:** Dev Notes below.

### The Stripe **Customer** object receives:

```json
metadata: {
  "name": "John Doe",
  "ip": "xxx.xxx.xxx.xxx"
}
```

### The Stripe **Source** object receives:

```json
metadata: {
  "name": "John Doe",
  "ip": "xxx.xxx.xxx.xxx",
  "address_city: "Los Angeles",
  "address_state: "CA",
  "address_zip": "90001",
  "address_country": "US"
}
```

### The Stripe **Charge** object receives:

```json
metadata: {
  "coupon": [JSON-encoded object; e.g., {"code":"SAVE10"}],
  "tax_info": [JSON-encoded object; e.g., {"tax":"3.45","tax_per":"8.5"}]
}
```

### The Stripe **Subscription** object receives:

```json
metadata: {
  "coupon": [JSON-encoded object; e.g., {"code":"SAVE10"}],
  "trial_tax_info": [JSON-encoded object; e.g., {"tax":"3.45","tax_per":"8.5"}],
  "tax_info": [JSON-encoded object; e.g., {"tax":"3.45","tax_per":"8.5"}]
}
```

_**Note:** The `trial_tax_info` property contains any tax applicable to a first initial payment that forms an initial/trial period. The `tax_info` property represents the regular recurring rate after the initial/trial period is over and regular charges apply._

---

## Dev Notes

In the examples above, values represented by `[JSON-encoded object...]` indicate that a string value is stored in Stripe _as_ a JSON-encoded string that you can decode. For instance, in PHP you would `json_decode($metadata->tax_info)` to gain access to the object properties for the tax information.

The `coupon`, `trial_tax_info`, and `tax_info` properties are only passed to Stripe if they apply; i.e., if the customer used a coupon configured with s2Member. In the case of tax, only if the site owner is charging tax and tax applied to the purchase that a customer made.
