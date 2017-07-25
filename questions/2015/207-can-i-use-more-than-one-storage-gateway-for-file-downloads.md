---
title: Can I use more than one storage gateway for file downloads?
categories: questions
tags: s2file, download-options, basic-download-restrictions, s2stream, rtmp
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/207
toc-enable: off
---

Yes. If you're storing protected files locally (in the `wp-content/plugins/s2member-files/` directory) but you want to store some of the files on Amazon S3/CloudFront, this can be achieved by manually specifying the file storage gateway. By default, s2Member will default to using local storage (`/s2member-files/`) when Amazon S3/CloudFront is not configured and it will default to using Amazon S3/CloudFront when it is configured.

If you want to override the default behavior and host some of your protected files locally, while hosting other protected files on Amazon S3/CloudFront, simply configure Amazon S3/CloudFront (**WordPress Dashboard → s2Member → Download Options → Amazon S3/CDN Storage Option**) and then specify the file storage gateway in your File Download Links and/or `[s2File /]` or `[s2Stream /]` shortcodes using `&s2member_file_storage=` (links) or `storage=` (shortcodes).

## File Download Links
 
To force a particular storage gateway whenever you generate a download link, you can simply include `&s2member_file_storage=[s3|cf|local]` in the URL. 

For example, to force a local storage location (`/s2member-files/`) when you have Amazon S3/CloudFront configured, you would add `&s2member_file_storage=local` to your file download links.

## s2File and s2Stream Shortcodes

The `[s2File /]` and `[s2Stream /]` shortcodes both support a `storage=""` attribute that allows you to pass in one of three options: `local`, `s3`, or `cf` (CloudFront). 

For example, to force a local storage location (`/s2member-files/`) when you have Amazon S3/CloudFront configured, you would add `storage="local"` to the shortcode for the locally-hosted file.

For more information, see the [\[s2Stream /\] Shortcode Documentation](http://s2member.com/kb-article/s2stream-shortcode-documentation/#toc-f5f9fcf2).

# An Important Note Regarding RTMP Streaming

If you are using RTMP Streaming, note that using RTMP will always require Amazon S3 + CloudFront, because RTMP requires a dedicated media server—which is a function of Amazon CloudFront. You cannot use RTMP Streaming when specifying the local storage option.
