---
title: How can I style Pro Forms w/ custom CSS?
categories: questions
tags: pro-forms, mu-plugins-hacks
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/6
---

Each s2Member Pro Form includes built-in CSS class names that allow you to apply styles across all Pro-Form variations at once (e.g., checkout, registration, cancellation, billing modifications, specific post/page access, etc). Or, you can use class names that are specific to certain types of Pro-Forms, or even specific to certain sections within a Pro-Form.

The easiest way to find these class names and to customize your Pro-Forms with custom CSS that takes advantage of them; is to open a page containing a Pro-Form in a browser that supports a Web Developer Console (e.g., Chrome, Firefox). The Developer Console makes it easy for you to fiddle with custom CSS and see immediate results. See: https://developer.chrome.com/devtools/docs/elements-styles

When you have things just the way you like, take the modifications that you've made and add those to the `style.css` in your WordPress theme of choice. See: `/wp-content/themes/[YOUR THEME]/style.css`

**See also:** [Customizing Pro-Forms](http://s2member.com/kb-article/s2member-pro-forms/#-customizing-pro-forms)
