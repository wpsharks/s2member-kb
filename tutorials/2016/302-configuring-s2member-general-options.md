---
title: Configuring s2Member General Options
categories: tutorials
tags: s2member-users-guide, s2member-profile, s2member-security-badge, s2mop, custom-capabilities, email-config, login-welcome-page, login-registration, member-profile-modifications, membership-levels, membership-options-page, captcha-anti-spam-security, roles-capabilities, security, shortcodes
author: patdumond
github-issue: https://github.com/websharks/s2member-kb/issues/302
---

This Knowledge Base Article covers configuring *General Options* for *s2Member*. These range from simple settings such as *Plugin Deletion Safeguards* or using a *CAPTCHA* to designing your *Membership Levels*, *Login Welcome Page*, and *Membership Options Page*.  

*This article is part of the [s2Member User's Guide](http://s2member.com/kb/kb-tag/s2member-users-guide/), a series of articles that cover the fundamentals of using s2Member.*

## General Options

After you've installed *s2Member* and planned your *s2Member* configuration, including creating at least a skeleton *Login Welcome Page* (LWP) and *Membership Options Page* (MOP), it's time to start the real work of configuring *s2Member*. Go to **WordPress Dashboard → s2Member → General Options**. Here you will set up the *s2Member General Options*.

- Plugin Deletion Safeguards
- Security Encryption Key
- Localhost WAMP/MAMP Developers
- CSS/JS Lazy Loading
- s2Member Security Badge
- Email Configuration
- Open Registration
- Membership Levels/Labels
- Login/Registration Design
- Login Welcome Page
- One-Time-Offers (Upon Login)
- Membership Options Page
- Member Profile Modifications
- URL Shortening Service Preference
- CAPTCHA Anti-Spam Security

## Plugin Deletion Safeguards

By default, *s2Member* will retain all of its *Roles*, *Capabilities*, and *Configuration Options* if you delete the *s2Member* plugin from the **Plugins** panel in *WordPress*. However, if you would like for *s2Member* to erase itself altogether, just choose: **No (upon deletion, erase all data/options)**. See also: [s2Member Uninstall Instructions](http://s2member.com/kb-article/how-do-i-uninstall-s2member).

**Tip**: *It is a good idea to leave this set to* **Yes** *unless you are sure you will no longer be using s2Member on a website.*

## Security Encryption Key

Just like *WordPress*, *s2Member* is open-source software, and that is wonderful. However, this also makes it possible for anyone to grab a copy of the software, and try to learn their way around its security measures. To keep your installation of *s2Member* unique and secure, you should configure a *Security Encryption Key*. *s2Member* will use your *Security Encryption Key* to protect itself against hackers.

It does this by encrypting all sensitive information with your key. The *Security Encryption Key* is unique to **your** installation.

Once you configure this, you do not want to change it -- ever! It is an excellent idea to keep this backed up in a safe place too, in case you need to move your site or re-install *s2Member* in the future.

*s2Member* encrypts Some of the sensitive data it stores with this key. If you change the key, that data can no longer be read even by *s2Member* itself. In other words, don't use *s2Member* for six months and then decide to change your key. That would break your installation.

### How s2Member Uses the Key

The *Security Encryption Key* is used throughout *s2Member's* source code for many different things. However, most (not all, but most) uses of this key are related to transactional processing within a particular session; so changing the key won't impact these scenarios in any significant way. The *Security Encryption Key* is simply there to enhance the security of transmitted data.

That said, there are a few scenarios where the use of the *Security Encryption Key* is long-term, including *Specific Post/Page Access Links* and *Registration Access Links*. It can also have a long-term impact on IPN communication because some data analyzed by *s2Member* includes a checksum that depends on the key. If the key changes, it could cause future IPN data (i.e., data from your payment gateway) to fail validation.

## Localhost WAMP/MAMP Developers

If you're developing your site in a localhost environment, running something like WAMP/MAMP or [EasyPHP](http://www.easyphp.org/), please add this line to your `/wp-config.php` file: `define("LOCALHOST", true);`.

This configuration lets *s2Member* know that your site is in a localhost environment. *s2Member* will adjust itself accordingly, maximizing functionality during your development. *s2Member* can usually auto-detect this, but in cases where your localhost installation runs on something other than `127.0.0.1/localhost`, you must explicitly tell *s2Member* this by adding that line to your `wp-config.php` file. For instance, *s2Member* needs to know when your server IP is the same as all User IPs.

**Note**: *Once your site goes live, please remove this line. If you're already on a live server connected to the web, please ignore this section.*

## CSS/JS Lazy Loading

By default, *s2Member* will load its CSS/JS libraries on every page of your site. However, you may wish to leverage lazy-loading by enabling it here. Select: **Yes (lazy-load CSS/JS libraries (i.e., only load when absolutely necessary)**.

**Tip**: Do you need *s2Member's* CSS/JS on every page? If not, you can enable lazy-loading. If you need *s2Member's* CSS/JS on a given **Post/Page**, you can insert an HTML comment into the **Post/Page** content like this: `<!--s2member-->`. If a **Post/Page** contains the word *s2member* or an `[s2\*` shortcode, this will automatically trigger *s2Member's* lazy-load routine. Thus, it's an easy way to force *s2Member* to load its CSS/JS only on specific **Posts/Pages** where you deem this necessary. There is also a *WordPress* filter available for developers: 

```
add_filter("ws_plugin_s2member_lazy_load_css_js", "__return_true");
```

## s2Member Security Badge

An **s2Member Security Badge** (optional), can be used to express your site's concern for security -- demonstrating to all site visitors that your site and *s2Member* take security seriously.

To qualify your site, you **must** generate a *Security Encryption Key* as described above. *s2Member* will not verify your site if you turn off *Unique IP Restrictions*, *Brute Force Login Protection*, or if your `wp-config.php` file lacks [Security (SALT) Keys](http://codex.wordpress.org/Editing_wp-config.php#Security_Keys) (each at least 60 chars in length). Also, it's not possible for *s2Member* to verify your *Security Badge* if your site is in a localhost environment; i.e., not connected to the web. Finally, you must disable *s2Member* logging (**WordPress Dashboard → s2Member → Log Files (Debug) → Logging Configuration**) and delete any existing files from the `s2member-logs` directory on your server.

Once you've correctly configured all security aspects of *s2Member*, your *s2Member Security Badge* will be verified. To see the *Verified* version of your *Security Badge*, you might need to refresh your browser after saving all changes.

Please see this *s2Member* KB article, [Security Badges](http://s2member.com/kb-article/security-badges) for detailed instructions on qualifying your site for the *s2Member Security Badge*.

### How does s2Member know when my site is secure?

If enabled, an API call for *Security Badge Status* will allow web service connections to determine your status. Clicking this link will report `1 (secure)`,`0 (at risk)`, or `- (API disabled)`. Once all security considerations are satisfied, *s2Member* will report `1 (secure)` for your installation.

**Note**: *This simple API will not, and should not, report any other information*. It will only indicate the current status of your *Security Badge* as determined by your installation of *s2Member*. When you install the *s2Member Security Badge*, *s2Member* will make a connection to your site once per day to test your status.

### Customize WordPress Footer

You can add the **s2Member Security Badge** to your *WordPress* footer by clicking the **Click HERE to insert your Security Badge** link, shown in the screenshot below. You can add any valid XHTML, JavaScript, or PHP code you want to add to your footer in the text box.

![insert-security-badge-rszd](https://cloud.githubusercontent.com/assets/9320495/15054282/904daa08-12d4-11e6-87f3-03845c603620.jpg)

## Email Configuration

You configure the necessary information for the emails sent automatically by *s2Member* here. You need to complete the following fields:

- *Email From Name*: This is the name that appears in the **From** field of the email. We recommend you use the name of your site. 
- *Email From Address*: This is the email address being used to send the email. Use a valid email address as most email providers and local SMTP servers will reject email without a valid **From** address. 
- Email *Support/Contact Link*: This can be either a `mailto:` link with an email address (`support@example.com`) or a web URL (`http://www.example.com/contact`).

### New User Emails

You can further customize the emails sent to new users and the site's administrative contact here. First, select **Yes (customize New User Emails with s2Member)** then customize the email formats using the **click to customize** links shown in the screenshot below.

![click-to-customize-rszd](https://cloud.githubusercontent.com/assets/9320495/15053841/83667312-12d2-11e6-8b49-99e2db42fd11.jpg)

#### New User Email Configuration

##### New User Email Subject
The *Subject Line* used in the email sent to new *Members*.

##### New User Email Message
The primary purpose of this email is to send the user a link to set their password (`%%wp_set_pass_url%%`). You can modify the body of the email using plain-text and *s2Member replacement codes*. Please see **WordPress Dashboard → s2Member®(Pro) → General Options → Email Configuration → New User Email Message (click to customize)** for the list of available *replacement codes*.

**Note**: *This email will* **not** *be sent if you have Custom Passwords enabled.*

##### Administrative: New User Notification
This email is sent to you (or the administrative contact, if not you) each time a new *Member* registers. Customization is the same as the *New User Email Configuration* section above.

![new-user-notification-rszd copy](https://cloud.githubusercontent.com/assets/9320495/15054013/5ffcdd34-12d3-11e6-8e53-397716246e46.jpg)

## Open Registration

*s2Member* supports *Free Subscribers* (at *s2Member Level* **0**/*WordPress Role* **Subscriber**), along with four Primary Levels (1 - 4) of paid Membership. If you want your visitors to be capable of registering for free, you will need to enable *Open Registration* by setting **Allow Open Registration?** to **Yes (allow Open Registration; Free Subscribers at Level #0)**. Whenever a visitor registers without paying, they'll automatically become a *Free Subscriber* at *Level 0*.

**Note**: Site owners can still provide free registration using a *Free Registration Pro-Form*, even with *Open Registration* disabled. The *Open Registration* setting applies only to the default *WordPress Registration Page* (which is the only way to register with *s2Member Framework*, but only one of several ways with *s2Member Pro*).

## Membership/Levels Labels

*s2Member* uses *Membership Levels* to enforce content restrictions. Please customize these to match your site requirements. The default *Membership Levels* have generic labels. Feel free to modify them as desired.

*s2Member* supports *Free Subscribers* (at *Level #0*), along with several Primary Roles for paid Membership (i.e., *Levels 1 - 4*). *s2Member* also supports unlimited *Custom Capability Packages* (see **WordPress Dashboard → s2Member® → API Scripting → Custom Capabilities**). You don't have to use all of the *Membership Levels* if you don't need them. To use only 1 or 2 of these Levels, just design your *Membership Options Page* so it only includes payment options for the levels required.

**TIP**: **Unlimited Membership Levels** *are only possible with* **s2Member Pro**. *However,* **Custom Capabilities** *are available in both the free and Pro versions of* **s2Member**. **Custom Capabilities** *are an excellent way to extend* **s2Member** *in creative ways*.

If you're an advanced Site Owner, a theme designer, or a web developer integrating *s2Member* for a client, please see **WordPress Dashboard →  s2Member® → API Scripting → Custom Capabilities**. We also recommend [this video tutorial](http://www.s2member.com/videos/A2C07377CF60025E).

Also see these *s2Member* KB articles: 
- [s2Member Roles/Capabilities](http://www.s2member.com/kb/roles-caps) 
- [Simple Shortcode Conditionals](http://www.s2member.com/kb/simple-shortcode-conditionals)

### Unlimited Membership Levels (via `wp-config.php`)

With *s2Member Pro* installed, you may configure an unlimited number of *Membership Levels*. You can set the number of *Membership Levels* by adding this line to the top of your `wp-config.php` file: `define("MEMBERSHIP*LEVELS", 4);`. 

Insert this line at the beginning of your `wp-config.php` file, right after the `<?php` tag. Just change the default value of `4` to whatever you need. The minimum allowed value is `1`. The recommended maximum is `100`. If you intend to exceed the recommended maximum, you will also need to add a *WordPress Filter* like this: `add_filter("ws_plugin_s2member_max_levels", function(){ return PHP_INT_MAX; });` to your `functions.php` file.

### Customizing Membership Level Labels

Use the fields on this panel to customize the labels for your *Membership Levels*.

![membership-levels-rszd](https://cloud.githubusercontent.com/assets/9320495/15054028/75709e9e-12d3-11e6-87c2-09a3c68b90fd.jpg)

### Force WordPress to Use Your Labels?

Forcing *WordPress* to use your *s2Member* labels affects only your **WordPress Dashboard** (that is, your list of *Users*). *s2Member* can force *WordPress* to use your *Labels* instead of referencing *Roles* such as *s2Member Level 1*. 

If this is your first installation of *s2Member*, we suggest you set this to **No** until you've had a chance to become familiar with *s2Member's* functionality. In fact, many site owners choose to leave this *Off*, because they find it less confusing when *Roles* are called by their *s2Member* *Level Number*.

### Reset Roles/Capabilities 

The button on the bottom right of this panel is a nifty tool that allows you to reset *s2Member's* internal **Roles and Capabilities** which integrate with *WordPress*. If you, or a developer working with you, has made attempts to alter the default internal **Role/Capability** sets that come with *s2Member* and you need to reset them, please use this tool.

![reset-roles-capabilities](https://cloud.githubusercontent.com/assets/9320495/15054110/ddfa9000-12d3-11e6-9155-3e8fba38db24.jpg)

**Attention Developers**: *It is also possible to lock-in your modified* **Roles and Capabilities** *with an s2Member filter.* Please see this [KB article for details](http://s2member.com/kb-article/locking-s2member-rolescapabilities).

## Login/Registration Design

*s2Member* uses the existing *WordPress* *Login/Registration* system. This is the same *Login/Registration* Form that you use to access your **WordPress Dashboard**. However, with *s2Member* installed, your *Login/Registration Form* can be customized (that is, re-branded). See: **WordPress Dashboard → s2Member → General Options → Login/Registration Design**.

You can make the default *Login/Registration* forms match your *WordPress* theme design. You can change the background color or image, customize the logo, add [Custom Registration Fields](http://s2member.com/kb-article/can-i-create-custom-registration-andor-user-profile-fields-some-required-some-not), and more!

Since *s2Member* uses the default *Login/Registration* system for *WordPress*, *s2Member* is also compatible with themes and other plugins (such as *BuddyPress*). If your theme has a login form built-in already, chances are, it's entirely compatible with *s2Member*. There are also many plugins available that are designed to place login forms into your Sidebar, and many of those are also compatible with *s2Member*. These settings customize your *WordPress Standard Login/Registration Pages*: `http://www.example.com/wp-login.php?action=register`.

To customize the *Login/Registration* page you need to select **Yes (customize Login/Registration with s2Member)** from the drop-down under *Enable This Functionality?*. The remaining fields on this panel are the things you can customize:

- Fonts: Size, Font-Family
- Background: Color, Image, Text Color and Text-Shadow Color
- Logo Image 
- Footer Design: You can customize the footer of the *Login/Registration* form using HTML, PHP, or both.

## Registration/Profile Fields & Options

You can use this panel to add *Custom Registration/Profile Fields* for your Members. Some fields are already built-in. They are *Username*, *Email*, *First Name*, and *Last Name*.

*Custom Registration/Profile Fields* will appear in your *Registration Form*, and in *User Profiles*.

**Regarding Registration**: *Custom Registration/Profile Fields* do not appear during repeat registration/checkout attempts (that is, they won't be shown to any user currently logged into the site). *Please make sure that you test registration and checkout forms while not logged in (in other words, test as a first-time customer).* Existing *Members* may update *Custom Registration/Profile Fields* by editing their *Profile*.

You create new *Custom Registration/Profile Fields* by clicking *Add New Field* underneath *Custom Registration/Profile Fields*. 

Clicking *Add New Field* will bring up a pop-up window used to create your *Custom Registration/Profile Field*. 

![add-new-field](https://cloud.githubusercontent.com/assets/9320495/15054180/23520e3a-12d4-11e6-8ef2-b851ad1322c3.jpg)

For each *Custom Registration/Profile Field* you can configure the following options:

- **Starts a New Section**: Should this field start a new section on the registration form?
- **Form Field type**: Select from a drop-down menu of available field types. 
- **Field Label/Desc**: What label should appear before the field data-entry box? 
- **Unique Field ID**: This is the *slug* for the field. For example, *country*code* or *street*address*. 
- **Field Required**: Does the user **have** to fill in this field to submit the form or is it optional? 
- **Default Text Value (optional)**: If there is a value that most of your users will enter in a field it is a good idea to provide that as a default. Otherwise, leave this blank. 
- **Expected Format**: Select from a variety of common data formats or select *Anything Goes* for a free-form field. 
- **Applicable Membership Levels**: Is this field only used for certain s2Member Membership Levels? If so, enter them here in a comma-delimited list of numeric values. Otherwise, leave the default of *all*. 
- **Allow Profile Edits**: Should the user be allowed to edit this field from the *User Profile*? 
- **CSS Classes**: If you want to assign custom CSS classes to this field, enter them here. Otherwise, leave this blank. 
- **CSS Styling**: If you want to assign custom CSS styling to this field, enter it here. Otherwise, leave this blank. 
- **Other Attributes**: If you'd like to add other attributes, such as `onkeyup=""` or `onblur=""` to this field, enter them here. Otherwise, leave this blank.

### Other Registration Settings

#### Collect First/Last Names During Registration?

If you are selling memberships, you'll want to leave this enabled, because *s2Member Pro Forms* always require a first and last name. If you only have free members, this is optional.

#### Set "Display Name" During Registration?

You can choose from several options for setting the Member's *Display Name* at registration.

#### Allow Custom Passwords During Registration?

Custom Passwords are easier for users. However, this has an impact on site security. Enabling *Custom Passwords* disables the *New User Notification* email that sends a password setup link for each user. In other words, allowing *Custom Passwords* effectively disables any email verification procedure for registration.

#### Minimum Length/Strength for Custom Passwords

You can choose a minimum number of characters and complexity requirements for user-selected passwords.

**Tip**: *Minimum length and password strength also impact profile updates, so it's a good idea to configure these even if you're not using* **Custom Passwords** *during registration*.

### Force Personal Emails During Registration?

You can enter commonly-used "catch-all" email prefixes (for example: *admin*, *webmaster*) here to encourage users to enter a personal email address.

See [this article](http://s2member.com/r/mailchimp-role-based-emails) for a comprehensive list of such emails to ban.

### Integrate Custom Registration/Profile Fields with BuddyPress?

If you are using *BuddyPress*, you can choose to combine *s2Members Custom Registration Fields* with the *BuddyPress Public Profiles*, *Registration Form*, and the *BuddyPress Profile Editing Panel*.

## Login Welcome Page

If you have not already done so, please create a new **WordPress Page** or choose an existing **WordPress Page** to use as your *Login Welcome Page* (LWP) This will be the first page *Members* will see after logging in. 

**Always Private**: The LWP will always require a logged-in *Member*. In fact, this Page will be protected from public access by *s2Member* automatically. 

**Note**: *For technical reasons, your LWP cannot be your* **Front Page** *(also known as your* **Home Page**) *or your* **Posts Page** (*that is, your main* **Blog Page**). Please create a dedicated **Page** in *WordPress* and then designate it as your *Login Welcome Page*.

See also: This KB article: [Customizing Your Login Welcome Page](http://www.s2member.com/kb/customizing-your-lwp).

![login-welcome-page-rszd](https://cloud.githubusercontent.com/assets/9320495/15054204/41b0328a-12d4-11e6-896b-692230bd2efc.jpg)

1. Select the LWP you created from the drop-down list below **Login Welcome Page:**. 
2. Alternatively, you can set an alternate URL as the first page members see after logging in by typing the URL in the text box below **Or, a Special Redirection URL?**.               
3. If your site uses SSL/HTTPS, you need to decide whether you want your members redirected using HTTP or HTTPS. Select the appropriate option below **Always Redirect non-Administrative Users (after login) using HTTP?** 

**Tip**: Having an entire site protected by SSL/HTTPS is becoming more common and is expected by many users. If you enforce  SSL/HTTPS for your entire site, you should select **No, do NOT modify (use WordPress default behavior; i.e., detect URL scheme automatically)**.

## One-Time-Offers (Upon Login)

**Note**: *One-Time-Offers* are an *s2Member Pro* feature.

This optional setting allows you to override your default *Login Welcome Page* based on the number of times a User/Member has logged in previously. s2Member gives you the ability to write a custom configuration file for these *One Time Offers*. This configuration file will then display pages you have created when the User/Member logs in for your designated number of times. You can specify designated logins by *s2Member User Level* as well, allowing you to customize your *Onboarding Experience*.

### One-Time-Offer Configuration File

Enter the name of your *One-Time-Offer Configuration File* in the text box in the **WordPress Dashboard → s2Member® → General Options → One-Time-Offers (Upon Login)**. This file contains a line-delimited list of URLs named in the special format below.

#### Special Format for One-Time-Offer URLs

```
[Logins]:[Access Level]:[One-Time-Offer URL]
```

- `[Logins]` is an integer designating the number of logins that trigger the offer. The offer is triggered **on** the login with the value entered here (this triggers your One-Time-Offer page upon x number of logins). That is, a `1` will trigger the offer on the *first* login, and a `10` will trigger the offer on the *tenth*. 

- `[Access Level]` This **optional** value triggers your One-Time-Offer, based on *s2Member User Level* as well as the designated [Logins] value. 
- `[One-Time-Offer URL]` This is the full URL to the page you want the User/Member to see upon the designated login.

##### Example Configuration File

```
1:http://example.com/your-first-login/  
25:http://example.com/customer-loyalty-reward/  
3:1:http://example.com/upgrade-to-level-2/ (displayed on 3rd login, to Level #1 Members only)  
1:0:http://example.com/upgrade-to-level-1/  
```

- Line 1 will be displayed on the first login to all User/Members. 
- Line 2  will be displayed on the twenty-fifth login to all User/Members. 
- Line 3 will be displayed on the first login to *Level 1* User/Members only. 
- Line 4 will be displayed on the first login to *Free Subscribers* (s2Member User Level 0) only.

##### Replacement Codes

Advanced site owners can use *Replacement Codes* in their One-Time-Offer URLs. See **WordPress Dashboard → s2Member (Pro) → One-Time-Offers (Upon Login)** and click the *Replacement Codes* link to see a list of all of the *Replacement Codes* available for one-time-offers while working in your *WordPress Dashboard*.

- `%%current_user_nicename%%` = The current User's `nicename` in lowercase format. The `nicename` is a cleaner version of the `username` for use in URLs.
- `%%current_user_id%%` = The current User's `id`.
- `%%current_user_level%%` = The current User's *s2Member Level*.
- `%%current_user_role%%` = The current User's *WordPress Role*.
- `%%current_user_ccaps%%` = The current User's *s2Member Custom Capabilities*.
- `%%current_user_login%%` = Number of times the current User has logged in.

## Membership Options Page 

The *Membership Options Page* (MOP) is a unique *WordPress* **Page** you create where you will either place the *s2Member Button* or *Pro-Form* shortcodes you generate or place links to separate pages for selling multiple Membership options.

Your MOP should detail all of the features that come with Membership to your site. The MOP is the Page that anyone who tries to access content protected above their level will be redirected to by *s2Member*. Think of it as a *Landing Page* for non-Members.

**Note**: This Page must be public at all times. In fact, *s2Member* will not allow this Page to be restricted in any way.For technical reasons, your MOP cannot be set to your *Front Page* (that is, your *Home Page*); or your *Posts Page* (that is, your main *Blog* Page). Please create a separate (dedicated) Page in WordPress, and then designate it as your MOP here: **WordPress Dashboard → s2Member (Pro) → General Options → Membership Options Page**

1. Select the (MOP) you created from the drop-down list below **Membership Options Page:**. 
2. Select whether to enable *MOP Variables* from the drop-down list below **Enable MOP Vars (i.e., Membership Options Page Variables)**. For more information on these options see, **WordPress Dashboard → s2Member → API / Scripting → Membership Options Page / Variables**.

## Member Profile Modifications

*s2Member* is configured by default to redirect Members away from the default *Profile Editor* (**WordPress Dashboard → Users → Your Profile**) built into *WordPress*. When a Member attempts to access the default *Profile Editor*, they'll instead be redirected to the *Login Welcome Page* that you've configured with s2Member.

### Why would I redirect away from the default Profile Editor?

Unless you've made some drastic modifications to your *WordPress* installation, the default **Profile Editor** that comes with *WordPress* is not secured for any public access.

So instead of using it, *s2Member* provides you (the Site Owner) with a special shortcode: `[s2Member-Profile /]`. You can insert this into your *Login Welcome Page*, or any Post or Page for that matter (even into a Text Widget). This shortcode produces an *Inline Profile Editing Form* that supports all aspects of *s2Member*, including Password changes and any *Custom Registration/Profile Fields* that you've configured with *s2Member*. Alternatively, you can send your Members to a special Stand-Alone version. The stand-alone version makes it possible for you to open it up in a popup window, or embed it into your *Login Welcome Page* using an IFRAME.

### `[s2Member-Profile /]` Shortcode

`[s2Member-Profile /]` This shortcode displays the *Inline Profile Modification Form* in a WordPress Page, Post, or Text Widget.

See this s2Member KBA for more details: [[[s2Member-Profile /]] Shortcode](https://s2member.com/kb-article/s2member-profile-shortcode/).

### Stand-Alone Profile Editor (Pop-up Window)

To display the *Stand-Alone Profile Editor* in a popup window use this HTML code: 

```
<a href="#" onclick="window.open('http://pat.websharks-inc.net/?s2member_profile=1', '_popup', 'width=600,height=400,left=100,screenX=100,top=100,screenY=100,location=0,menubar=0,toolbar=0,status=0,scrollbars=1,resizable=1'); return false;">Modify Profile</a>
```

## URL Shortening Service Preference

In a few exceptional cases, long URLs generated by *s2Member* (that is, those containing encrypted authentication details) will be shortened. URLs are shortened automatically, using one of the URL Shortening APIs. A shortened URL prevents issues with very long links becoming corrupted by a User's email application. 

For instance, the *Signup Confirmation Email* that *s2Member* sends out to a new, paying Member may contain a link that is shortened to prevent corruption by email applications. By default, *s2Member* uses the *tinyURL* API. *tinyURL* has proven itself to be the most reliable. 

However, in cases where an API service call fails, *s2Member* will automatically use one or more of its other APIs as a backup. This option setting allows you to configure which URL Shortening API *s2Member* should try first (that is, the one you prefer). Select your preferred provider from the drop-down list. If your preferred provider requires an access token or API Key, enter it into the text box below the drop-down.

## CAPTCHA Anti-Spam Security

Please note. *s2Member* does not introduce a CAPTCHA (i.e., a challenge-response) into any core feature for *WordPress*. We've excluded this functionality on purpose because many site owners prefer to use a more comprehensive CAPTCHA plugin that encompasses all aspects of their site.

*s2Member Pro-Forms* for *Stripe*, *PayPal Pro* and *Authorize.Net* (including *Free Registration Forms)* can be configured to use *Google's reCAPTCHA™* service (free). Just add this attribute to your *Pro-Form* Shortcode: `captcha="light"`. Or, use `captcha="dark"`, for a dark-themed *reCAPTCHA™* box instead.

You'll need to create a [free set of keys](https://www.google.com/recaptcha/admin#list) for your website to use *reCAPTCHA™*. Enter the keys into the appropriate text boxes on this *s2Member* panel.
