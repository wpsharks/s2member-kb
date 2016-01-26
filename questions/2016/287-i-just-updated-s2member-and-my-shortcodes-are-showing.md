---
title: I Just Updated s2Member and My Shortcodes are Showing!
categories: questions
tags: shortcodes, error-messages, 
author: patdumond
github-issue: https://github.com/websharks/s2member-kb/issues/287
toc-enable: off
---

So, you just updated *s2Member* and now your shortcodes aren't working? They just show up in plain text on your *WordPress* page and, it sure is ugly. Relax. This is a very common problem. Almost always, this happens because you updated *s2Member Framework*, but didn't update *s2Member Pro*. 

The version number of *s2Member Pro* must always match the version number of *s2Member Framework*. If it doesn't, the *Pro Add-On* will not activate. Since *s2Member Pro-Forms* require *s2Member Pro*, when *s2Member Pro* is not activated *Pro-Form* shortcodes will not be processed by *WordPress* and will show up as plain-text.

## The Symptoms

You notice that *s2Member* needs to be updated, so you click the appropriate buttons wherever you are and you're done. Then you go back to whatever you were doing. A few minutes, hours, or even days later you or somebody notices that some or all of your *s2Member* pages with shortcodes on them look strange. Instead of a form or beautifully constructed conditional content you have plain-text shortcodes rendering your page ugly and useless. What happened here?

![my-shortcodes-are-showing](https://cloud.githubusercontent.com/assets/9320495/12522217/5f1ea92c-c11d-11e5-9362-22a99b8e306e.png)

## Troubleshooting

You log in to your **WordPress Dashboard** wondering what happened. You head to the *Plugins* panel and see this helpful message displayed:

![s2member-pro-must-be-updated](https://cloud.githubusercontent.com/assets/9320495/12522224/6aa6f4fc-c11d-11e5-8ad3-4ba32c7bdbb6.png)

Wait, didn't you already update *s2Member*? Yes, and no. Scroll down to the *s2Member* plugin description and you'll see that the version showing for the *s2Member Framework* is the same version that the message at the top of the page wants to update to for the *s2Member Pro Add-on*, but *s2Member Pro* isn't mentioned at all. The *s2Member Framework* is not in sync with the *s2Member Pro Add-on*.

![s2member-framework-160120](https://cloud.githubusercontent.com/assets/9320495/12522235/7920a0b4-c11d-11e5-96e7-06de033902ed.png)

You updated *s2Member Framework*, but the *s2Member Pro Add-on* does not update automatically just because you update the *Framework*. There is still another step to perform. That message at the top of the *Plugins* panel makes it pretty easy. Just put in your *Username* and the key from your *My Account* page at [s2Member.com](https://s2member.com/) and press the **Update s2Member Pro Automatically** button.

## The Next Time You Update s2Member...

Remember, just as when [installing *s2Member*](http://s2member.com/installation/), you must update the *s2Member Framework* and *s2Member Pro* separately. They are two distinct entities and, at least for now, updating the *Framework* does not kick off an automatic update of the *Pro Add-on*. 

**Related Article**: [Why are my Shortcodes Showing Up as Plain Text?](http://s2member.com/kb-article/why-are-my-shortcodes-showing-up-as-plain-text/)
