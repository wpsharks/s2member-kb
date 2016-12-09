---
title: Translating s2Member & s2Member Pro
categories: tutorials
tags: translation
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/228
---

s2Member and s2Member Pro are equipped with support for front-end translation, using WordPress standards; i.e., we've implemented the use of `_x()`, and various other translation routines for many aspects of s2Member's front-end interfaces.

For instance: Profile panels, Login/Registration Fields, and Pro-Form integrations; as well as error messages displayed to Users/Members. _Translation support for back-end admin panels provided by s2Member will come in a future release, along with more extensive translation support for front-end aspects._

Like WordPress itself, we chose to use the GNU `gettext` localization framework to provide localization infrastructure for s2Member. GNU `gettext` is a mature, widely used framework for modular translation of software, and is the *de facto* standard for localization in the open source/free software realm. See also: [WordPress In Your Langauge](https://make.wordpress.org/polyglots/teams/)

## Building a Translation `.mo` File

If you'd like to translate s2Member and/or s2Member Pro, please use [the POT file](https://github.com/websharks/s2member/blob/dev/master/includes/translations) found inside `/s2member/src/includes/translations/s2member.pot`, which contains all translation entries for **both** the s2Member Framework *(i.e., the free version)*, and also for s2Member Pro.

_**Quick Tip:** If this is your first translation of a WordPress plugin, [this article](http://urbangiraffe.com/articles/translating-wordpress-themes-and-plugins/) might be of some assistance._

_**Quick Tip:** If you don't use the POT file that comes with s2Member, and instead, you decide to use something like [Codestyling Localization](http://www.code-styling.de/english/development/wordpress-plugin-codestyling-localization-en) to generate your own, please make sure that you configure the scanner to search both the `/s2member` and `/s2member-pro` directories. Since the `/s2member-pro` add-on is not an official plugin (it's actually an add-on), this might require a symlink, or that you contact the team behind the software you're running for some assistance in this matter._

When you are finished translating the `s2member.pot` file, place your completed `s2member-[locale].mo` file into this directory: `/wp-content/plugins/`; and please feel free to [share your translation](https://wordpress.org/support/plugin/s2member) with the rest of the s2Member community.

_**Quick Tip:** If you only need to translate the front-end of s2Member, please ignore entries in the `s2member.pot` file with a context matching `s2member-admin`. Those sections of s2Member are only seen by site Administrators; they are NOT used in s2Member's front-end integration with WordPress. Skipping over translation entries with a context matching `s2member-admin` can save you time._

## Loading Your `.mo` Translation File

Let's assume that your locale is: `fr_FR`

- You should create: `/wp-content/plugins/s2member-fr_FR.mo`
- All you need now is to define the locale for WordPress.

  Please open your `/wp-config.php` file and add the following line:

  ```php
   <?php
   define('WPLANG', 'fr_FR');
  ```
  _See also: [Additional considerations](https://codex.wordpress.org/Installing_WordPress_in_Your_Language)_

## Existing Translations (Updating Your `.po` File)?

**FUZZY translation entries:** If you're updating an existing `.po` file (e.g., recompiling your `.mo` file after changes in a new release of s2Member) please be sure to manually review any "fuzzy" entries. A fuzzy entry can occur as a result of changes from one release of s2Member to the next. Small changes in text might render your translation invalid (i.e., fuzzy).

Depending on your `.po` file editor, fuzzy entries may need to be reviewed and changes committed _before_ you recompile; otherwise fuzzy entries will revert to their default state in your final `.mo` file. Translations that are fuzzy, are _not_ compiled into your final `.mo` file. This can lead to much confusion. Please review any fuzzy entries carefully.
