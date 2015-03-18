---
title: '[s2Stream /] Shortcode + Amazon S3/CloudFront'
categories: tutorials, videos
tags: download-options, amazon-s3-cloudfront-cdn-storage-option, s2stream, s2file
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/96
toc-enable: false
---

https://www.youtube.com/watch?v=ZTopRQQAELw

---

## Amazon S3 (Protected File Downloads)

[Amazon Simple Storage Service](http://aws.amazon.com/s3/) (Amazon S3). Amazon S3 is storage for the Internet. It is designed to make web-scale computing easier for developers. Amazon S3 provides a simple web services interface that can be used to store and retrieve any amount of data, at any time, from anywhere on the web. It gives developers access to the same highly scalable, reliable, secure, fast, inexpensive infrastructure that Amazon uses to run its own global network of web sites. s2Member has been integrated with Amazon S3, so that (if you wish), instead of using the `/s2member-files/` directory, you can store all of your protected files inside an Amazon S3 Bucket.

## Amazon S3 + Amazon CloudFront (CDN + Media Server)

Amazon Simple Storage Service (Amazon S3) combined with [Amazon CloudFront](http://aws.amazon.com/cloudfront/). Amazon CloudFront is a web service for content delivery. It integrates with other Amazon Web Services (i.e. Amazon S3 Storage) to give developers and businesses an easy way to distribute content to end users with low latency, and with high data transfer speeds. Amazon CloudFront delivers your static and streaming content using a global network of edge locations. Requests for your Amazon S3 Bucket Objects (i.e. your protected files) are automatically routed to the nearest edge location, so content is delivered with the best possible performance. s2Member has been integrated with both Amazon S3 and with Amazon CloudFront. So (if you wish), instead of using the `/s2member-files/` directory, you can store all of your protected files inside an Amazon S3 Bucket and serve them via Amazon CloudFront.

One of the great things about Amazon CloudFront, is its ability to stream/seek media files in the truest sense of the word. For sites delivering protected FLV/MP4/OGG/WEBM and other streaming audio/video file types over the RTMP protocol, Amazon CloudFront is our recommendation. RTMP streams allow site owners to stream their videos, but without ever exposing an MP4 video file that could potentially be redistributed by viewers. Videos streamed over RTMP are not downloadable. Perfecto!
