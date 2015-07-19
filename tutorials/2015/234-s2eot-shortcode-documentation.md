---
title: '[s2Eot /] Shortcode Documentation'
categories: tutorials
tags: shortcodes, eot-time, s2eot
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/234
---

The `[s2Eot /]` shortcode can be used to display a user's EOT (End of Term) time; i.e., the date when the customer will lose access. Or, if an EOT cannot be determined, an NPT (next payment time) can be displayed. For instance, if the customer has an ongoing recurring plan, there is no fixed EOT time. In this case, it is more appropriate to display the NPT (next payment time).

**Important, see**: [`s2Eot` Limitations (Supported Payment Gateways)](#-limitations)

---

## `[s2Eot /]` Shortcode Examples

### Example 1 (Suggested Usage)

_**Note:** This is really all that's required. It's the easiest way to use `[s2Eot /]`; i.e., just insert the shortcode as-is without needing to specify any additional shortcode attributes. The defaults work just fine for most site owners. This goes into a WordPress Post or Page of your choosing. Your Login Welcome Page is suggested, since that is where members are going to be._

```wpsc
[s2Eot /]
```

**Output examples:**

- If an EOT can be determined: `Access Expires: Jul 16th, 2025, 12:00 am UTC`
- Else, if an NPT (next payment time) can be determined: `Next Payment: Mar 5th, 2022, 12:00 am UTC`
- _Otherwise it displays nothing._

_**Note:** The above examples show the output text only. The output is actually displayed in rich text with HTML markup and CSS class names for easy customization via `style.css` in your WordPress theme of choice. Customizing the CSS is completely optional though; i.e., not necessary._

<pre style="word-wrap:normal;">
<strong class="s2member-sc-eot-label -future">Access Expires:</strong>
<span class="s2member-sc-eot-date -future">Jul 16th, 2025, 12:00 am UTC</span>
</pre>

---

### Example 2 (Specific User ID)

```wpsc
[s2Eot user_id="677" /]
```

**Output examples (for a specific user ID):**

- If an EOT can be determined: `Access Expires: Jan 24th, 2026, 12:00 am UTC`
- Else, if an NPT (next payment time) can be determined: `Next Payment: Apr 2nd, 2023, 12:00 am UTC`
- _Otherwise it displays nothing._

---

### Example 3 (Custom Date Format)

```wpsc
[s2Eot date_format="M jS, Y" /]
```

**Output examples (w/ a [specific date format](http://php.net/manual/en/function.date.php)):**

- If an EOT can be determined: `Access Expires: Jan 24th, 2026`
- Else, if an NPT (next payment time) can be determined: `Next Payment: Apr 2nd, 2023`
- _Otherwise it displays nothing._

_**Note:** Dates are formatted using special characters supported by the PHP `date()` function. See [this article](http://php.net/manual/en/function.date.php) for additional details and examples of each date format char that you can include._

---

### Example 4 (Custom Timezone)

```wpsc
[s2Eot date_format="M jS, Y, g:i a T" timezone="America/New_York" /]
```

**Output examples (w/ a [specific timezone](http://www.php.net/manual/en/timezones.php)):**

- If an EOT can be determined: `Access Expires: Fed 3rd, 2029, 1:06 pm EST`
- Else, if an NPT (next payment time) can be determined: `Next Payment: Apr 2nd, 2018, 5:05 pm EST`
- _Otherwise it displays nothing._

---

## Shortcode Attributes (Explained)

- `user_id="0"` Defaults to a value of `0`; indicating the current user who is logged into the site. If you set this to a WordPress user ID it will display the EOT or NPT (next payment time) for that specific user.

---

- `mode=""` In some cases you might want to request a specific type of EOT; i.e., a fixed EOT (if available), or only the NPT (next payment time). If you don't set a mode, the default behavior is to display a fixed EOT if it can be determined; else display the NPT (next payment time) if it can be determined. Otherwise, nothing is returned.

  **Available Modes (Optional):**

  - `mode=""` Default. Fixed EOT; else NPT (next payment time); else empty format.
  - `mode="fixed"` Only display a fixed EOT (if possible), else display the empty format.
  - `mode="next"` Only display an NPT (next payment time), else display the empty format.

  **Example Use:**

  ```text
  Access Expires: [s2Eot mode="fixed" /]
  Next Payment: [s2Eot mode="next" /]
  ```

  _**Note:** As explained in greater detail below, when you request a specific mode by passing this shortcode attribute, the default output display formats are altered to exclude the prefix and other styling. If you ask for a specific mode, the default behavior is for the shortcode to simply return the date and nothing more. If you need to change this for any reason, you can customize the output format attributes to your liking. However, this is usually not necessary._

---

- `past_format=""` The output display format when a fixed EOT exists and it is a date in the past; i.e., less than the current time. You can use the `%%date%%` replacement code in order to inject the EOT date/time into this output variation if you like. _**Tip:** This attribute supports HTML markup._

  **Default value for `past_format=""` is dynamic:**

  - If `mode="fixed"`, the default output format is simply `past_format="%%date%%"`; i.e., the shortcode assumes that you only want the date whenever you put the shortcode into a specific `mode`.

  - Otherwise, if `mode=""` (default behavior), the default format is:
     <pre style="word-wrap:normal;">past_format="&lt;strong class='s2member-sc-eot-label -past'&gt;Access Expired:&lt;/strong&gt; &lt;span class='s2member-sc-eot-date -past'&gt;%%date%%&lt;/span&gt;"</pre>

---

- `future_format=""` The output display format when a fixed EOT exists and it is a date in the future; i.e., greater than the current time. You can use the `%%date%%` replacement code in order to inject the EOT date/time into this output variation if you like. _**Tip:** This attribute supports HTML markup._

  **Default value for `future_format=""` is dynamic:**

  - If `mode="fixed"`, the default output format is simply `future_format="%%date%%"`; i.e., the shortcode assumes that you only want the date whenever you put the shortcode into a specific `mode`.

  - Otherwise, if `mode=""` (default behavior), the default format is:
     <pre style="word-wrap:normal;">future_format="&lt;strong class='s2member-sc-eot-label -future'&gt;Access Expires:&lt;/strong&gt; &lt;span class='s2member-sc-eot-date -future'>%%date%%&lt;/span&gt;"</pre>

---

- `next_format=""` The output display format when a next payment time is available and in the future; i.e., greater than the current time. You can use the `%%date%%` replacement code in order to inject the next payment date/time into this output variation if you like. _**Tip:** This attribute supports HTML markup._

  **Default value for `next_format=""` is dynamic:**

  - If `mode="next"`, the default output format is simply `next_format="%%date%%"`; i.e., the shortcode assumes that you only want the date whenever you put the shortcode into a specific `mode`.

  - Otherwise, if `mode=""` (default behavior), the default format is:
     <pre style="word-wrap:normal;">next_format="&lt;strong class='s2member-sc-eot-label -next'&gt;Next Payment:&lt;/strong&gt; &lt;span class='s2member-sc-eot-date -next'>%%date%%&lt;/span&gt;"</pre>

---

- `empty_format=""` This output display format is used when the user has no EOT associated with their account, and no next payment time either. Or, when you request a specific `mode=""` and the details for that mode are not applicable or are unavailable.

  **Default value for `empty_format=""` is dynamic:**

  - If `mode="next|fixed"`, the default output format is simply `empty_format="N/A"` to indicate that the value is empty (not applicable). In the case of a partially-supported payment gateway, instead of `N/A`, a value of `—` is used, because time calculations are still a bit fuzzy with partially-supported payment gateways. See [limitations](#-limitations) below for additional details on this.

  - Otherwise, if `mode=""` (default behavior), the default format is nothing; i.e., an empty string and nothing is displayed. In this way, the default behavior is for nothing to be displayed whenever there is no fixed EOT and no NPT (next payment time) either.

---

- `date_format="M jS, Y, g:i a T"` This is the format used to construct the date/time; i.e., the value of the `%%date%%` replacement code that is available for customization in the `past|future|next_format=""` attributes documented above. If you don't set this, it defaults to: `M jS, Y, g:i a T`

  You can customize this if you like. It can be set to a value of `timestamp` for a simple Unix timestamp; i.e., 10 digits that represent the UTC time in seconds. Or, you can set it to a value of `default` to use the default WordPress `get_option('date_format')` that you configured in your WordPress General Settings. Or, you can build a date format based on [these PHP date format chars](http://php.net/manual/en/function.date.php); e.g., `date_format="M jS, Y, g:i a T"`

---

- `timezone="UTC"` This is the timezone used by the date display formatter. See: [this list of all timezone codes](http://www.php.net/manual/en/timezones.php) for further details. If you don't set this shortcode attribute, it defaults to GMT/UTC time; i.e., a value of `timezone="UTC"`.

---

- `round_to=""` In some cases you might like to round the date in a certain way. For instance, if you want to round the date/time to a time relative to the date itself, you could set this to `round_to="tomorrow"`; i.e., the day after the time that is returned. Or, you could set this to `round_to="yesterday"`; i.e., the day before the time that is returned. This shortcode also supports anything that is accepted by PHP's `strtotime()` function. Equivalent to: `strtotime('[round_to]', '%%date%%')`; i.e., relative to the `%%date%%`.

---

- `offset="0"` In some cases you might like to offset the time in a certain way. For instance, if you want to display the EOT or next payment time, plus one extra day to help avoid confusion, this could be set to `86400`; i.e., the number of seconds in one day. This value, if given, should always be provided as a number of seconds. You can use a positive or negative value.

  _**Note:** s2Member already includes what is referred to as an EOT Grace Period, which can be configured in your Dashboard under: **s2Member → [Payment Gateway] Options → EOT Behavior**. When the shortcode returns a fixed EOT time, that time already includes your grace period to help avoid confusion. Thus, any offset that you provide here will be in addition to any configured grace period that is already being applied internally._

---

- `debug="no"` This is for debugging only. If you set this to any boolean-ish true value (e.g., `1|on|yes|true`) then additional details will be displayed to help clarify what is being displayed, or why nothing is being displayed. This should NEVER be used in production.

---

## PHP Equivalent for Developers

```php
<?php
print_r($eot = s2member_eot());
```

```php
/**
* Auto EOT time, else NPT (next payment time).
*
* @param string|int $user_id Defaults to the current user ID.
* @param bool $check_gateway Defaults to a true value. If this is false, it is only possible to return a fixed EOT time.
*   In other words, if this is false and there is no EOT time, empty values will be returned. Be careful with this, because not checking
*   the payment gateway can result in an inaccurate return value. Only set to false if you want to limit the check to a fixed hard-coded EOT time.
* @param string $favor Defaults to a value of `fixed`; i.e., if a fixed EOT time is available, that is returned in favor of a next payment time.
*   You can set this to `next` if you'd like to favor a next payment time (when applicable) instead of returning a fixed EOT time.
*
* @return array An associative array of EOT details; with the following elements.
*
* - `type` One of `fixed` (a fixed EOT time), `next` (next payment time; i.e., ongoing recurring subscription), or an empty string if there is no EOT for the user.
* - `time` The timestamp (UTC time) that represents the EOT (End Of Term); else `0` if there is no EOT time.
* - `tense` One of `past`, `future`, or an empty string if there is no EOT time. If time is now (or earlier) this will be `past`. If time is in the future, this will be `future`.
* - `debug` A string of details that explain to a developer what was returned. For debugging only.
*/
function s2member_eot($user_id = 0, $check_gateway = true, $favor = 'fixed');
```

---

## Limitations (Payment Gateways) {#-limitations}

### Fully Supported Payment Gateways

_If you've integrated with one of these payment gateways you can take full advantage of the `[s2Eot /]` shortcode for both fixed EOT and NPT (next payment time) calculations._

- Stripe _(best support, most accurate)_
- PayPal Pro _(good support, fairly accurate)_
- PayPal Pro Payflow Edition _(good support, fairly accurate)_
- ClickBank _(good support, fairly accurate)_

### Partially-Supported Payment Gateways

- PayPal Standard; i.e., Standard Buttons
- Authorize.Net
- ccBill Buttons
- AliPay Buttons

_**Note:** If you've integrated with Authorize.Net, you will only be able to display fixed EOT times that s2Member records in WordPress; i.e., determining an exact NPT (next payment time) is currently not possible given limitations in the Authorize.Net API for Automated Recurring Billing (ARB) profiles._

#### What does "partially" supported mean exactly?

You can still use the `[s2Eot /]` shortcode with partially-supported payment gateways. However, the `[s2Eot /]` shortcode will only return a fixed EOT time if there is one set by s2Member within WordPress. This is due to limitations in the APIs provided by these payment gateways; i.e., is not possible (at this time) for s2Member to accurately report specific NPTs (next payment times) or calculate recurring intervals later once a subscription has already been created on the payment gateway side.

See also: [When is an EOT Time set for each user?](http://s2member.com/kb-article/when-is-an-eot-time-set-for-each-user/)

In other words, if you're using a partially-supported payment gateway, the `[s2Eot /]` shortcode will only work reliably if you are selling fixed-term access where s2Member sets an EOT time whenever the customer completes checkout. If you sell a "Subscription" of any kind with a partially-supported payment gateway, we suggest that you avoid the use of `[s2Eot /]` altogether to avoid confusion.
