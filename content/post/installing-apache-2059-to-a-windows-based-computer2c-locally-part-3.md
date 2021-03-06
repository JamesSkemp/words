+++
title = "Installing Apache 2.0.59 to a Windows-based computer, locally: Part 3"
description = "In part three of this multi-part guide, we'll be porting over from an Apache 1.3.x Web server to an Apache 2.0.x Web server by adding support for PHP 4.4.2 and PHP 5.1.4.  We also go over how to setup MySQL and PostgreSQL for our new version of Apache. In the last guide of this series, we'll be going over how to create batch files to switch between all of the different possible servers we can now run."
draft = false
comments = true
date = "2006-08-26T16:09:00-05:00"
modified = "2009-12-20T20:00:28-06:00"
slug = "Installing-Apache-2059-to-a-Windows-based-computer2c-locally-Part-3"
blogengine = "2aa73834-f63d-40d0-860b-e930a7e0449c"
categories = ["software", "tutorials / guides"]
tags = ["coldfusion", "postgresql", "php", "mysql", "apache"]
+++

<p>In <a href="/words/post/Installing-Apache-2059-to-a-Windows-based-computer2c-locally-Part-1.aspx">Part 1 of this Apache 2.0.59 guide</a>, we setup Apache 2.0.59 on a Windows XP SP2 machine. We also setup Perl and mod_perl, attempting to mimic our Apache 1.3.34 install. In <a href="/words/post/Installing-Apache-2059-to-a-Windows-based-computer2c-locally-Part-2.aspx">Part 2 of this Apache 2.0.59 guide</a>, we setup ColdFusion MX 6.1 and 7.0. This time, we'll be continuing in our quest by adding support for both PHP 4 and PHP 5.</p>
<p>In previous guides, we <a href="/words/post/Installing-PHP-on-a-local-Windows-based2c-Apache2c-server.aspx">installed PHP 4</a> and <a href="/words/post/Dual-installing-PHP-Running-PHP-5-and-4-on-the-same-local2c-Windows-based2c-Apache2c-server.aspx">PHP 5</a>, so if you need to install either one, do so with the above directions. If you'll be installing PHP 4 and PHP 5 for the first time, and have not installed on Apache 1.3.x already, then you may be able to pick and choose from these guides to get the information you need.</p>
<p>Before we do this, however, we need to think about just what we're doing.</p>
<p>Up until this point, you may have installed any (or none) of the below. (Keep in mind that you can generalize these if you have slightly newer versions. So, PHP 5.1.4 = PHP 5.x.)</p>
<ul>
<li>Apache 1.3.34</li>
<li>Apache 2.0.59</li>
<li>PHP 4.4.2</li>
<li>PHP 5.1.4</li>
<li>ColdFusion MX 6.1</li>
<li>ColdFusion MX 7.0.2</li>
</ul>
<p>This gives us a number of options on what our local Web server could be running at one time. For example, we could be running PHP 4, ColdFusion MX 6.1, and Apache 1.3.x or Apache 2.0.x. Likewise, we could use PHP 4 or PHP 5, or ColdFusion MX 6.1 or ColdFusion MX 7.0. Writing out a list of all of our possible combinations, we've got something like the following.</p>
<ol>
<li>Apache1.3_CF6.1_PHP4</li>
<li>Apache1.3_CF7.0_PHP4</li>
<li>Apache1.3_CF6.1_PHP5</li>
<li>Apache1.3_CF7.0_PHP5</li>
<li>Apache2.0_CF6.1_PHP4</li>
<li>Apache2.0_CF7.0_PHP4</li>
<li>Apache2.0_CF6.1_PHP5</li>
<li>Apache2.0_CF7.0_PHP5</li>
</ol>
<p>Of course, we could also run our local server without the ColdFusion MX component, or PHP component at all. For ease, however, we'll just stick with one of the above possibilities. What this means is that for each of the above that you want to run, you'll need to have an httpd.conf file.</p>
<p>If you followed my above guides, than you should already have the Apache 1.3.x configuration files (although with slightly different names). Once we have all eight configurations, we can write batch files to automate most of the process. For getting these up and running. With one click (and maybe just a little renaming), we can have the Web server that we want up and running.</p>
<p>Whatever you may have for Apache 1.3.x, I recommend you create a 'configuration' folder in your DocumentRoot directory (so, c:\home\configuration\ if you've been following along) where you can begin compiling httpd.conf files.</p>
<p>For example, I've obviously followed by own guides, so I have four files thus far.</p>
<ul>
<li>httpd_Apache1.3_CFMX6.1_PHP4.conf </li>
<li>httpd_Apache1.3_CFMX6.1_PHP5.conf </li>
<li>httpd_Apache1.3_CFMX7.0_PHP4.conf </li>
<li>httpd_Apache1.3_CFMX7.0_PHP5.conf </li>
</ul>
<p>We should also have either one or two php.ini files &ndash; one for PHP 4 and one for PHP 5 &ndash; that we'll also want to put copies of in this folder.</p>
<ul>
<li>php_Apache_PHP4.ini </li>
<li>php_Apache_PHP5.ini </li>
</ul>
<p>Apache 1.3.x and Apache 2.0.x use the same php.ini files. So, it's not necessary to make one copy each for Apache 1.3.x and one each for 2.0.x.</p>
<p>This done, we can begin connecting to PHP 4 and PHP 5 on Apache 2.0.x.</p>
<h3>Hooking up PHP 4.4.2</h3>
<p>In a previous guide, we <a href="/words/post/Installing-PHP-on-a-local-Windows-based2c-Apache2c-server.aspx">installed PHP 4.4.2</a> and in yet <a href="/words/post/Moving-the-location-of-PHP-on-your-hard-drive.aspx">a later guide moved our installation</a> to the c:\php4\ folder.</p>
<p>Since we've already got PHP 4 working on Apache 1.3.x, most of our setup is already complete. Now it's just a matter of hooking up Apache 2.0.x to recognize it.</p>
<p>First, we'll need to make sure we've got a backup of the httpd.conf file in the C:\Program Files\Apache Group\Apache2\conf folder.</p>
<p>Now open the Apache 2 httpd.conf file. Do a search for LoadModule, and at the end of this section, add the following line. Keep in mind that if you installed PHP 4 to a different folder, you should make that change here as well.</p>
<blockquote>
<p>LoadModule php4_module "c:/php4/php4apache2.dll"</p>
</blockquote>
<p>Now, do a search for AddType. After the first uncommented line (AddType application/x-gzip .gz .tgz), place the following.</p>
<blockquote>
<p>AddType application/x-httpd-php .php<br />AddType application/x-httpd-php-source .phps</p>
</blockquote>
<p>Finally, add 'index.php' to the DirectoryIndex line, where ever you'd like it be called in the order of things. Depending upon preference, you may also want to add index.htm, since Apache 2.0.x doesn't seem to want to include these.</p>
<p>Save httpd.conf. Now go to the c:\php4\ directory (or where you installed PHP 4) and copy the php4apache2.dll from the sapi folder into the root PHP folder. So, from c:\php4\sapi\ to c:\php4\.</p>
<p>For php.ini, everything should be setup correctly. However, you'll want to verify that the right php.ini file is in place.</p>
<p>Now start Apache2 from the Services panel (or the Apache Services Monitor) and you should find that the description lists PHP 4. If you go to <a href="http://localhost/phpinfo.php">http://localhost/phpinfo.php</a> (if you created this file), you should also find that PHP is up and running.</p>
<p>Make sure both your ColdFusion MX 6.1 and ColdFusion MX 7.0 httpd.conf files have the httpd.conf changes made, and you can switch between either version.</p>
<h3>Connecting to PHP 5</h3>
<p>Assuming you've already setup PHP 4 for Apache 2.0.x, using the instructions above, moving to PHP 5 is extremely easy. So easy, in fact, that it's scary. Make a copy of any httpd.conf files you may have for PHP 4. For example, the two I have in C:\Program Files\Apache Group\Apache2\conf\ are called httpd_CFMX6.1_PHP4.conf and httpd_CFMX7.0_PHP4.conf.</p>
<p>I'll copy both of these and rename them to httpd_CFMX6.1_PHP5.conf and httpd_CFMX7.0_PHP5.conf. That done open both up and do a search for php4, one file at a time. You'll find php4 three times, in the following line.</p>
<blockquote>
<p>LoadModule php4_module "c:/php4/php4apache2.dll"</p>
</blockquote>
<p>Which you'll simply change to three '5's.</p>
<blockquote>
<p>LoadModule php5_module "c:/php5/php5apache2.dll"</p>
</blockquote>
<p>Now save the httpd.conf files. The php5apache2.dll file will already be in this location, so you should be set to go. Make a copy of either one of these, make sure that you're using the right php.ini file, restart Apache2, and verify that phpinfo() gives the correct information.</p>
<p>Wasn't that easy?</p>
<h3>Now that PHP 4 and/or PHP 5 are installed ...</h3>
<p>Now that we've setup PHP 4 and/or PHP 5 with Apache 2.0.x, it's time to backup the necessary .conf files into our 'configuration' folder.</p>
<p>At this point, you'll have up to ten files in this folder (c:\home\configuration\). Up to eight .conf files and up to two .ini files. I've listed all ten possibilities below.</p>
<ul>
<li>httpd_Apache1.3_CFMX6.1_PHP4.conf </li>
<li>httpd_Apache1.3_CFMX6.1_PHP5.conf </li>
<li>httpd_Apache1.3_CFMX7.0_PHP4.conf </li>
<li>httpd_Apache1.3_CFMX7.0_PHP5.conf </li>
<li>httpd_Apache2.0_CFMX6.1_PHP4.conf </li>
<li>httpd_Apache2.0_CFMX6.1_PHP5.conf </li>
<li>httpd_Apache2.0_CFMX7.0_PHP4.conf </li>
<li>httpd_Apache2.0_CFMX7.0_PHP5.conf </li>
<li>php_Apache_PHP4.ini </li>
<li>php_Apache_PHP5.ini </li>
</ul>
<p>Now, let's create a blank text file called zblank.txt. Next, we should determine whether we want to have a version that does not run ColdFusion MX. If you want to, read the next section. Otherwise, skip the next section and read the following one.</p>
<!--nextpage-->
<h3>Removing ColdFusion MX from our configurations</h3>
<p>To remove ColdFusion MX, you'll need four more httpd.conf files. Two for Apache 1.3.x and two for Apache 2.0.x, as each has two versions of PHP. Since it doesn't matter which one we take from, just copy the four httpd.conf files that reference CFMX6.1 in their file names.<!--adsense--></p>
<p>Now, simply remove the 'Copy of ' and 'CFMX<em>x</em>.<em>y</em>' from the four file names. You'll end up with the following.</p>
<ul>
<li>httpd_Apache1.3_PHP4.conf</li>
<li>httpd_Apache1.3_PHP5.conf</li>
<li>httpd_Apache2.0_PHP4.conf</li>
<li>httpd_Apache2.0_PHP5.conf </li>
</ul>
<p>There's just a couple of things to remove from each of these conf files. The following block will need to be removed from the Apache 1.3.x files.</p>
<blockquote>
<p># JRun Settings<br />LoadModule jrun_module "C:/CFusionMX/runtime/lib/wsconfig/1/mod_jrun.so"<br />&lt;IfModule mod_jrun.c&gt;<br />JRunConfig Verbose false<br />JRunConfig Apialloc false<br />JRunConfig Ssl false<br />JRunConfig Ignoresuffixmap false<br />JRunConfig Serverstore "C:/CFusionMX/runtime/lib/wsconfig/1/jrunserver.store"<br />JRunConfig Bootstrap 127.0.0.1:51010<br />#JRunConfig Errorurl &lt;optionally redirect to this URL on errors&gt;<br />AddHandler jrun-handler .jsp .jws .cfm .cfml .cfc<br />&lt;/IfModule&gt;</p>
</blockquote>
<p>And this block will need to be removed from the Apache 2.0.x files.</p>
<blockquote>
<p># JRun Settings<br />LoadModule jrun_module "C:/CFusionMX/runtime/lib/wsconfig/2/mod_jrun20.so"<br />&lt;IfModule mod_jrun20.c&gt;<br />JRunConfig Verbose false<br />JRunConfig Apialloc false<br />JRunConfig Ssl false<br />JRunConfig Ignoresuffixmap false<br />JRunConfig Serverstore "C:/CFusionMX/runtime/lib/wsconfig/2/jrunserver.store"<br />JRunConfig Bootstrap 127.0.0.1:51010<br />#JRunConfig Errorurl &lt;optionally redirect to this URL on errors&gt;<br />AddHandler jrun-handler .jsp .jws .cfm .cfml .cfc<br />&lt;/IfModule&gt;</p>
</blockquote>
<p>Finally, make sure 'index.cfm index.cfml' is removed from the DirectoryIndex lines in each file.</p>
<p>By allowing our Apache 2.0.x server, and Apache 1.3.x server, to run without checking for ColdFusion MX, we can keep it running quick, even if we decide not to start any versions of ColdFusion MX.</p>
<p>The only thing we have left is hooking up MySQL and PostgreSQL and creating batch files to use these httpd.conf and php.ini files to get the server we want up and running.</p>
<p>So, let the hardest part begin.</p>
<h3>Connecting to MySQL and PostgreSQL</h3>
<p>Amazingly enough, as long as you already setup MySQL and PostgreSQL for Apache 1.3.x, you're all set to begin using MySQL and PostgreSQL for both ColdFusion MX 6.1, ColdFusion MX 7.0, PHP 4, and PHP 5. This is because ColdFusion MX is handling the SQL requests via the datasources, and PHP is likewise handling it's own requests (via the php.ini file).</p>
<p>Feel free to test this using the PHP files I detailed before (<a href="/words/post/Installing-MySQL-and-phpMyAdmin-on-a-local-Windows-based2c-Apache2c-server.aspx">check MySQL connection in PHP</a> | <a href="/words/post/Installing-PostgreSQL-on-a-local-Windows-based2c-Apache2c-server.aspx">check PostgreSQL connection in PHP</a>) or just using the ColdFusion MX Administrator to check all datasources.</p>
<h3>Coming in Part 4 ...</h3>
<p>In Part 4, I'll be going over how to create the batch files that we'll need to work with the httpd.conf and php.ini files that we've created. While I could detail it here, better to just put it in it's own article/post, as that makes things much easier (if not for you, then at least for me ;)).</p>
<p><a href="/local-apache-server/">View all of the steps to creating a local Web server, for development.</a></p>
