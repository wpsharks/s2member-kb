---
title: How do I display protected PDFs with the PDF Viewer plugin?
categories: questions
tags: basic-download-restrictions, download-options
author: raamdev
toc-enable: off
github-issue: https://github.com/websharks/s2member-kb/issues/274
---

To display PDF files that you've protected with s2Member using Download Restrictions (which you do by uploading the files to the `/s2member-files/` directory), you can use a plugin such as the WordPress [PDF Viewer](https://wordpress.org/plugins/pdf-viewer/) plugin. However, to pass s2Member-protected file URLs to the PDF Viewer plugin, you must make use of the Apache Mod-Rewrite links, which is explained below.

There are three ways of linking to s2Member-protected files: 1) Using the `[s2File /]` shortcode, 2) linking directly using the `?s2member_file_download=example-file.zip` URL, and 3) using Mod-Rewrite (see **Dashboard → s2Member → Download Options → Advanced Mod-Rewrite Linkage**).

The last method, using Mod-Rewrite, is the only method that will work with the PDF Viewer plugin. To use the Mod-Rewrite method, simply build the link to your protected PDF file inside the `/s2member-files/` directory as follows:

```
http://example.com/wp-content/plugins/s2member-files/s2member-file-inline-no/EXAMPLE.pdf
```

In the above example, we have a file called `EXAMPLE.pdf` that has been uploaded to the `/s2member-files/` directory (note that the `s2member-file-inline-no` portion of the URL is _not_ a directory--that's how you tell s2Member to serve the file "inline" using Mod-Rewrite; this is the same as specifying `inline="yes"` in the `[s2File /]` shortcode and `&s2member_file_inline=yes` using the standard linking method). 

Using that Mod-Rewrite URL to the protected PDF file, you can then tell the PDF Viewer to load the file (assuming the user has permission to download the file):

```
[pdfviewer width="600px" height="849px"]http://example.com/wp-content/plugins/s2member-files/s2member-file-inline-no/EXAMPLE.pdf[/pdfviewer]
```

![2015-11-04_21-56-14](https://cloud.githubusercontent.com/assets/53005/10958701/e93952aa-833e-11e5-8cdd-1d5b992277c3.png)