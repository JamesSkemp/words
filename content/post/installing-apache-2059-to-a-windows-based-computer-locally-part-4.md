+++
title = "Installing Apache 2.0.59 to a Windows-based computer, locally: Part 4"
description = "In the last part of the Apache 2.0.59 installation guide, we cover creating batch files to switch between various instances of Apache, PHP, and ColdFusion. In a later guide we'll clean this process up considerably, but until then ..."
draft = false
comments = true
date = "2006-08-28T21:45:00-05:00"
modified = "2009-12-20T18:24:29-06:00"
slug = "Installing-Apache-2059-to-a-Windows-based-computer-locally-Part-4"
blogengine = "ca253b85-575c-4f0c-82f0-93bfa9d2676f"
categories = ["software", "tutorials / guides"]
tags = ["apache", "coldfusion", "php"]
+++

<p>In the previous three parts of this guide, we setup Apache 2.0.59 and then created the necessary connections to use ActivePerl, mod_perl, ColdFusion MX 6.1, ColdFusion MX 7.0.2, PHP 4.4.2, PHP 5.1.4, MySQL 4.1.18, and PostgreSQL 8.1.3. This time, we're going to bring everything together by creating a number of batch files to fairly easily switch between various Web server setups.</p>
<h3>What is a batch file?</h3>
<p>A batch file is basically a way to run a number of Windows prompts at once. In this particular case, we'll be using it to stop the Web server, copy, rename, and delete, files, and then start the necessary services up once again.<!--adsense--></p>
<p>While we could do this manually, having just one, correctly setup, file to run is much easier, and much more logical.</p>
<h3>Assumptions</h3>
<p>I'm going to assume that;</p>
<ol>
<li>Your Web root folder is c:\home\.</li>
<li>If you installed PHP, you placed the php.ini file in the c:\windows\ folder. </li>
<li>If you installed Apache 1.3.x, you installed it to C:\Program Files\Apache Group\Apache\ </li>
<li>If you installed Apache 2.0.x, you installed it to C:\Program Files\Apache Group\Apache2\ </li>
<li>If you installed PHP, you have one working httpd.conf file for each version of PHP you installed, times each version of Apache you have installed. So, if you have two versions of PHP and one version of Apache, you should have two httpd.conf files. One for Apache with PHP 4, one for Apache with PHP 5. </li>
<li>If you installed PHP, you have one working php.ini file for each version of PHP you installed. </li>
<li>If you installed ColdFusion MX, you have one working httpd.conf file for each version of ColdFusion MX you installed, times each version of PHP you installed, times each version of Apache you installed, plus the number of ColdFusion MX versions you installed. So, if you installed two version of ColdFusion MX, one version of PHP, and one version of PHP, that's [(2 * 1 * 1) + 2] </li>
<li>Each of these httpd.conf files is in c:\home\configuration\. Likewise, each php.ini file necessary is in this same folder. There is also a blank text file called zblank.txt in this folder. </li>
</ol>
<h3>Creating the necessary batch files</h3>
<p>I'm going to go through a batch file nice and slow, working through each line. This batch file will stop Apache 1.3.x. It will then prepare Apache 1.3.x to run PHP 4. We'll then create a text file that tells us that Apache 1.3.x, running PHP 4, is started.</p>
<p>First, the batch file.</p>
<pre class="code"><code class="powershell">net stop "ColdFusion MX Application Server"
net stop "ColdFusion MX 7 Application Server"
net stop "Apache"
net stop "Apache2"
DEL "c:\home\zApache1.3_CFMX6.1_PHP4 is ready.txt"
DEL "c:\home\zApache1.3_CFMX7.0_PHP4 is ready.txt"
DEL "c:\home\zApache1.3_CFMX6.1_PHP5 is ready.txt"
DEL "c:\home\zApache1.3_CFMX7.0_PHP5 is ready.txt"
DEL "c:\home\zApache2.0_CFMX6.1_PHP4 is ready.txt"
DEL "c:\home\zApache2.0_CFMX7.0_PHP4 is ready.txt"
DEL "c:\home\zApache2.0_CFMX6.1_PHP5 is ready.txt"
DEL "c:\home\zApache2.0_CFMX7.0_PHP5 is ready.txt"
DEL "c:\home\zApache1.3_PHP4 is ready.txt"
DEL "c:\home\zApache1.3_PHP5 is ready.txt"
DEL "c:\home\zApache2.0_PHP4 is ready.txt"
DEL "c:\home\zApache2.0_PHP5 is ready.txt"
COPY "C:\Program Files\Apache Group\Apache\conf\httpd.conf" "C:\Program Files\Apache Group\Apache\conf\httpd_backup.conf"
COPY "c:\home\configuration\httpd_Apache1.3_PHP4.conf" "C:\Program Files\Apache Group\Apache\conf\httpd.conf"
COPY "C:\windows\php.ini" "c:\windows\php_backup.ini"
COPY "C:\home\configuration\php_Apache_PHP4.ini" "c:\windows\php.ini"
net start "Apache"
COPY "C:\home\configuration\zblank.txt" "C:\home\zApache1.3_PHP4 is ready.txt"</code></pre>
<p>Start Notepad, and we'll walk through this beast of a batch file.</p>
<pre class="code"><code class="powershell">net stop "ColdFusion MX Application Server"
net stop "ColdFusion MX 7 Application Server"
net stop "Apache"
net stop "Apache2"</code></pre>
<p>These four lines stop ColdFusion MX 6.1, ColdFusion MX 7, Apache 1.3.x, and Apache 2.0.x (in order). Of course, if you have not installed one of these, you can simply remove those lines. However, if you have installed any of these, you should keep these lines in place. After all, you never know what services may be running.</p>
<pre class="code"><code class="powershell">DEL "c:\home\zApache1.3_CFMX6.1_PHP4 is ready.txt"
DEL "c:\home\zApache1.3_CFMX7.0_PHP4 is ready.txt"
DEL "c:\home\zApache1.3_CFMX6.1_PHP5 is ready.txt"
DEL "c:\home\zApache1.3_CFMX7.0_PHP5 is ready.txt"
DEL "c:\home\zApache2.0_CFMX6.1_PHP4 is ready.txt"
DEL "c:\home\zApache2.0_CFMX7.0_PHP4 is ready.txt"
DEL "c:\home\zApache2.0_CFMX6.1_PHP5 is ready.txt"
DEL "c:\home\zApache2.0_CFMX7.0_PHP5 is ready.txt"
DEL "c:\home\zApache1.3_PHP4 is ready.txt"
DEL "c:\home\zApache1.3_PHP5 is ready.txt"
DEL "c:\home\zApache2.0_PHP4 is ready.txt"
DEL "c:\home\zApache2.0_PHP5 is ready.txt"</code></pre>
<p>These lines delete the file referenced. In this case, we're deleting every possible text file that could exist. As before, if you have not installed one of the versions of Apache, or one of the versions of PHP, or one of the versions of ColdFusion MX, you can remove those lines.</p>
<pre class="code"><code class="powershell">COPY "C:\Program Files\Apache Group\Apache\conf\httpd.conf" "C:\Program Files\Apache Group\Apache\conf\httpd_backup.conf"</code></pre>
<p>First, we create a backup of the httpd.conf file for Apache 1.3.x.</p>
<pre class="code"><code class="powershell">COPY "c:\home\configuration\httpd_Apache1.3_PHP4.conf" "C:\Program Files\Apache Group\Apache\conf\httpd.conf"</code></pre>
<p>Second, we make a copy of the working httpd.conf file that runs Apache 1.3.x with PHP 4.</p>
<pre class="code"><code class="powershell">COPY "C:\windows\php.ini" "c:\windows\php_backup.ini"
COPY "C:\home\configuration\php_Apache_PHP4.ini" "c:\windows\php.ini"</code></pre>
<p>As with the httpd.conf file, we create a backup of the php.ini file, and then copy a working PHP 4 file into the correct directory.</p>
<pre class="code"><code class="powershell">net start "Apache"</code></pre>
<p>Next, we start the Apache 1.3.x service.</p>
<pre class="code"><code class="powershell">COPY "C:\home\configuration\zblank.txt" "C:\home\zApache1.3_PHP4 is ready.txt"</code></pre>
<p>Finally, we copy the blank text file and rename the copy so that we know which configuration is running.</p>
<p>Save the Notepad file as Apache1.3_PHP4.bat where ever makes the most sense to you. I put it in the configuration folder, but you could also put it in the c:\home\ folder, or another folder entirely (or on your Desktop).</p>
<h3>Moving forward</h3>
<p>I've created twelve (12) batch files in a matter similar to the above, and zipped them up for download. Feel free to modify them as necessary, for your own use.</p>
<p>Keep in mind that these are very basic batch files. It's possible to clean these up significantly, with the full range of commands at your disposal. For now, however, this will get you going.</p>
<p>Download <a title="Batch files for switching between our servers" rel="download" href="/files/2006/08/bat_20060826.zip">bat_20060826.zip</a> for the twelve batch files. Feel free to modify as necessary to get them to work on your own system.</p>
<p><a href="http://strivinglife.net/wordpress/a-local-apache-web-server-on-a-windows-xp-computer/">View all of the steps to creating a local Web server, for development.</a></p>
