+++
title = "Upgrading (our local install of) WordPress"
description = "In a previous guide, we walked through installing WordPress on a local machine. This time, we'll be upgrading WordPress. For this guide, we'll be upgrading from WordPress 2.0.1 to 2.0.2.  Note this guide will work equally well for 2.0.3 or 2.0.4 as well."
draft = false
comments = true
date = "2006-03-11T16:31:00-06:00"
modified = "2007-08-11T09:42:29-05:00"
slug = "Upgrading-(our-local-install-of)-WordPress"
blogengine = "574d088b-ab26-4d54-ac7c-3f465f0bbb45"
categories = ["software", "Internet", "tutorials / guides"]
tags = ["wordpress", "mysql"]
+++

<p>
In <a href="http://strivinglife.net/wordpress/2006/02/28/59/setting-up-wordpress-on-a-local-web-server/">a previous guide</a>, we walked through installing WordPress on a local machine. This time, we&#39;ll be upgrading WordPress. For this guide, we&#39;ll be upgrading from WordPress 2.0.1 to 2.0.2.  Note that this guide will work equally well for upgrading to 2.0.3, 2.0.4 or 2.0.5.
</p>
<!--more--><!--adsense-->
<p>
<strong>Downloading WordPress</strong>
</p>
<p>
First, we&#39;ll have to download a copy of WordPress. Currently, the same download can be used to upgrade WordPress as to install WordPress, which makes things rather simple, in one sense. <a href="http://wordpress.org/download/">http://wordpress.org/download/</a>
</p>
<p>
We&#39;ll download the zip file into our downloads directory (in my case, at c:\home\downloads\), making sure that we keep the 2.0.1 install file, at least until we can verify that this new version doesn&#39;t cause compatibility issues.
</p>
<p>
<strong>Backup our current installation</strong>
</p>
<p>
Now that we&#39;ve downloaded the new version, we&#39;ll want to prepare our current version for the upgrade. When we do this, we&#39;ll be making backups of everything, so that we can roll-back to our working version, if necessary.
</p>
<p>
We&#39;ll first want to backup our current installation. This involves making a copy of the entire WordPress directory. In my case, c:\home\wordpress\. 
</p>
<p>
Now, we&#39;ll login to phpMyAdmin to backup the WordPress database. Visit <a href="http://phpmyadmin.localhost/">http://phpmyadmin.localhost/</a>, and login using your wordpress user. If you&#39;ve forgotten the password, you can find it by opening the wp-config.php file, in the main wordpress folder. Once you&#39;ve logged in, click on the Databases link, in the main content area, under the MySQL column, and then on the wordpress database, on the following screen.
</p>
<p>
Once you do this, you&#39;ll see a listing of all of the tables in the wordpress database, along with size and the like. Click on the Export tab, to continue.
</p>
<p>
Here, you&#39;ll be able to export the tables that are a part of the wordpress database. First, use the Select All link under the Export column to select all of the database tables. In the Structure area of the SQL options column, check Add DROP TABLE. Scroll down, and check the Save as file item. Finally, hit the Go button.
</p>
<p>
Once you do this, you&#39;ll be prompted to do something with a file called wordpress.sql. We&#39;ll create a new folder in our c:\home\ folder called backups, and save this file to that folder. When you save the folder, add the current date before the extension. For example, wordpress_20060311.sql. This will ensure that you&#39;re able to keep multiple backups, and will be able to sort the files easily.
</p>
<p>
Now that we&#39;ve made our backups, we&#39;ll need to disable any plugins that we may have running on our WordPress. Login to the wordpress, <a href="http://wordpress.localhost/wp-admin/">http://wordpress.localhost/wp-admin/</a>, and hit the Plugins tab. If any plugins are activated, deactivate them.
</p>
<p>
<strong>Performing the upgrade</strong>
</p>
<p>
Now that we&#39;ve made our backups, and disabled any plugins, we can proceed to upgrade the necessary files.
</p>
<p>
First, extract the downloaded zip file to it&#39;s own folder. Next, we&#39;ll be moving files from the new folder to our current install&#39;s folder. Because of this, it&#39;s a good idea to have two windows open while we&#39;re doing this. Depending upon the amount of customization you&#39;ve done, you can either copy files over and overwrite them all (save a few mentioned below), or you can check the dates of each file, only moving over those files that have dates that do not match (between the new and old installs). Since you have backups, you can always get the older copy if necessary.
</p>
<p>
The files that you will not want to overwrite are;
</p>
<ul>
	<li>wp-config.php file
	</li>
	<li>wp-content folder
	</li>
	<li>wp-images folder
	</li>
	<li>wp-includes/languages/ folder
	</li>
	<li>.htaccess files (which we haven&#39;t talked about before)
	</li>
</ul>
<p>
Working directory through directory ...
</p>
<ul>
	<li>In the root folder, c:\home\wordpress\, the only file changed should be the wp-config.php file, and there won&#39;t be a matching one in the downloaded zip. So, move all <em>files</em> from the new zip into the old zip, overwriting all files.
	</li>
	<li>In the entire wp-includes directory (including sub-folders), there&#39;s probably no reason to have modified any of these files. Move the entire wp-includes folder over, overwriting as necessary.
	</li>
	<li>In the wp-content folder, delete the cache folder on our current install.
	<ul>
		<li>Next, move the index.php file over.</li>
		<li>Now, move the plugins folder over. Since it&#39;s possible you installed plugins, we&#39;ll just want to overwrite the existing documents. If you have upgraded one of the standard plugins, however, you may want to verify after we have performed the WordPress upgrade that you did not lose this update.</li>
		<li>The themes folder should contain the standard themes, which you can simply move over, as any modifications to the themes should have been done in a new theme, instead of in these.</li>
	</ul>
	</li>
	<li>Finally, move the wp-admin folder. Again, modifications probably weren&#39;t made to these files (by you), so you shouldn&#39;t lose any changes. </li>
</ul>
<p>
Now that we&#39;ve upgraded the files, we&#39;ll just need to upgrade the database. Visit <a href="http://wordpress.localhost/wp-admin/upgrade.php">http://wordpress.localhost/wp-admin/upgrade.php</a>, and hit the link that you&#39;re bound not to miss. You should see Step 1, which will tell you that you&#39;re done.
</p>
<p>
Now, visit <a href="http://wordpress.localhost/">http://wordpress.localhost/</a>, login to the admin interface, and turn any plugins on, that you may have deactivated. All other options should be preserved.
</p>
<p>
<strong>Planning ahead for future upgrades</strong>
</p>
<p>
To make future installations easier, you can note which files you&#39;ve made modifications to, when you make them, and keep a backup of both the original, and the modification. This allows you to easily determine which files you&#39;ve changed.
</p>
<p>
You can also use a program like WinMerge, <a href="http://winmerge.sourceforge.net/">http://winmerge.sourceforge.net/</a>, to then determine what changes were made between the versions.
</p>
<p>
<a href="http://strivinglife.net/wordpress/a-local-apache-web-server-on-a-windows-xp-computer/">View all of the steps to creating a local Web server, for development.</a>
</p>

