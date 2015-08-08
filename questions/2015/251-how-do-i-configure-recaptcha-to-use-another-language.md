---
title: How do I configure reCAPTCHA to use another language?
categories: questions
tags: captcha-anti-spam-security, pro-forms, login-registration, 
author: raamdev
github-issue:
github-issue: https://github.com/websharks/s2member-kb/issues/251
---

To configure s2Member to use a different language for reCAPTCHA, you'll need to create an [MU-Plugin](http://codex.wordpress.org/Must_Use_Plugins), as described below, that replaces the default `en` language code with one of the [reCAPTCHA language codes](https://developers.google.com/recaptcha/docs/language).

Create this directory and file: `/wp-content/mu-plugins/s2-translations.php`

```php
<?php
add_filter('gettext_with_context', function ($translated, $original, $context, $text_domain)  {

  if($text_domain === 's2member' && $context === 's2member-front recaptcha-lang-code' && $original === 'en')
    $translated = 'es'; // Any code listed here: https://developers.google.com/recaptcha/docs/language?hl=en

  return $translated; // Return final translation.

}, 10, 4);
```