+++
title = "Setting up WordPress on a local Web server"
description = "In our previous tutorials, we setup an Apache-based Web server, on a Windows XP home computer. The Web server is also running PHP and MySQL, as well as ColdFusion MX. This time, we'll be installing WordPress onto our local Web server. This installation will require us to work with both PHP and MySQL, and we'll be able to setup any number of WordPresses after we have completed this one."
draft = false
comments = true
date = "2006-02-28T08:13:00-06:00"
slug = "Setting-up-WordPress-on-a-local-Web-server"
blogengine = "242ff272-af7e-4b08-96b6-2dda221d7e52"
categories = ["tutorials / guides"]
tags = ["wordpress", "apache", "mysql"]
+++

<div class="note">
<p>
<em>Note: This guide should work equally well for WordPress 2.0.2 and above.  For a guide on upgrading this 2.0.1 install, see <a href="http://strivinglife.net/wordpress/2006/03/11/63/upgrading-our-local-install-of-wordpress/">Upgrading (our local install of) WordPress</a>.</em>
</p>
</div>
<p>
In our previous tutorials, we setup an Apache-based Web server, on a Windows XP home computer. The Web server is also running PHP and MySQL, as well as ColdFusion MX. This time, we&#39;ll be installing WordPress onto our local Web server. This installation will require us to work with both PHP and MySQL, and we&#39;ll be able to setup any number of WordPresses after we have completed this one.
</p>
<!--more--><!--adsense-->
<p>
<strong>Downloading WordPress</strong>
</p>
<p>
First, we&#39;ll need to download the latest version of WordPress, from <a href="http://wordpress.org/download/">http://wordpress.org/download/</a>. As of this writing, that version is 2.0.1.
</p>
<p>
Once we&#39;ve downloaded WordPress, we can extract the zip file into the same folder that we downloaded the zip to (in my case, c:\home\downloads\). Now move the wordpress folder from within this folder, to c:\home\. Once you&#39;ve done this, the path to the license.txt should be something like c:\home\wordpress\.
</p>
<p>
<strong>Configuring localhost</strong>
</p>
<p>
Now that we&#39;ve extracted the WordPress installation, we&#39;ll want to point a quick URL to this folder. We&#39;ll use <a href="http://wordpress.localhost/">http://wordpress.localhost/</a> to do this.
</p>
<p>
First, open the httpd.conf file using your shortcut, or the Start menu. At the bottom of this file, we&#39;ll need to add a new VirtualDirectory for wordpress.localhost. My addition looked like the below.
</p>
<blockquote>
	<p>
	&lt;VirtualHost 127.0.0.5&gt;<br />
	ServerName wordpress.localhost<br />
	DocumentRoot c:\home\wordpress<br />
	ErrorLog logs/wordpress-error.log<br />
	TransferLog logs/wordpress-access.log<br />
	&lt;/VirtualHost&gt;
	</p>
</blockquote>
<p>
Now, save this file and close it.
</p>
<p>
Next, open the hosts file, using a shortcut, or by scrolling to it. At the end of this file, add a new entry for the VirtualDirectory we just created.
</p>
<blockquote>
	<p>
	127.0.0.5	wordpress.localhost
	</p>
</blockquote>
<p>
Again, save this file and close it.
</p>
<p>
Finally, we&#39;ll need to restart Apache in order for our change to take effect, using the Services control panel.
</p>
<p>
<strong>Configuring MySQL: Creating the WordPress user and database</strong>
</p>
<p>
Now that WordPress is extracted, and we&#39;ve setup <a href="http://wordpress.localhost/">http://wordpress.localhost/</a>, we&#39;ll need to create a MySQL user account and database for WordPress to use. First, start up MySQL Administrator. Type in the root password, and click on User Administration. Press the New User button. Fill in the MySQL User and Password fields, and Apply changes. The user name I used was simply wordpress. Right click on this new user name, select Add Host From Which This User Can Connect, and type localhost in the window. Press OK.
</p>
<p>
Next, click on the Catalogs item, right click on an empty area in the Schemata area, and select Create New Schema. For the Schema name, I once again simply used wordpress.
</p>
<p>
Now that we&#39;ve setup a database, we&#39;ll need to associate the wordpress item with it. Click on User Administration, then on wordpress, then on localhost beneath it. Next, click on the wordpress Schemata, and move all available privileges to assigned privileges. Select Apply Changes.
</p>
<p>
Note that we could have done this in a different order if we would have liked. Namely, we could have first setup our database/catalog, and then created our user.
</p>
<p>
Now that we&#39;ve created our user, we&#39;ll have to do the work-around to get the password correct. Open the Command Prompt and type the following.
</p>
<blockquote>
	<p>
	mysql -u root -p
	</p>
</blockquote>
<p>
Press enter, and type in the root password. Finally, we&#39;ll change the password for wordpress for all hosts.
</p>
<blockquote>
	<p>
	UPDATE mysql.user SET Password = OLD_PASSWORD(&#39;your_password&#39;) WHERE User = &#39;wordpress&#39;;<br />
	FLUSH PRIVILEGES;
	</p>
</blockquote>
<p>
Remember to substitute your_password with the password you would like to use. Once you&#39;ve done this, log on to phpMyAdmin to verify that the password works as expected, and you can view the wordpress database. <a href="http://phpmyadmin.localhost/">http://phpmyadmin.localhost/</a>.
</p>
<p>
<strong>Setting up the WordPress configuration file</strong>
</p>
<p>
Now that we&#39;ve created our MySQL user and database, we&#39;ll need to setup a configuration file for WordPress. Navigate to c:\home\wordpress\, and copy the wp-config-sample.php file. Now, rename our copy to wp-config.php. Finally, open this file in Notepad.
</p>
<p>
If you look at the top of this file, you&#39;ll notice four fields that start with &quot;define&quot;. We&#39;ll need to add the relevant information into the first three fields. First, verify that the DB_NAME is what you just setup in MySQL Administrator. The default is wordpress, which is what I setup above. Change DB_USER appropriately &ndash; in my case, wordpress is again used. Finally, change DB_PASSWORD to your password. Yes, we are entering this information into a text file. However, visitors won&#39;t be able to see this information, so long as you keep this file a PHP file.
</p>
<p>
Save the wp-config.php file, and close it, once you have made these changes.
</p>
<p>
<strong>Installing WordPress</strong>
</p>
<p>
That we&#39;ve created the wp-config.php file, we can visit <a href="http://wordpress.localhost/">http://wordpress.localhost/</a> to get a link to actually install WordPress. Otherwise, you can visit the installation file directly, at <a href="http://wordpress.localhost/wp-admin/install.php">http://wordpress.localhost/wp-admin/install.php</a>.
</p>
<p>
On the installation page, click the First Step link. Now, enter a Weblog title, and your email address. I used wordpress and my email, accordingly. Click to the next step.
</p>
<p>
Now, it will give you a username, admin, and a password, which should be random. Make a note of both of these, and do what it suggests &ndash; log in. <a href="http://wordpress.localhost/wp-login.php">http://wordpress.localhost/wp-login.php</a>
</p>
<p>
Now that you&#39;ve logged in, there&#39;s two things to do. The first is to setup your profile and change you password (the second bullet), and the second thing is to write a test post.
</p>
<p>
Once you do so, you&#39;ll have two posts on your site, one from the installation, and one from the user you just setup. To view you post, visit <a href="http://wordpress.localhost/">http://wordpress.localhost/</a>.
</p>
<p>
Congratulations &ndash; you&#39;ve successfully setup WordPress. Now, you can remove the installation&#39;s post and comment, and begin working on creating a unique style.
</p>
<p>
At this point, I should also point out the boon of creating a local WordPress. Backing up your WordPress is one of the best things that you can do. If you setup a WordPress, using the same username/password as the one you actually use on the Web, with the same database information (if you know that), you can backup your WordPress, and be able to work with your actual content when you work on style revisions. Killing two birds with one stone is always enjoyable.
</p>
<p>
In a later guide, we&#39;ll walk through backing up your WordPress installation, and when a new version of Wordpress is released, we&#39;ll walk through upgrading our installation. Until then, have fun playing around with WordPress.
</p>
<p>
<a href="http://strivinglife.net/wordpress/a-local-apache-web-server-on-a-windows-xp-computer/">View all of the steps to creating a local Web server, for development.</a>
</p>

