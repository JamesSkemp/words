+++
title = "Upgrading PHP (4.4.2 to 4.4.4 and 5.1.4 to 5.2.0)"
summary = "In this article, we'll be upgrading PHP, both 4.4.2 to 4.4.4 and 5.1.4 to 5.2.0."
draft = false
comments = true
date = "2006-11-26T17:00:00-06:00"
modified = "2009-10-15T07:35:31-05:00"
slug = "Upgrading-PHP-(442-to-444-and-514-to-520)"
blogengine = "54e8a9b7-294d-46a6-912d-8ac2c2b17f5b"
categories = ["tutorials / guides"]
tags = ["apache", "php"]
+++

<p>In this article, we'll be upgrading PHP on our local, Windows, Web server. In previous guides we installed PHP 4.4.2 as well as PHP 5.1.4, both on the same machine, with the ability to switch as we like. However, we've yet to cover how to upgrade either installation (and upgrading is definitely a need).</p>
<p>At the time of this writing, the current versions of PHP are 4.4.4 and 5.2.0, for the 4.x and 5.x versions, respectively.<!--more--></p>
<p>We'll be going over the upgrade for each version separately, so you can simply skip to which version you're currently using.</p>
<h4>Upgrading PHP 4.4.2 to PHP 4.4.4</h4>
<p>First off, make sure that Apache has been stopped.<!--adsense--></p>
<p>Now, rename the directory where you've installed PHP 4.x to ... have the suffix of '-previous' (for example, c:\php4-previous\). We'll do this, instead of installing over the directory so that we have a backup copy, as well as a 'clean' version of the install directory.</p>
<p>Next, you should have, or should, download the Windows binary in zip format, for the most current version of PHP 4.x (4.4.4 at the time of this writing). Extract the contents of this folder so that you have the same directory structure as before.</p>
<p>For example, for the previous version of PHP, my php.exe file was at c:\php4\php.exe. For the new install, I'll want php.exe to be in the same location.</p>
<p>Once that's done, we'll want to grab the php4apache.dll and/or php4apache2.dll files from our previous install directory and put a copy of them into our new install directory.</p>
<p>For the new version of PHP 4.x, make a copy the php4ts.dll file and put the copy in the Windows folder (c:\windows\).</p>
<p>Next, there's the matter of the php.ini file. At this point, I did a compare of the new version's file with the previous version's file (php.ini-dist) using <a href="http://strivinglife.net/wordpress/2006/10/16/249/winmerge-26-released/">WinMerge</a>. Luckily, the two files are identical, so there's no updating necessary.</p>
<p>At this point, you can start up Apache and hit your phpinfo page (code listed below). You should see that PHP's version has been updated to 4.4.4. If you'd like, you can also test your connection to the database server of your choice (MySQL and/or PostgreSQL).</p>
<pre class="code"><code class="php">&lt;?php
phpinfo();
?&gt;</code></pre>
<p>Now that we're set with our new version of PHP 4.x, you can either delete, or as I recommend, archive, your old PHP install directory, just in case something comes up in the next couple of weeks. Also, if you have any non-core extensions, you'll want to make sure that those get moved over as well.</p>
<p>Next, we've got our PHP 5.x installation to upgrade.<!--nextpage--></p>
<h4>Upgrading PHP 5.1.4 to PHP 5.2.0</h4>
<p>Upgrading PHP 5.x is almost exactly the same as upgrading PHP 4.x.</p>
<p>First, make sure that Apache has been stopped. Next, rename your current PHP 5.x directory (I added '-previous' to the end of my directory's name). If you don't already have a copy, download the Windows PHP 5.x binaries and extract them so that you preserve the same file structure as before.</p>
<p>For example, php.exe was located at c:\php5\php.exe for my previous version, so that's also where it should sit in the new directory.</p>
<p>Next, make a copy of the php5ts.dll file and put it into the Windows directory (c:\windows\ for example), overwriting the old one. If you installed any extensions, copy those extensions over from your previous install's directory to your new install's directory.</p>
<p>Now there's the matter of the php.ini file. At this point, I did a compare of the new version's file with the previous version's file (php.ini-dist) using <a href="http://strivinglife.net/wordpress/2006/10/16/249/winmerge-26-released/">WinMerge</a> and there's a number of changes.</p>
<p>So, what you'll want to do is compare your PHP.ini file with the php.ini-dist file from the previous version, so we can get an idea of what changes were made. Now, make a copy of the new php.ini-dist and make the same changes you've made for the old version.</p>
<p>For example, six changes had been made to my php.ini file, which I've listed below.</p>
<pre class="code"><code class="powershell">doc_root
extension_dir
extension=php_mysql.dll
extension=php_pgsql.dll
session.save_path
[Zend]</code></pre>
<p>Once you've ported over all of your changes, make a backup of your old php.ini file and replace it with the updated version. You can now restart Apache (2) and verify using phpinfo() that your version has been upgraded. You'll also want to check your database connection(s) as well.</p>
<p>And with that, you've updated PHP 5.x.</p>
<p><a href="http://strivinglife.net/wordpress/a-local-apache-web-server-on-a-windows-xp-computer/">View all of the steps to creating a local Web server, for development.</a></p>
