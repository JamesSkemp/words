+++
title = "Dual-installing PHP: Running PHP 5 and 4 on the same local, Windows-based, Apache, server"
summary = "In previous guides, we installed PHP 4.4.2 and later moved our installation to a different folder. This time, we'll be installing the current release of PHP 5 (5.1.4) so that we can still switch back to PHP 4.4.2 if we'd like."
draft = false
comments = true
date = "2006-07-18T20:34:00-05:00"
modified = "2009-11-07T21:11:45-06:00"
slug = "Dual-installing-PHP-Running-PHP-5-and-4-on-the-same-local-Windows-based-Apache-server"
blogengine = "22f42ac1-7c49-483f-b4a8-5c9d98b13d7e"
categories = ["tutorials / guides"]
tags = ["php", "apache"]
+++

<p>In previous guides, we <a href="http://strivinglife.com/words/post/Installing-PHP-on-a-local-Windows-based-Apache-server.aspx">installed PHP 4.4.2</a> and later <a href="http://strivinglife.com/words/post/Moving-the-location-of-PHP-on-your-hard-drive.aspx">moved our installation to a different folder</a>. This time, we'll be installing the current release of PHP 5 (5.1.4) so that we can still switch back to PHP 4.4.2 if we'd like.</p>
<h3>Downloading PHP 5.x</h3>
<p>The current version of PHP 5.x is 5.1.4, so we'll begin by downloading that from PHP.net. We&rsquo;ll want to download the (Windows Binaries) zip file, even though it is significantly larger in size than the installer (the zip file is almost 9 MB, compared to less than 3 MB for the executable), but allows us a deal more flexibility.</p>
<h3>Installing</h3>
<p>Once you've downloaded the zip file, extract the contents to a folder called c:\php5\. Once done, php.exe will have the full path of c:\php5\php.exe.</p>
<p>As with the PHP 4 installation, the install.txt file will detail how to install PHP 5. However, since you're using this guide, you shouldn't need to consult it. As with our PHP 4 installation, we'll be installing PHP 5 as a module, instead of as CGI binary (again, you can do this instead, if you so desire).</p>
<p>Start by backing up all of your httpd.conf files, in C:\Program Files\Apache Group\Apache\conf (if using the defaults). Since these work, add '_php4' to each of these backups.</p>
<p>For example, I have three httpd.conf files that I'm backing up; httpd.conf, httpd_CFMX6.1.conf, and httpd_CFMX7.01.conf. I'll be creating copies of each of these files, and calling them httpd_php4.conf, httpd_php4_CFMX6.1.conf, and httpd_php4_CFMX7.01.conf. This way I know that these use PHP 4. Once we modify the httpd.conf file(s) below, it may be a good idea to create backups and then call name them with '_php5'.</p>
<p>For the next steps, I'll be assuming that you've already installed PHP 4.</p>
<p>Begin by doing a search for</p>
<blockquote>
<p>LoadModule php4_module "c:/php4/php4apache.dll"</p>
</blockquote>
<p>Change this to</p>
<blockquote>
<p>LoadModule php5_module "c:/php5/php5apache.dll"</p>
</blockquote>
<p>Now do a search for</p>
<blockquote>
<p>AddModule mod_php4.c</p>
</blockquote>
<p>And change this to</p>
<blockquote>
<p>AddModule mod_php5.c</p>
</blockquote>
<p>Save httpd.conf. Next, head over to c:\windows\ and find the php.ini file. Rename this file to php_php4.ini (to keep with our naming standard above). We're renaming the original file, in this case, because we actually want to copy the file php.ini-dist from the c:\php5 folder to the c:\windows folder, and rename it to simply php.ini.</p>
<p>Once you've renamed the file, open it up. Once the file has been opened, do a search for doc_root and change it from</p>
<blockquote>
<p>doc_root =</p>
</blockquote>
<p>to</p>
<blockquote>
<p>doc_root = "c:\home"</p>
</blockquote>
<p>Or where your document root is for Apache.</p>
<p>Now do a search for the following line</p>
<blockquote>
<p>;session.save_path = "/tmp"</p>
</blockquote>
<p>And change that to your temporary PHP folder (in my previous guide, it ended up being</p>
<blockquote>
<p>session.save_path = "c:/windows/temp/temp_php"</p>
</blockquote>
<p>Make sure you remove the semi-colon from the beginning of the line to uncomment this line. Make sure that this folder exists.</p>
<p>Finally, search for the following line</p>
<blockquote>
<p>extension_dir = "./"</p>
</blockquote>
<p>and change it to</p>
<blockquote>
<p>extension_dir = "c:\php5\ext\"</p>
</blockquote>
<p>If you've installed <a href="http://strivinglife.com/words/post/Installing-MySQL-and-phpMyAdmin-on-a-local-Windows-based-Apache-server.aspx">MySQL</a> (this page also contains a script to check the connection), you can enable access by uncommenting the following line</p>
<blockquote>
<p>;extension=php_mysql.dll</p>
</blockquote>
<p>You'll also want to copy libmysql.dll from c:\php5\ to c:\windows\system32\.</p>
<p>If you've installed <a href="http://strivinglife.com/words/post/Installing-PostgreSQL-on-a-local-Windows-based-Apache-server.aspx">PostgreSQL</a> (this page also contains a script to check the connection), you can enable access by uncommenting the following line</p>
<blockquote>
<p>;extension=php_pgsql.dll</p>
</blockquote>
<p>Save your changes to the php.ini file, and close out of the file. You may want to create a copy of this file as php_php5.ini - this way you have both a php4 and php5 file.</p>
<p>Finally, in c:\php5\, copy php5ts.dll into the c:\windows\ folder.</p>
<p>Restart Apache, and assuming it starts, hit the phpinfo.php page (which contains the following lines).</p>
<pre class="code"><code class="php">&lt;?php
phpinfo();
?&gt;</code></pre>
<p>If you visit this page, you should be told that you're running PHP 5.1.4. You may notice that Zend Optimizer is no longer listed as being installed.</p>
<p>If you made a copy of the php.ini file for PHP 4 (php_php4.ini is what I recommended), then you can copy the last four lines from this file, which are as follows (<span style="text-decoration: line-through;">I'm including the new line as a line</span> the new line is absent from the code below, but it sits immediately before the first line below)</p>
<pre class="code"><code class="text">[Zend]
zend_extension_manager.optimizer_ts="C:\Program Files\Zend\ZendOptimizer-3.0.1\lib\Optimizer-3.0.1"
zend_extension_ts="C:\Program Files\Zend\ZendOptimizer-3.0.1\lib\ZendExtensionManager.dll"</code></pre>
<p>Paste these lines at the end of your php.ini (and php_php5.ini file, if necessary) file. Restart Apache and Optimizer 3.0.1 should display on the phpinfo() page.</p>
<p>Until then, verify that you have backups of the files that we modified in this guide; httpd.conf and php.ini. In a later guide, or update, I'll detail how to setup a batch file to automatically move the necessary files to switch from PHP 4 to PHP 5, and vice versa (again, for updates, leave a comment).</p>
<p>To manually change from PHP 4 to PHP 5, and vice versa, simply delete the existing httpd.conf file. Next, make a copy of the httpd_php4.conf or httpd_php5.conf file, and rename it to httpd.conf. Do the same thing for the php.ini file. Finally, restart Apache. As long as you keep your backup copies, you can switch back and forth fairly easily. Again, a future batch file will make this much easier, by allowing one file to do all the work for you.</p>
<h3>The batch files</h3>
<p>Below is code for two batch files. Lines beginning with === should not be entered into the batch file - they merely contain the name of the file. Note that you may need to make some modifications, based upon where you installed programs and files.</p>
<p>c:\home\zblank.txt is simply a blank file. Including blank lines, each batch file contains 12 lines (2 of which are blank).</p>
<h4>===_start php4.bat</h4>
<pre class="code"><code class="powershell">net stop "Apache"
DEL "c:\home\php4 is ready.txt"
DEL "c:\home\php5 is ready.txt"
COPY "c:\windows\php.ini" "c:\windows\php_backup.ini"
COPY "c:\windows\php_php4.ini" "c:\windows\php.ini"

COPY "C:\Program Files\Apache Group\Apache\conf\httpd_php4.conf" "C:\Program Files\Apache Group\Apache\conf\httpd.conf"
COPY "C:\Program Files\Apache Group\Apache\conf\httpd_php4_CFMX6.1.conf" "C:\Program Files\Apache Group\Apache\conf\httpd_CFMX6.1.conf"
COPY "C:\Program Files\Apache Group\Apache\conf\httpd_php4_CFMX7.01.conf" "C:\Program Files\Apache Group\Apache\conf\httpd_CFMX7.01.conf"

net start "Apache"
COPY "C:\home\zblank.txt" "C:\home\php4 is ready.txt"</code></pre>
<h4>===_start php5.bat</h4>
<pre class="code"><code class="powershell">net stop "Apache"
DEL "c:\home\php4 is ready.txt"
DEL "c:\home\php5 is ready.txt"
COPY "c:\windows\php.ini" "c:\windows\php_backup.ini"
COPY "c:\windows\php_php5.ini" "c:\windows\php.ini"

COPY "C:\Program Files\Apache Group\Apache\conf\httpd_php5.conf" "C:\Program Files\Apache Group\Apache\conf\httpd.conf"
COPY "C:\Program Files\Apache Group\Apache\conf\httpd_php5_CFMX6.1.conf" "C:\Program Files\Apache Group\Apache\conf\httpd_CFMX6.1.conf"
COPY "C:\Program Files\Apache Group\Apache\conf\httpd_php5_CFMX7.01.conf" "C:\Program Files\Apache Group\Apache\conf\httpd_CFMX7.01.conf"

net start "Apache"
COPY "C:\home\zblank.txt" "C:\home\php5 is ready.txt"</code></pre>
<p><a href="http://strivinglife.com/local-apache-server/">View all of the steps to creating a local Web server, for development.</a></p>
