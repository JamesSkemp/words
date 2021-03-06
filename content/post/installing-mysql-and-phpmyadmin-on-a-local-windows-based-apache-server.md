+++
title = "Installing MySQL and phpMyAdmin on a local Windows-based, Apache, server"
description = "MySQL will allow us to create databases on our local server. With PHP, this will allow us to install applications like the free WordPress, as well as number of open source content management systems, not to mention bulletin boards and the like. phpMyAdmin will allow us to administer MySQL quite easily."
draft = false
comments = true
date = "2006-02-24T23:31:00-06:00"
modified = "2007-09-06T22:02:47-05:00"
slug = "Installing-MySQL-and-phpMyAdmin-on-a-local-Windows-based-Apache-server"
blogengine = "06a0a6bc-146f-4257-9f89-4954d617a952"
categories = ["software", "tutorials / guides"]
tags = ["mysql", "phpmyadmin"]
+++

<div class="note">
<p>
<em>Note: This guide should work equally well for phpMyAdmin 2.8.1 and above.  For a guide on upgrading this 2.7.0-pl2 install, see <a href="http://strivinglife.com/words/post/Upgrading-phpMyAdmin-(270-pl2-to-281)-on-a-local%2c-Windows-based%2c-Apache-server.aspx">Upgrading phpMyAdmin (2.7.0-pl2 to 2.8.1) on a local, Windows-based, Apache server</a>.</em>
</p>
</div>
<p>
MySQL will allow us to create databases on our local server. With PHP, this will allow us to install applications like the free WordPress, as well as number of open source content management systems, not to mention bulletin boards and the like. phpMyAdmin will allow us to administer MySQL quite easily.
</p>
<p>
<strong>MySQL</strong>
</p>
<p>
While MySQL 5.0 is the recommend version, we&#39;ll be downloading the most current 4.x release &ndash; at the time of this writing &ndash; 4.1.18. Head over to <a href="http://dev.mysql.com/downloads/">http://dev.mysql.com/downloads/</a>, and under MySQL Community Edition, you&#39;ll find an Older Releases heading. Download the Windows Essentials (x86), at a whopping 16.5 MB.
</p>
<p>
Once the download has completed, open the MSI file. When you&#39;re prompted on what kind of setup you&#39;d like to use, select Custom. Use the default options, however, and note where MySQL will be installed to. Continue along until you&#39;ve installed MySQL. Once you have, you&#39;ll be prompted to sign-up to MySQL.com, login, or skip sign-up. Honestly, I recommend you go ahead and sign-up for an account, since there&#39;s no reason not to. However, you can simply skip this step if you&#39;d like to. Finally, before you Finish, you&#39;ll want to verify that the checkbox next to &quot;Configure the MySQL Server now&quot; is checked (it should be).
</p>
<p>
On the Configuration Wizard, select Detailed Configuration. Then Developer Machine. Then Multifunctional Database. For InnoDB Tablespace Settings, we&#39;ll leave things as they are (Installation Path). We&#39;ll leave the next setting as it is, since we&#39;re only interested in development (Decision Support (DSS)/OLAP). We&#39;ll also leave the next setting as it is &ndash; Port Number 3306. We&#39;ll change MySQL character set to the Best Support For Multilingualism option.
</p>
<p>
Since we want MySQL to show up in the Service control panel, leave the first option checked in the next window. We&#39;ll also want to check the second box, in case we want to troubleshoot our installation using the command line.
</p>
<p>
Finally, create a password for the root account. Make sure you write this password down somewhere safe. Keep the checkbox unchecked, since we only want our machine to be able to access the root. Now, hit Execute and Finish once it&#39;s started.
</p>
<p>
If we now open up the Services control panel, we&#39;ll find a MySQL item, which, like Apache, can be started, restarted, and stopped. While you&#39;re in the Services panel, restart Apache.
</p>
<p>
<strong>phpMyAdmin</strong>
</p>
<p>
For phpMyAdmin, we&#39;ll be happy with the latest stable release. As of the time of this writing, that&#39;s phpMyAdmin 2.7.0-pl2. Download the zip version, which is about 3.5 MB.
</p>
<p>
Once the download has completed, unzip the contents of this file to our main server directory &ndash; C:\home\. Ultimately, it&#39;s your call whether you keep the folder with the version information, or whether you rename the folder to just phpMyAdmin.
</p>
<p>
Once you&#39;ve unzipped the contents, we&#39;ll want to create an easy way to access the folder. To do this, we&#39;ll setup a subdomain under localhost. While you could call the folder up using <a href="http://localhost/phpMyAdmin-2.7.0-pl2/">http://localhost/phpMyAdmin-2.7.0-pl2/</a>, or whatever you named the folder, if we use a VirtualHost entry, we&#39;ll make things easier in the future (if we want to upgrade, we can continue to have older versions available when we have newer versions). Now, setup <a href="http://phpMyAdmin.localhost/">http://phpMyAdmin.localhost/</a>. Once you&#39;ve finished, or if you need help, come back to this guide &ndash; we&#39;ll walk through this in the next paragraph.
</p>
<p>
First, we&#39;ll open up the httpd.conf file. Since we&#39;ve already got at least two other instances of how we&#39;ll need to set this up, simply copy the last one. Next, change the values accordingly. For ease, I did the below.
</p>
<blockquote>
	<p>
	&lt;VirtualHost 127.0.0.4&gt;<br />
	ServerName phpMyAdmin.localhost<br />
	DocumentRoot C:\home\phpMyAdmin-2.7.0-pl2<br />
	ErrorLog logs/phpMyAdmin-error.log<br />
	TransferLog logs/phpMyAdmin-access.log<br />
	&lt;/VirtualHost&gt;
	</p>
</blockquote>
<p>
Save and close httpd.conf. Next, open the hosts file (in the C:\WINDOWS\system32\drivers\etc\ folder) and insert the appropriate line at the end of the file.
</p>
<blockquote>
	<p>
	127.0.0.4	phpMyAdmin.localhost
	</p>
</blockquote>
<p>
Again, save and close this file. Finally, restart Apache, and head over to <a href="http://phpMyAdmin.localhost/">http://phpMyAdmin.localhost/</a>. The first thing you&#39;ll notice is that you get an error message. If we look, we see this is because the password isn&#39;t correct. If we go looking for the config.inc.php file, however, we won&#39;t be able to find it in our phpMyAdmin directory. If we look at the documentation, we&#39;ll find that we&#39;ll have to create one.
</p>
<p>
So, copy the config.default.php file and open it in WordPad (as you may lose formatting in Notepad). You can open WordPad easily by pressing the Window + R key, and typing &#39;write&#39; (no quotes) in the prompt. Now look for a line that starts with $cfg[&#39;Servers&#39;][$i][&#39;password&#39;], and enter the root password here. Now, save this file, and close out of WordPad. Finally, rename the file (Copy of config.default.php) to config.inc.php.
</p>
<p>
If we were to try loading <a href="http://phpMyAdmin.localhost/">http://phpMyAdmin.localhost/</a> again, we&#39;d still have connection problems. Unfortunately, this is because the password we entered in the installer isn&#39;t encoded quite correctly, for whatever reason. This means we&#39;ll have to do some extra work, at the command line.
</p>
<p>
Now, type Windows + R once again, and type &#39;cmd&#39; (no quotes) to bring up the command line interface. Now, type
</p>
<blockquote>
	<p>
	<strong>mysql -u root -p</strong>
	</p>
</blockquote>
<p>
at the command line. What we&#39;ll be doing is changing the password that we just setup. We need to do this for a number of reasons, unfortunately. When it prompts you for a password, type the password you used at setup, and above, once again. Next, type the following, where your_password is your password.
</p>
<blockquote>
	<p>
	<strong>UPDATE mysql.user SET Password = OLD_PASSWORD(&#39;your_password&#39;) WHERE Host = &#39;localhost&#39; AND User = &#39;root&#39;;</strong>
	</p>
</blockquote>
<p>
Once you run this command (by pressing enter) you&#39;ll have updated your password. Type exit, press enter, and type exit and press enter once again (the first time to exit out of MySQL, the second time to exit out of the command prompt). Now, restart MySQL using the Services control panel.
</p>
<p>
If we load <a href="http://phpmyadmin.localhost/">http://phpMyAdmin.localhost/</a> again, we&#39;ll now be logged in. However, we&#39;ll notice that the images are not loading correctly. So, let&#39;s open up config.inc.php once again, and change some values.
</p>
<p>
First, find the line that begins with $cfg[&#39;PmaAbsoluteUri&#39;] and change it&#39;s value to <a href="http://phpMyAdmin.localhost/">http://phpMyAdmin.localhost/</a> (include the trailing slash). Next, look for the line that starts with $cfg[&#39;Servers&#39;][$i][&#39;auth_type&#39;], and change config to http. Save the file and reload <a href="http://phpMyAdmin.localhost/">http://phpMyAdmin.localhost/</a>. Once we do that, we&#39;ll be prompted for a username (root) and a password (whatever your password happens to be).
</p>
<p>
Finally, open Notepad and insert the following text. Make sure you change your_password accordingly.
</p>
<blockquote>
	<p>
	&lt;?php<br />
	$user=&quot;root&quot;;<br />
	$password=&quot;<strong>your_password</strong>&quot;;<br />
	mysql_connect(localhost,$user,$password) or die (&quot;Can&#39;t connect to MySQL.&quot;);<br />
	echo &quot;Connected to MySQL.&quot;;<br />
	mysql_close();<br />
	?&gt;
	</p>
</blockquote>
<p>
Save the file as mysqlconnection.php, in the C:\home\ folder. Now, load <a href="http://localhost/mysqlconnection.php">http://localhost/mysqlconnection.php</a>. If you see &quot;Connected to MySQL.&quot;, then PHP can now access MySQL. Otherwise, you&#39;ll see &quot;Can&#39;t connect to MySQL.&quot;, and you&#39;ll need to review the above once again. If you want, you can Stop MySQL via the Services panel and load this page to see what happens.
</p>
<p>
One last thing we&#39;ll need to clear up is a mbstring error in phpMyAdmin. To fix this, we&#39;ll open up the php.ini file, which is at c:\windows\php.ini (or you may have a shortcut stashed away somewhere). Do a search for &quot;php_mbstring.dll&quot; (without the quotes) and remove the &#39;;&#39; on this line. Save this file and close it. Now, restart Apache. Once you do so, and reload <a href="http://phpMyAdmin.localhost/">http://phpMyAdmin.localhost</a>, you&#39;ll notice that the error is gone.
</p>
<p>
Now that you&#39;ve setup MySQL and phpMyAdmin, you may want to head over to Analog and add the new log file. You&#39;ll notice some new status codes in the Report.html, if you do so. However, we&#39;ll be dumping Analog pretty soon, so don&#39;t worry if you don&#39;t.
</p>
<p>
Next time, we&#39;ll be installing MySQL Administrator, so we can setup some additional users and databases easily. For now, stay clear of using the root user to do much of anything. We&#39;ll create some user accounts with limited access, next time.
</p>
<p>
<a href="http://strivinglife.com/local-apache-server/">View all of the steps to creating a local Web server, for development.</a>
</p>

