---
title: Resolving File Download Problems
categories: tutorials
tags: download-options,troubleshooting
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/142
---

## Disable GZIP Compression Momentarily

If you're running s2Member with `mod_deflate` for Apache (common on many hosts, including BlueHost), you'll want to add this section to the top of your WordPress `.htaccess` file so that your installation of Apache will know when it should _not_ use GZIP compression. This `.htaccess` file should be located in the same root directory as your WordPress files. If you already have an `.htaccess` file in this location (very common), then please add this snippet right above the section for WordPress itself.

_**What does this do?** It temporarily disables GZIP compression for files that s2Member serves locally via PHP._

```apache
# BEGIN s2Member GZIP exclusions
<IfModule rewrite_module>
	RewriteEngine On
	RewriteBase /
	RewriteCond %{QUERY_STRING} (^|\?|&)s2member_file_download\=.+ [OR]
	RewriteCond %{QUERY_STRING} (^|\?|&)no-gzip\=1
	RewriteRule .* - [E=no-gzip:1]
</IfModule>
# END s2Member GZIP exclusions
```

### ↑ UPDATE: Now Added Automatically by s2Member

As of s2Member v120213+, s2Member will automatically attempt to add this code to the `.htaccess` file at the web root. This disables GZIP compression when s2Member attempts to deliver files. GZIP compression _must_ be disabled during s2Member's attempt to deliver a file via PHP, because files that s2Member delivers via PHP are already compressed. Thus, re-compressing files delivered by a script will corrupt them in your browser. Note that some media playback devices will choke on this as well. It's never a bad idea to place this in your `.htaccess` file, regardless of server configuration.

### More Information About GZIP Compression & s2Member

s2Member makes every attempt to programmatically disable GZIP during it's delivery of a file. However, in some scenarios (with certain server configurations) s2Member may fail to do so. This issue is often related to the use of `mod_deflate` for GZIP compression. Unfortunately, when s2Member is running on a CGI-based installation of PHP it has only _one_ way to disable GZIP compression via PHP.

The only way for s2Member to disable GZIP compression on a CGI-based installation of PHP is to send: `Content-Encoding: none`. However, this header goes against standards and was thus removed in more recent versions of s2Member. It's just not a good idea to send an invalid header. It's better to solve the underlying issue. For instance, this invalid header: `Content-Encoding: none` is known to cause an issue with the `WP_Http` class. s2Member now empties this header instead of setting it to `none`, which is the correct standards-compliant method of saying "no GZIP here".

Unfortunately, CGI-based installations of PHP don't look at `Content-Encoding:` empty as expected. When `mod_deflate` is being used (which is a good idea, nothing wrong with this) it will attempt to GZIP all PHP script output, regardless of `Content-Type`. This is a limitation on CGI-based installations of PHP. On installations of PHP running as an Apache module, s2Member has no trouble; because it can call upon `apache_setenv('no-gzip')`. It's more difficult when dealing with a CGI or FastCGI extension though.

**Solution for CGI or FastCGI?** Yes, the snippet above resolves the problem. Please make sure you have the snippet (shown above) in the `.htaccess` file in the root directory of your WordPress installation. This resolves the problem on all PHP installations—even those running via CGI or FastCGI.

## Does `wp-content/plugins/s2member-files/.htaccess` Exist?

You should also have an `.htaccess` file in your `/s2member-files/` directory. If you don't, please re-install s2Member and that will create the proper `.htaccess` file automatically. Either that, or create this file `/wp-content/plugins/s2member-files/.htaccess` with the following contents:

```apache
<IfModule env_module>
# No GZIP for script-based file downloads.
	SetEnv no-gzip 1
</IfModule>

<IfModule rewrite_module>
# Enable symlinks (required for rewrites).
	Options +FollowSymLinks

# Enable rewrite and configure base.
	RewriteEngine On
	RewriteBase /

# Initialize all environment variables we're using below.
	RewriteCond %{ENV:s2member_file_download_setup} !^complete$
	RewriteRule ^(.*)$ - [E=s2member_file_download_wp_vdir:0,E=s2member_file_download:$1,E=s2member_file_stream:0,E=s2member_file_inline:0,E=s2member_file_storage:0,E=s2member_file_remote:0,E=s2member_file_ssl:0,E=s2member_file_download_key:0,E=s2member_skip_confirmation:0,E=s2member_file_download_setup:complete]

# Handle virtual directories, common on multisite networks.
	RewriteCond %{ENV:s2member_file_download_wp_vdir_check} !^complete$
	RewriteCond %{THE_REQUEST} ^(?:GET|HEAD)(?:[\ ]+)(?:/)([_0-9a-zA-Z\-]+/)(?:wp-content/)
	RewriteRule ^(.*)$ - [E=s2member_file_download_wp_vdir:,E=s2member_file_download_wp_vdir:%1,E=s2member_file_download_wp_vdir_check:complete]

# Handle streaming download requests via the rewrite engine.
	RewriteCond %{ENV:s2member_file_download} ^(.*?)(?:s2member-file-stream/)(.+)$
	RewriteRule ^(.*)$ - [N,E=s2member_file_download:,E=s2member_file_download:%1%2,E=s2member_file_stream:,E=s2member_file_stream:&s2member_file_stream=yes]

	RewriteCond %{ENV:s2member_file_download} ^(.*?)(?:s2member-file-stream-(.+?)/)(.+)$
	RewriteRule ^(.*)$ - [N,E=s2member_file_download:,E=s2member_file_download:%1%3,E=s2member_file_stream:,E=s2member_file_stream:&s2member_file_stream=%2]

# Handle inline file requests via the rewrite engine.
	RewriteCond %{ENV:s2member_file_download} ^(.*?)(?:s2member-file-inline/)(.+)$
	RewriteRule ^(.*)$ - [N,E=s2member_file_download:,E=s2member_file_download:%1%2,E=s2member_file_inline:,E=s2member_file_inline:&s2member_file_inline=yes]

	RewriteCond %{ENV:s2member_file_download} ^(.*?)(?:s2member-file-inline-(.+?)/)(.+)$
	RewriteRule ^(.*)$ - [N,E=s2member_file_download:,E=s2member_file_download:%1%3,E=s2member_file_inline:,E=s2member_file_inline:&s2member_file_inline=%2]

# Handle storage specifications via the rewrite engine.
	RewriteCond %{ENV:s2member_file_download} ^(.*?)(?:s2member-file-storage-(.+?)/)(.+)$
	RewriteRule ^(.*)$ - [N,E=s2member_file_download:,E=s2member_file_download:%1%3,E=s2member_file_storage:,E=s2member_file_storage:&s2member_file_storage=%2]

# Handle remote authorization requests via the rewrite engine.
	RewriteCond %{ENV:s2member_file_download} ^(.*?)(?:s2member-file-remote/)(.+)$
	RewriteRule ^(.*)$ - [N,E=s2member_file_download:,E=s2member_file_download:%1%2,E=s2member_file_remote:,E=s2member_file_remote:&s2member_file_remote=yes]

	RewriteCond %{ENV:s2member_file_download} ^(.*?)(?:s2member-file-remote-(.+?)/)(.+)$
	RewriteRule ^(.*)$ - [N,E=s2member_file_download:,E=s2member_file_download:%1%3,E=s2member_file_remote:,E=s2member_file_remote:&s2member_file_remote=%2]

# Handle SSL file requests via the rewrite engine.
	RewriteCond %{ENV:s2member_file_download} ^(.*?)(?:s2member-file-ssl/)(.+)$
	RewriteRule ^(.*)$ - [N,E=s2member_file_download:,E=s2member_file_download:%1%2,E=s2member_file_ssl:,E=s2member_file_ssl:&s2member_file_ssl=yes]

	RewriteCond %{ENV:s2member_file_download} ^(.*?)(?:s2member-file-ssl-(.+?)/)(.+)$
	RewriteRule ^(.*)$ - [N,E=s2member_file_download:,E=s2member_file_download:%1%3,E=s2member_file_ssl:,E=s2member_file_ssl:&s2member_file_ssl=%2]

# Handle file download keys via the rewrite engine.
	RewriteCond %{ENV:s2member_file_download} ^(.*?)(?:s2member-file-download-key-(.+?)/)(.+)$
	RewriteRule ^(.*)$ - [N,E=s2member_file_download:,E=s2member_file_download:%1%3,E=s2member_file_download_key:,E=s2member_file_download_key:&s2member_file_download_key=%2]

# Handle confirmations having beek skipped via the rewrite engine.
	RewriteCond %{ENV:s2member_file_download} ^(.*?)(?:s2member-skip-confirmation/)(.+)$
	RewriteRule ^(.*)$ - [N,E=s2member_file_download:,E=s2member_file_download:%1%2,E=s2member_skip_confirmation:,E=s2member_skip_confirmation:&s2member_skip_confirmation=yes]

	RewriteCond %{ENV:s2member_file_download} ^(.*?)(?:s2member-skip-confirmation-(.+?)/)(.+)$
	RewriteRule ^(.*)$ - [N,E=s2member_file_download:,E=s2member_file_download:%1%3,E=s2member_skip_confirmation:,E=s2member_skip_confirmation:&s2member_skip_confirmation=%2]

# Cleanup variables not used in this request. Looking for `0` values.
	RewriteCond %{ENV:s2member_file_download_wp_vdir} ^0$
	RewriteRule ^(.*)$ - [E=s2member_file_download_wp_vdir:]

	RewriteCond %{ENV:s2member_file_stream} ^0$
	RewriteRule ^(.*)$ - [E=s2member_file_stream:]

	RewriteCond %{ENV:s2member_file_inline} ^0$
	RewriteRule ^(.*)$ - [E=s2member_file_inline:]

	RewriteCond %{ENV:s2member_file_storage} ^0$
	RewriteRule ^(.*)$ - [E=s2member_file_storage:]

	RewriteCond %{ENV:s2member_file_remote} ^0$
	RewriteRule ^(.*)$ - [E=s2member_file_remote:]

	RewriteCond %{ENV:s2member_file_ssl} ^0$
	RewriteRule ^(.*)$ - [E=s2member_file_ssl:]

	RewriteCond %{ENV:s2member_file_download_key} ^0$
	RewriteRule ^(.*)$ - [E=s2member_file_download_key:]

	RewriteCond %{ENV:s2member_skip_confirmation} ^0$
	RewriteRule ^(.*)$ - [E=s2member_skip_confirmation:]

# Put everything together now and process the internal rewrite.
	RewriteRule ^(.*)$ %{ENV:s2member_file_download_wp_vdir}?s2member_file_download=%{ENV:s2member_file_download}%{ENV:s2member_file_stream}%{ENV:s2member_file_inline}%{ENV:s2member_file_storage}%{ENV:s2member_file_remote}%{ENV:s2member_file_ssl}%{ENV:s2member_file_download_key}%{ENV:s2member_skip_confirmation} [QSA,L]
</IfModule>

<IfModule !rewrite_module>
	<IfModule authz_core_module>
		Require all denied
	</IfModule>
	<IfModule !authz_core_module>
		deny from all
	</IfModule>
</IfModule>
```
