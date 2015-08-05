---
title: Using Download Restrictions with NGINX
categories: tutorials
tags: nginx, basic-download-restrictions, s2stream, s2file, server-config-files, download-options
author: raamdev
github-issue:
github-issue: https://github.com/websharks/s2member-kb/issues/250
---

The s2Member Download Restrictions will work with NGINX, as the access control relies almost entirely on PHP and not the web server. However, there are a few things to keep in mind if you're using NGINX with s2Member Download Restrictions.

## Preventing Access to `/s2member-files/`

All files that you want to protect with s2Member must reside in `wp-content/plugins/s2member-files/`. s2Member adds an `.htaccess` file to that directory to prevent public access. However, NGINX does not support .htaccess files. This means that you will need to update your NGINX server configuration to prevent public access to files in that directory.

What follows is an example of what you might add to your NGINX configuration, however we highly recommend contacting your web hosting company for assistance with making this change as each hosting environment is different.

```
location /wordpress/wp-content/plugins/s2member-files {
        deny  all;
        return 403;
}
```

## Basic Download Restrictions

Yes, Basic Download Restrictions (**s2Member → Download Options → Basic Download Restrictions**) will work just fine with NGINX.

## Using the `[s2File /]` Shortcode

The `[s2File /]` shortcode should work just fine with NGINX. No additional configuration is necessary.

## Advanced Mod-Rewrite Linkage

This feature will _not_ work with NGINX. Rewriting in s2Member depends on using an `.htaccess` file, which means that rewriting will not work with NGINX.

## Using the `[s2Stream /]` Shortcode and JWPlayer

If you are self-hosting your video files (i.e., in `wp-content/plugins/s2member-files/`), then you must set the shortcode attribute `rewrite="no"`, to tell the `[s2Stream /]` shortcode _not_ to do any rewriting, as rewriting will not work with NGINX.

If you are using Amazon S3/CloudFront integration and hosting your video files with Amazon, you don't need to do anything special--the default `[s2Stream /]` shortcode should work as expected. 

## Advanced Download Restrictions

Yes, Advanced Download Restrictions (**s2Member → Download Options → Advanced Download Restrictions**) should work just fine with NGINX, as that functionality relies on PHP and is not dependent on the web server.

## Remote Auth / Podcasting

Yes, Remote Authentication, most commonly used with podcasting (**s2Member → Download Options → Remote Auth / Podcasting**), should work fine with NGINX. The remote auth headers are sent via PHP and not the web server, so the s2Member implementation of this should work with NGINX.

## Summary

To summarize, the main thing you need to be aware of when using Download Restrictions with s2Member and NGINX is that you must protect the `/s2member-files/` directory inside your NGINX web server configuration. Once that has been done, the following points should be kept in mind.

The following should work fine with NGINX:

- Basic Download Restrictions
- Advanced Download Restrictions
- Remote Auth / Podcasting
- `[s2File /]` Shortcode
- `[s2Stream /]` Shortcode w/ self-hosted files and `rewrite="no"` shortcode attribute
- `[s2Stream /]` Shortcode w/ Amazon S3/CloudFront

The following will not work with NGINX:

- Advanced Mod-Rewrite Linkage