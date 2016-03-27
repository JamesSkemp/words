+++
title = "Upgrading phpMyAdmin (2.7.0-pl2 to 2.8.1) on a local, Windows-based, Apache server"
description = "In this guide, we'll be upgrading phpMyAdmin 2.7.0-pl2 to 2.8.1, on a Windows machine, running Apache 1.x."
draft = false
comments = true
date = "2006-06-20T15:00:00-05:00"
modified = "2007-07-22T17:22:25-05:00"
slug = "Upgrading-phpMyAdmin-(270-pl2-to-281)-on-a-local-Windows-based-Apache-server"
blogengine = "85c8a6f5-bbea-435d-b824-b0daa3225e9f"
categories = ["tutorials / guides"]
tags = ["phpmyadmin", "apache", "mysql"]
+++

<p>
In a <a href="http://strivinglife.net/wordpress/?p=53">previous post</a>, we installed phpMyAdmin 2.7.0-pl2 to our local Web server. We did this so that we would have an easy way to administer our MySQL databases, from a PHP-based interface. This time, we&#39;ll be upgrading phpMyAdmin to version 2.8.1.
</p>
<!--more-->
<h4>Downloading and unzipping</h4>
<p>
First, we&#39;ll need to grab the download for phpMyAdmin, from <a href="http://www.phpmyadmin.net/">http://www.phpmyadmin.net/</a>. As of this writing, the current version is 2.8.1. The zip file runs about 3.5 MB.<!--adsense-->
</p>
<p>
Once the download has finished, we can unzip the file into our main Web directory (C:\home). Depending upon how you installed the previous version of phpMyAdmin, you can either keep this new version in a folder containing the version number, or not. For example: c:\home\phpMyAdmin-2.8.1\ or c:\home\phpMyAdmin\ If you&#39;ll be doing things the latter way, make sure you make a backup of your previously installed phpMyAdmin directory - just in case. If you&#39;ll be saving to a directory containing the version information, then there&#39;s no real reason to remove the old directory (unless you&#39;re concerned with space).
</p>
<h4>Configuring phpMyAdmin</h4>
<p>
At this point you can go to <a href="http://localhost/phpmyadmin-2.8.1/">http://localhost/phpmyadmin-2.8.1/</a> However, if you do so, you&#39;ll notice that you&#39;re unable to view the interface due to an error. As with our initial install, we need to configure phpMyAdmin before we can start using it.
</p>
<p>
Browse to the directory containing your previous installation of phpMyAdmin (for example, C:\home\phpMyAdmin-2.7.0-pl2\) and copy the file config.inc.php. Now, make a copy of this file in your upgraded phpMyAdmin&#39;s directory - C:\home\phpMyAdmin-2.8.1\config.inc.php, for example.
</p>
<p>
Open this file and verify that $cfg[&#39;PmaAbsoluteUri&#39;] (on line 31) is correct. If you&#39;ve switched from one directory scheme to another (with version number to without, or vice versa), then this may not be correct.
</p>
<p>
You should now be able to refresh, or visit, <a href="http://localhost/phpmyadmin-2.8.1/">http://localhost/phpmyadmin-2.8.1/</a> and log in, using one of the MySQL user names and passwords you&#39;ve setup.
</p>
<p>
Finally, if you setup a subdomain in your httpd.conf file (C:\Program Files\Apache Group\Apache\conf\), you can modify the subdomain so that it points to the correct path. If you make this change, make sure you restart Apache afterwards.
</p>
<p>
And with that, you&#39;ve successfully updated phpMyAdmin. Really, a pretty easy upgrade.
</p>
<p>
<a href="http://strivinglife.net/wordpress/a-local-apache-web-server-on-a-windows-xp-computer/">View all of the steps to creating a local Web server, for development.</a>
</p>

