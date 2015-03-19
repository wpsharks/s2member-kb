---
title: What `.htaccess` files does s2Member create?
categories: questions
tags: server-config-files,download-options
author: raamdev
github-issue: https://github.com/websharks/s2member-kb/issues/5
toc-enable: false
---

s2Member creates two `.htaccess` entries. One in the root `.htaccess` file, and the other is actually a separate `.htaccess` file that is specifically for s2Member's File Download functionality; which goes into a directory that is dedicated to that purpose; i.e., `/wp-content/plugins/s2member-files/.htaccess`.

---

## Root `.htaccess` Entry for Apache

s2Member writes the following entry into the root `.htaccess` file on installation and/or update of the s2Member plugin. It can also occur whenever you save your **s2Member → Download Options**, where s2Member sees that the entry is not there. Currently, the only way to prevent this is to change file permissions on `/wp-config.php`. If it's not writable, s2Member will not attempt to do this.

### Why does s2Member add this entry to my `.htaccess` file?

For a full explanation, please see: [this KB article about GZIP conflicts](http://s2member.com/kb-article/resolving-file-download-problems/)

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

---

## `.htaccess` for Protected Files on Apache

You should have an `.htaccess` file in your `/s2member-files/` directory. If you don't, please re-install s2Member and that will create the proper `.htaccess` file automatically. Either that, or create this file: `/wp-content/plugins/s2member-files/.htaccess` with the following contents...

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

**See also:** [Resolving File Download Problems](http://s2member.com/kb-article/resolving-file-download-problems/#toc-f2f90d17)