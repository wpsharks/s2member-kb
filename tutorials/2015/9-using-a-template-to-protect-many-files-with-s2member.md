---
title: Using a Template to Protect many Files with s2Member
categories: tutorials
tags: download-options, mu-plugins-hacks, s2file, shortcodes
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/9
---

### Advanced Download Restrictions

There are MANY options when it comes to serving files protected by s2Member. Among these, there is an option that we consider the most flexible. It's the `[s2File /]` shortcode coupled with the `download_key="true"` attribute. This is what we refer to as "Advanced (or Flexible) Download Restrictions".

If a file is protected by s2Member (in whatever way, it doesn't matter) you can always make this file available to certain users through the `[s2File /]` shortcode as follows:

```text
[s2File download="example.zip" download_key="true" /]
```

This shortcode produces a link which contains an auto-generated (and encrypted) key that allows the file to be downloaded for up to 24 hours by a specific browser and IP address; i.e. the current user's browser and IP address.

It does not matter what other restrictions you've imposed, the use of a Download Key (explained further in your Dashboard, see: `s2Member ⥱ Download Options ⥱ Advanced Download Restrictions`), allows a user to access the file because you have explicitly told s2Member that it's OK for this to occur, by using the `download_key="true"` attribute to begin with.

_NOTE: the link produced contains a download key that is good for up to 24  hours, for a single user operating from a specific browser and IP address. However, the 24 hour period is reset on each page load; i.e. the link is reproduced each time. Therefore, you should be cautious (or at least consider this) whenever you present a page which contains such a shortcode. The link being reproduced each time is not a security issue at all, but if your intention is to restrict the amount of time the file will be available, it's important to realize how this works; that's all :-)_

### Integrating Download Keys into a WordPress Template

Many site owners (particularly WP developers) have used s2Member to sell themes/plugins of their own, or to sell a large array of files they make available within a library that customers gain access to. This usually incorporates s2Member's File Download functionality, since files are downloadable items for sale; i.e. a key part of the business model.

With s2Member, there are many ways to sell access to particular pages, either in the form of a subscription or as separate Custom Capability purchases that provide access to specific areas. Such a discussion is outside the scope of this article.

Instead, I'm going to focus on how to incorporate Download Keys into a WP template file, making the process of delivering many downloadable files easier, no matter how the customer gains access; i.e. whether it be through a CCAP purchase, or through Specific Post/Page Access, or via Member Level 1, etc. You should be able to adapt the contents of this article to any of these scenarios.

#### Example Use Case

In this example, let's assume that I'm selling Custom Capabilities (CCAPS) with s2Member. I won't deal with Membership Levels. Instead, I will design my site in a way where CCAPs are always required for access to files. Again, just an example scenario.

So, in this example, in order to access a particular file, I will make it so my customers will need to have a Custom Capability (CCAP) that I associate with each file; e.g. the file's name or an ID number; whatever make sense.

Now, let's pretend that I have files: `a.zip`, `b.zip` and `c.zip`. Each of these are separate purchases. `a.zip` requires `access_s2member_ccap_a`. `b.zip` requires `access_s2member_ccap_b`. You get the picture.

With this in mind, I can now open my favorite editor and add a snippet to one of my WordPress templates. It might look something like this:

```php
<?php
$file_id = 'a'; // Acquire current file ID; from wherever you store file IDs.
?>

<?php if(current_user_can('access_s2member_ccap_'.$file_id)): ?>
    <a href="<?php echo do_shortcode('[s2File download="'.$file_id.'.zip" download_key="true" /]'); ?>">click here to download</a>
<?php endif; ?>
```

Incorporating this snippet would make it easy for me to build a system where I store IDs associated with each file, and sell CCAPs that provide access to each file. Then, I can serve those files to users who have the required CCAP, using s2Member's Advanced Download Restrictions. And, I can do this with a template file that will make it all very easy for me to maintain.

Documentation for all of the shortcodes and other details discussed in this article can be found in the s2Member Dashboard under: `s2Member ⥱ Download Options`.