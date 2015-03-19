---
title: Using the E-Mail address as the Username
categories: tutorials
tags: login-registration,mu-plugins-hacks,email-config
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/10
---

It is possible to modify the s2Member Pro-Form to hide the username field (via CSS) and then use JavaScript to dynamically auto-generate a username in the background when the user types in their email address in the email field. That auto-generated username would be added to the hidden username field so that when the form is submitted, it looks like they entered a username.

_**Note:** WordPress itself does not allow users to register without a username, so generating a hidden username for the user is the best you'll be able to do._

---

An idea about how this might work in code ([original post](http://www.primothemes.com/forums/viewtopic.php?f=4&t=15672&p=49082#p49082); note that the following code has not been tested in a few years):

Create this directory and file:
`/wp-content/mu-plugins/email-to-username.php`

```php
<?php
add_action ("login_head", "s2_customize_login", 1000);
function s2_customize_login ()
    {
?>
        <script type = "text/javascript">
        function getParameterByName(name)
        {
          name = name.replace(/[\[]/, "\\\[").replace(/[\]]/, "\\\]");
          var regexS = "[\\?&]" + name + "=([^&#]*)";
          var regex = new RegExp(regexS);
          var results = regex.exec(window.location.href);
          if(results == null)
            return "";
          else
            return decodeURIComponent(results[1].replace(/\+/g, " "));
        }

            (function ($) /* Wraps this `$ = jQuery` routine. */
                {
                    $.fn.swapWith = function (to) /* Utility extension for jQuery. */
                        {
                            return this.each (function ()
                                {
                                    var $to = $ (to).clone (true), $from = $ (this).clone (true);
                                    $(to).replaceWith ($from), $ (this).replaceWith ($to);
                                });
                        };
                    /**/
                    $(document).ready (function () /* Handles email-to-username on keyup. */
                        {    
                         /* If this is the register page, customize it */
                         if(getParameterByName('action') == 'register'){
    
                                /* Generate random number to append to username, 
                                hopefully making it unique (yes, this isn't perfect!) */
                                var randomNum = Math.ceil(Math.random()*999);

                                var email = 'input#user_email';
                                var login = 'input#user_login';
                                var firstname = 'input#ws-plugin--s2member-custom-reg-field-first-name';
                                var lastname = 'input#ws-plugin--s2member-custom-reg-field-last-name';
    
                                $('p.message').hide();
                                $('div.ws-plugin--s2member-custom-reg-field-divider-section').hide();
                                $('#reg_passmail').hide();
                                $('#nav').hide();
                                $('#wp-submit').val('Subscribe');
                                $(login).closest ('p').hide();
                                
                                $(email).closest ('p').swapWith ($ (firstname).closest ('p'));
                                $(email).closest ('p').swapWith ($ (lastname).closest ('p'));
                                $(firstname).focus();
                                $(email).attr('tabindex', 50);
                                /* Fill hidden username field with first part of email address
                                    and append randomNum to hopefully make it unique. */
                                $ (email).keyup (function ()
                                    {
                                        $(login).val ($.trim ($ (email).val ().split (/@/)[0].replace (/[^\w]/gi, '')) + randomNum.toString());
                                    });                                
                }
                        });
                }) (jQuery);
        </script>
<?php
    }
?>
```

_Note that this code also demonstrates how you can hide additional fields._

---

### Another approach

This code forces the WordPress username to match the email address:

```php
<?php
// Set the username to match the Email
function update_post_vars_for_registration()
{
	if(!empty($_POST['s2member_pro_paypal_registration']))
	{
		$_POST['s2member_pro_paypal_registration']['username'] =
			$_POST['s2member_pro_paypal_registration']['email'];
	}
	elseif(!empty($_POST['s2member_pro_paypal_checkout']))
	{
		$_POST['s2member_pro_paypal_checkout']['username'] =
			$_POST['s2member_pro_paypal_checkout']['email'];
	}
}

add_action('init', 'update_post_vars_for_registration', 1);

// Hide the Username and Display Name fields when displaying the Profile
function hide_username_in_edit_profile($bool)
{
	$bool = FALSE;
	return $bool;
}

add_filter(
	'ws_plugin__s2member_during_profile_during_fields_display_username',
	'hide_username_in_edit_profile');
add_filter(
	'ws_plugin__s2member_during_profile_during_fields_display_display_name',
	'hide_username_in_edit_profile');
```

The downside here would be that if your email address changed, you would't be able to update your username (since usernames cannot be changed once the account is created), so you'd end up with an old email address as the username and a current email address as the email.