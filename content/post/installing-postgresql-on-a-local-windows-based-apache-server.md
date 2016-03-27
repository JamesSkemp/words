+++
title = "Installing PostgreSQL on a local Windows-based, Apache, server"
description = "While we've already setup MySQL, another popular SQL server is PostgreSQL. Like MySQL, PostgreSQL is absolutely free, and will allow us to create databases on our local server."
draft = false
comments = true
date = "2006-03-15T23:32:00-06:00"
modified = "2009-10-15T07:39:20-05:00"
slug = "Installing-PostgreSQL-on-a-local-Windows-based-Apache-server"
blogengine = "e69e3ec0-8075-4202-aafb-1dfdd702f790"
categories = ["software", "tutorials / guides"]
tags = ["apache", "php", "postgresql"]
+++

<p>While we've already <a href="/words/post/Installing-MySQL-and-phpMyAdmin-on-a-local-Windows-based%2c-Apache%2c-server.aspx">setup MySQL</a>, another popular SQL server is PostgreSQL. Like MySQL, PostgreSQL is absolutely free, and will allow us to create databases on our local server.</p>
<h3>Downloading PostgreSQL</h3>
<p>We'll be downloading the most current version of PostgreSQL, which is 8.1.3 at the time of this writing. You can download the installation file from <a rel="external" href="http://www.postgresql.org/ftp/win32">http://www.postgresql.org/ftp/win32</a>. We'll want to download the regular zip file, called postgresql-8.1.3-1.zip, and weighing in at 21 MB. You'll want to save this to the same folder you save your other installers &ndash; c:\home\downloads\ if you've been following along.</p>
<div class="note">
<p>This guide is also applicable to version PostgreSQL 8.2.3 (postgresql-8.2.3-1.zip), with minor changes (noted below).</p>
</div>
<p>Once the download has finished, extract the contents to a temporary folder.</p>
<h3>Install PostgreSQL</h3>
<p>Now that you've downloaded the zip and extracted it, run postgresql-8.1.msi, not postgresql-8.1-int.msi.</p>
<p>You'll be prompted to select a language for the <em>installation</em>. I chose English. Also, you can either check Write detailed installation log to postgresql-8.1.log in the current directory, or not. If you do, a log of the installation will be saved to the temporary folder. Click Next.</p>
<p>Read through the Installation Notes, and press Next. For Installation options, leave everything as default, and select Next.</p>
<p>For Service configuration, Install as a service. Leave Service name the default of PostgreSQL Database Server 8.1, and Account name the default of postgres.</p>
<div class="note">
<p>In PostgreSQL 8.2.3, the Service name will be version 8.2. This is so that you can run more than one version at once.</p>
</div>
<p>Account domain will default as the name of your computer, and we can leave this as is, but make a note of it. Mine was PAVA620N.</p>
<p>Now, fill in Account password and Verify password, or leave these empty to have the installer create a (very long) password. Make sure you make a note of this password.</p>
<p>When you click through, a pop-up will say that the user was not found. Click Yes to create an account. If your password is weak, it will say so and offer to create a password for you. Again, this will be a very long password, so if you want to change your password, select No and press Back to try a new password.</p>
<div class="note">
<p>If you don't recall your password, you can change it by going to the Windows command line and typing the following, where <strong>postgres</strong> is the username and <strong>password</strong> is the new password.</p>
<p>net user postgres password</p>
</div>
<p>On the next screen, Initialise database cluster, keep the defaults, but change Encoding to UTF-8. Make a note that the Port number is 5432. Keep the default Superuser name of postgres, but create a unique password &ndash; not the one you used previously.</p>
<p>If you've installed Perl, then you'll be able to check a couple of boxes. Pick the PL/pgsql and PL/perl checkboxes. Otherwise, just pick PL/pgsql. Click Next.</p>
<p>For Enable contrib modules, only pick the default of Admin81. Click Next.</p>
<div class="note">
<p>In PostgreSQL 8.2.3, the default is Adminpack.</p>
</div>
<p>At this point, you'll be "Ready to install." Click Next to install, and watch the Installation proceed.</p>
<p>Once the installation has finished, you can choose to subscribe to pgsql-announce. Otherwise, click Finish.</p>
<h3>Verify installation of PostgreSQL</h3>
<p>First, delete the temporary folder, but keep the log file, if you'd like, and if you opted to create one.</p>
<p>Next, go to Start &gt; All Programs &gt; PostgreSQL 8.1 &gt; pgAdmin III Copy this shortcut to where you store your other shortcuts, and then run this program.</p>
<p>If we check Help &gt; About, we'll see the version of pgAdmin. Mine is Version 1.4.1. If we need to, we can upgrade this program outside of PostgreSQL.</p>
<div class="note">
<p>In PostgreSQL 8.2.3, pgAdmin 1.6.2 is installed.</p>
</div>
<p>Now, right click on PostgreSQL Database Server 8.1 and select Connect. Enter the second password from above, and connect. Once you've connected, expand the tree as necessary. To disconnect, select Disconnect after right clicking on PostgreSQL Database Server 8.1.</p>
<h3>Setting up PHP to connect with PostgreSQL</h3>
<p>Open php.ini and do a search for pgsql. Uncomment "extension=php_pgsql.dll", by removing the ;, and then save and close php.ini. Now, restart Apache via Services.</p>
<p>If you go to <a rel="nofollow" href="http://localhost/phpinfo.php">http://localhost/phpinfo.php</a> and search for pgsql, you should see some information on your installation.</p>
<p>Now, we'll be testing the connection by creating a very small php file. Create a new file called postgresqlconnection.php, with the below text. Make sure you change PASSWORD as necessary.</p>
<pre class="code"><code class="php">&lt;?php
$user="postgres";
$password="PASSWORD";

$connection = pg_connect("host=localhost user=$user password=$password") or die("Connection failed." . pg_last_error());
echo "Connected to PostgreSQL.";
pg_close($connection);
?&gt;</code></pre>
<p>Save this to your default Web server directory &ndash; c:\home\. Now visit <a rel="nofollow" href="http://localhost/postgresqlconnection.php">http://localhost/postgresqlconnection.php</a>.</p>
<p>Congrats, you should see "Connected to PostgreSQL." and have now setup PostgreSQL to work with PHP.</p>
<p><a href="/local-apache-server/">View all of the steps to creating a local Web server, for development.</a></p>
