---
title: How do I send an email when the membership level is changed?
categories: questions
tags: mu-plugins-hacks,roles-capabilities,email-config
author: kristineds
github-issue: https://github.com/websharks/s2member-kb/issues/263
toc-enable: off
---

With s2Member, you can set up your site such that when a user registers, they must be manually approved before they can login and access their membership account. A common scenario would be if your users prefer to send payment through cash or check instead of one of the supported payment gateways (*Paypal, Stripe, Authorize.Net, ClickBank*) options. Manually approving user roles is discussed in [this article](http://s2member.com/kb-article/how-can-i-manually-approve-user-accounts/).

If you want to automatically send an email to your members when their user role has been changed by an Administrator from the WordPress Dashboard, i.e. an upgrade/downgrade of their membership level, this is possible but it requires a small bit of custom code. 

**NOTE**: This article does not apply to the Billing Modification Form which sends its own email when the user modifies their own account using a Billing Modification Form. See: **WordPress Dashboard → s2Member → [Payment Gateway] Options → Modification Confirmation Email (Standard/Pro Form)**.

By default, s2Member doesn't send any emails when a User Role is changed by an Administrator from the WordPress Dashboard. However, you can send an email when this happens by creating an [MU-Plugin](http://codex.wordpress.org/Must_Use_Plugins) and sending an email using the [`wp_mail()` function](https://codex.wordpress.org/Function_Reference/wp_mail). WordPress sends email using `wp_mail()` similar to [PHP’s `mail()`](http://php.net/manual/en/function.mail.php). It is a way for your site to send user an email message via PHP script.

_NOTE: If you are not familiar with MU (Must Use) Plugins or customizing s2Member with Hooks and Filters, read [this article](http://s2member.com/kb-article/hacking-s2member-plugin-w-hooksfilters-for-wordpress/)._

Create this directory and file: `/wp-content/mu-plugins/s2-role-change-handler.php`

```php
<?php
add_action('init', 's2_role_change_event_handler::init', 1);

class s2_role_change_event_handler
{
    public static $user_id;
    public static $user_old_role;

    public static function init()
    {
        global $pagenow;

        if (!is_admin()) {
            return; // Not applicable.
        }
        if ($pagenow !== 'user-edit.php') {
            return; // Not applicable.
        }
        if (empty($_REQUEST['user_id'])) {
            return; // Not applicable.
        }
        if (!current_user_can('edit_users')) {
            return; // Not applicable.
        }
        $user = new WP_User((int) $_REQUEST['user_id']);

        static::$user_id       = $user->ID;
        static::$user_old_role = reset($user->roles);

        add_action('set_user_role', 's2_role_change_event_handler::event', 10, 2);
    }

    public static function event($user_id, $new_role)
    {
        if ($user_id === static::$user_id && $new_role !== static::$user_old_role) {
            if (($user = new WP_User($user_id)) && $user->exists()) {
                // Replace $subject, $message, $headers with your information
                $subject = 'User Role Update';
                $message = 'Hello '.$user->first_name.'!'."\r\n"."\r\n".'This is to notify you that your User Role has been changed to "'.$new_role.'".';
                $headers = 'From: Awesome Site <hello@awesomesite.com>'; 
                wp_mail($user->user_email, $subject, $message, $headers);
            }
        }
    }
}
```

For more details on WP User Class, see [Class Reference/WP User](https://codex.wordpress.org/Class_Reference/WP_User)

#### See also:
- [Can I customize emails that s2Member sends?](http://s2member.com/kb-article/can-i-customize-emails-that-s2member-sends/)
- [How can I manually approve user accounts?](http://s2member.com/kb-article/how-can-i-manually-approve-user-accounts/)
- [How do I offer a free upgrade](http://s2member.com/kb-article/how-do-i-offer-a-free-upgrade/)
