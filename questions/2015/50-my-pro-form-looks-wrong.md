---
title: My Pro Form looks nothing like examples I've seen, why?
categories: questions
tags: pro-forms, troubleshooting
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/50
---

If you find that your Pro Form is presenting fields that seem out of place, or if you find that the overall style in Pro Forms is not a match to the [screenshot below](#-functional-example); here are some things to start looking at.

## Suggested Steps to Resolve

<div class="li-margins"></div>

- Do you have any JavaScript errors on the page where the Pro Form resides? Inspecting the page where your Pro Form loads up, using the Google JavaScript Developer Console, or in Firebug for Firefox should help you resolve this. If you have another theme/plugin that is causing a JavaScript error, this could prevent other functionality on the page (e.g. s2Member Pro Forms) from working as expected. We see this quite often, so checking in a Developer Console is highly recommended.

  ![2015-01-20_13-35-45](https://cloud.githubusercontent.com/assets/1563559/5828279/abe23ed0-a0ae-11e4-9b91-7e33270864c1.png){.aligncenter}
- Verify that s2Member's JavaScript/CSS libraries are actually loading up. You can inspect the HTML source code and also look for successful network connections to the following resources depicted in this screenshot. If either of these are missing (or fail to load properly), you should check your `s2Member ⥱ General Options` and look under `CSS/JS Lazy Loading`. Set the option to "No", always load.

  ![2015-01-20_14-17-44](https://cloud.githubusercontent.com/assets/1563559/5828315/32367942-a0af-11e4-9d2c-3ebb03c170e4.png){.aligncenter}

  ![2015-01-20_14-20-11](https://cloud.githubusercontent.com/assets/1563559/5828350/7e285f50-a0af-11e4-9dc5-5273b64ce586.png){.aligncenter}
- Test your Pro Forms in a [clean WordPress installation](https://github.com/websharks/s2member-kb/issues/81) (e.g., a default theme such as Twenty Fiftteen, Twenty Fourteen, and with only the s2Member plugin active). This will rule out a possible conflict with other plugins and/or a custom theme's CSS file. If you find that s2Member's default structural styles (i.e., the CSS that it comes with by default) is not enough to override styles presented by your theme, or it conflicts with your theme; then you may need to seek assistance from a developer to help resolve these conflicts.

---

## A Functional Pro Form Example {#-functional-example}

![2015-01-20_14-09-50](https://cloud.githubusercontent.com/assets/1563559/5828219/11725ee8-a0ae-11e4-9e0a-ed0c165b36b7.png){.aligncenter}
