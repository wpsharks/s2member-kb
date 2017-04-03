---
title: Plugins that work well with s2Member
categories: tutorials
tags: other-integrations, tricks
author: KTS915
github-issue: https://github.com/websharks/s2member-kb/issues/280
---

s2Member has been designed to make optimum use of core WordPress functions. It does not add its own tables to your site’s database, but instead uses the regular WordPress tables.

This means that s2Member’s functionality can easily be extended by using other plugins, even if they have not been designed specifically with s2Member in mind. Below is a list of plugins that integrate particularly well with s2Member, organized according to the function that they provide.

Please note that this list is *not* exhaustive. It simply lists those plugins that we have either used ourselves or that have been reported by s2Member users as integrating well with s2Member.

## Sites Specializing in s2Member Plugins

- [s2Plugins.com](https://s2plugins.com/) ~ not affiliated with s2Member or WebSharks, Inc., but they do provide several add-ons for products that we've created. Plugins built by this developer are clean and professional. Support is available by the author. See: [s2plugins.com](https://s2plugins.com/)

## Admin Bar

- [Admin Bar Disabler](https://wordpress.org/plugins/admin-bar-disabler/): This plugin allows you to show or hide the admin bar to users with specific user roles (including s2Member levels).

## Caching

- [ZenCache](https://wordpress.org/plugins/zencache/)
- [ZenCache Pro](https://zencache.com/) (paid plugin)

_**Tip:** We are the developers of ZenCache and ZenCache Pro, so these can always be guaranteed to work with s2Member. ZenCache Pro offers the significant advantage that it makes it possible to cache content for logged-in members. It also offers the ability to compress (minify) CSS and javascript files, which will make your site go even faster._

Other alternatives...

- [WP Super Cache](https://wordpress.org/plugins/wp-super-cache/)
- [W3 Total Cache](https://wordpress.org/plugins/w3-total-cache/) (provided that object caching is **not** enabled please).

## Capability Management

- [Capability Manager Enhanced](https://wordpress.org/plugins/capability-manager-enhanced/)
- [Members](https://wordpress.org/plugins/members/)

Both of these plugins allow you to have much finer-grained control over which capabilities are assigned to each user role (including s2Member levels). This enables you, for example, to allow those with s2Member Level 1 to have access to content that would otherwise be restricted to those at s2Member Level 4 and above.

Perhaps more importantly, these plugins also enable you to change the default hierarchical structure of s2Member levels. You could therefore use either of them to prevent users at s2Member Level 2 and s2Member Level 3 from being able to access content designated for those at s2Member Level 1.

## Changing Text Created by s2Member

- [Say What?](https://wordpress.org/plugins/say-what/)

s2Member and s2Member Pro provide a variety of forms and buttons for use on your site. You might, however, prefer to use different words or phrases (whether in English or another language) instead of the default s2Member text. This plugin (which, when activated, will appear in your Tools menu under Text Changes) allows you to do so easily by simply filling in four boxes for each phrase you wish to change.

Those boxes are as follows:
  
1.  Original string: type in the current text
1.  Text Domain: type `s2member`
1.  Text Context: type `s2member-front`
1.  Replacement String: type in your desired text

## Comment Subscriptions

- [Comment Mail](https://wordpress.org/plugins/comment-mail/)
- [Comment Mail Pro](http://comment-mail.com/) (paid plugin)

_**Tip:** We are the developers of both these plugins. They allow commenters to sign up for email notifications whenever they leave a comment on your site. Or, they can also subscribe without commenting — the choice is theirs. This is a fantastic way to engage visitors — giving them the details they want, when (and how) they want them!_

## Counting Hits on Posts and Pages

- [Post Views Counter](https://wordpress.org/plugins/post-views-counter/)

This plugin provides a means of displaying how many times a post or page has been viewed. There are options for displaying in the admin pages and/or on the front end, and it is possible to exclude visits by those with specific roles (including s2Member roles) from being counted.

## Groups Management

- [KC Groups Management](http://krumch.com/2013/07/09/kc-groups-management/#.Vklev3q350w) (paid plugin)

This enables one user to purchase a bundle of s2Member memberships that s/he can then control. This is very useful if, for example, you have a corporate client who wishes to enable access for a number of employees.

## Identifying Post and Page IDs

- [Reveal IDs](https://wordpress.org/plugins/reveal-ids-for-wp-admin-25/)
- [WP Show Ids](https://wordpress.org/plugins/wp-show-ids/)

Sometimes, when using s2Member, you might wish to protect a specific post or page and need to obtain its ID. Both these plugins add the ID number of each post and page to the lists of posts and pages in the WordPress admin pages.

## Login and Registration

- [Clean Login](https://wordpress.org/plugins/clean-login/): This provides a means of creating new login, lost password, and registration pages using regular WordPress pages. It also provides a setting to disable the admin bar for every user except administrators. Just make sure that the option to “Disable dashboard access for non-admin users?” is left unchecked, so that that can be managed by s2Member instead.
- [Sidebar Login](https://wordpress.org/plugins/sidebar-login/): As its name suggests, provides a means of adding a login widget to any sidebar.

_**Note:** s2Member Pro also provides its own widget that can be placed in any sidebar so as to enable a member to login on any post or page where that widget appears._

## MailChimp Integration

- [KC S2M+MC](https://wordpress.org/plugins/kc-s2mmc/): s2Member already enables basic integration capabilities with MailChimp. This plugin takes that integration much deeper, so that users can be added either from s2Member or from MailChimp, and they will be synced across to the other application.

## Menus

- [Nav Menu Roles](https://wordpress.org/plugins/nav-menu-roles/)
- [Privilege Menu](https://wordpress.org/plugins/privilege-menu/)

If you enable all Alternative View Protections in s2Member (or check the Nav Menus box option) then s2Member will ensure that menu items will reflect the user role of the current user. In other words, someone at s2Member Level 1 will see on the menu only those items that are accessible to someone with that user level.

These two plugins offer more fine-grained control. You might, for example, wish someone with s2Member Level 1 access to be able to see a menu item that is accessible only for someone at s2Member Level 2 so that this can act as a teaser, encouraging them to purchase an upgrade.

## PHP in Posts and Pages

- [ezPHP](https://wordpress.org/plugins/ezphp/): There are other plugins that also offer the capability to add PHP code to posts and pages. However, we are the developers of the ezPHP plugin, and recommend it because, besides the regular PHP syntax, it provides an alternative way of inserting PHP that uses shortcodes. This makes it possible to use on the visual editor of a post or page, as well as on the text editor.

## Protected Downloads Management and Tracking 

- [s2Member Secure File Browser](https://wordpress.org/plugins/s2member-secure-file-browser/): This plugin provides fine-grained control of your protected file downloads (including downloads served inline). It also enables you to track how many times a file has been downloaded, and by whom.

## Spam Prevention

- [Ban Hammer](https://wordpress.org/plugins/ban-hammer/): So long as you are using the default WordPress registration form, Ban Hammer provides a way of preventing registrations from users with email domains that you can specify.
- [Anti-Spam by CleanTalk](https://wordpress.org/plugins/cleantalk-spam-protect/)
- [WP-SpamShield Anti-Spam](https://wordpress.org/plugins/wp-spamshield/)

_The other two plugins provide more general spam protection on login and registration forms, including forms generated by s2Member and s2Member Pro._

## User Data: Listing, Searching, and Sorting

- [AMR Users](https://wordpress.org/plugins/amr-users/)
- [AMR Users Plus s2Member](https://wpusersplugin.com/downloads/amr-users-plus-s2-member/) (paid plugin)

s2Member Pro already provides an [`[s2Member-List /]`](https://s2member.com/kb-article/s2member-list-shortcode-documentation/) shortcode that makes it possible for site owners to build a list of their members in a variety of ways. The shortcode might be used to present a list of your highest ranking members, or simply to provide other members with a way to search for each other.

_**If, however**, you have some other use case that this shortcode does not cater for, these two plugins provide other ways to build lists of your members._

## Widgets

- [Display Widgets](https://wordpress.org/plugins/display-widgets/): This plugin adds a series of options to each active widget that enable you to control not only the posts, pages, categories, etc. on which the widget appears, but also which user roles (including s2Member user roles) will be able to see it.
