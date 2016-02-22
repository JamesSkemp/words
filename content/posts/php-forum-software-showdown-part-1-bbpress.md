+++
title = "PHP Forum Software Showdown Part 1: bbPress"
summary = "In this article, we'll be going over how to install bbPress 0.73.  We'll also be looking at how bbPress stacks up to other PHP-based forum solutions."
draft = false
comments = true
date = "2006-11-19T09:00:00-06:00"
slug = "PHP-Forum-Software-Showdown-Part-1-bbPress"
blogengine = "39338fa4-38ce-4b13-91a1-3e125ea5e0da"
categories = ["software", "tutorials / guides"]
tags = ["php", "mysql"]
+++

<p>
A relative new-comer, <a href="http://bbpress.org/">bbPress</a> &ldquo;is forum software with a twist from the creators of WordPress&rdquo;. The first public version, 0.72, was released in mid-October 2006, and the version we&#39;ll be installing, 0.73, was released a couple of weeks later. Downloading bbPress is fairly easy, since there&#39;s only two options &ndash; one for the installer in .zip, and one in .tar.gz.
</p>
<!--more-->
<h4>File and folder size</h4>
<p>
At 170 KB, the zip file is extremely small, and is less than 500 KB unzipped. Of the six pieces of forum software that I&#39;ll be reviewing, bbPress is the smallest, but we&#39;ll see what that translates into as far as functionality.<!--adsense-->
</p>
<h4>Requirements</h4>
<p>
bbPress requires PHP 4.2+ and MySQL 4.0+, as well as MultiViews or mod_rewrite. All-in-all, pretty standard.
</p>
<h4>Installing on our local Web server</h4>
<p>
Unlike past articles, for these forum reviews we&#39;re going to create the necessary users and databases using the command line interface of MySQL. If you&#39;re going to be installing these forums to a remote system, just create the user(s) and database(s) as usual (and that goes for if you&#39;re installing it locally as well).
</p>
<h4>Creating the user and database via the command-line</h4>
<p>
First, you&#39;ll need to login to MySQL. Open up the Run prompt by going to Start &gt; Run ... and type <strong>cmd</strong>, then press Enter. At the prompt, if you&#39;ve setup MySQL correctly, you can type the following command, followed by pressing Enter.
</p>
<blockquote>
	<p>
	 mysql -h localhost -u root -p
	</p>
</blockquote>
<p>
At this point, you&#39;ll be prompted to enter your password, which you&#39;ll have already setup. Enter your password and press Enter.
</p>
<p>
At this point, you&#39;re logged into MySQL. Now, we can create our database, create our user, and grant the user privilege to modify the database we created.
</p>
<p>
Since we&#39;re installing bbPress, we&#39;ll create a database called bbPress.
</p>
<blockquote>
	<p>
	 create database bbPress;
	</p>
</blockquote>
<p>
At this point, you&#39;ll be told that &ldquo;Query OK, 1 row affected&rdquo;, followed by the execution time.
</p>
<p>
Now, we&#39;ll create a user with privileges to access the database. Note that other than the bold text, this command is case-insensitive. Also, you may want to change &#39;<strong>bbpress</strong>&#39; to something different (as this is the user&#39;s password).
</p>
<p>
Before you enter this, look it over, and then read the paragraph following, for an explanation.
</p>
<blockquote>
	<p>
	 GRANT select, insert, update, delete, index, alter, create, drop<br />
	ON <strong>bbPress</strong>.*<br />
	TO <strong>bbPress</strong> IDENTIFIED BY &#39;<strong>bbpress</strong>&#39;;
	</p>
</blockquote>
<p>
The first line, &ldquo;GRANT select, insert, update, delete, index, alter, create, drop&rdquo;, states what privileges the user will be granted. The next line, &ldquo;ON <strong>bbPress</strong>.*&rdquo;, states what the privileges are applied to. Finally, &ldquo;TO <strong>bbPress</strong> IDENTIFIED BY &#39;<strong>bbpress</strong>&#39;;&rdquo; states what user will get these privileges. Since the user doesn&#39;t exist yet, we&#39;re also giving a password to the user.
</p>
<p>
If the query is ok, enter the following command.
</p>
<blockquote>
	<p>
	 UPDATE mysql.user SET Password = OLD_PASSWORD(&rsquo;bbpress&rsquo;) WHERE User = &lsquo;bbPress&rsquo;;
	</p>
</blockquote>
<p>
If this query is OK, and it works, type <strong>exit</strong>, and press Enter. Now attempt to login to the bbPress user. Once you&#39;ve logged in, enter the following command.
</p>
<blockquote>
	<p>
	 show databases;
	</p>
</blockquote>
<p>
You should be given an ASCII table that shows there&#39;s a database of bbpress. Yippee.
</p>
<p>
Now, let&#39;s install bbPress.
</p>
<!--nextpage-->
<h4>Installing bbPress</h4>
<p>
First, unzip the downloaded zip file. The files are all included in a bbpress folder. For this guide, we&#39;ll be keeping it in that folder, since we&#39;ll be installing a number of forums. However, if you decide to go with bbPress, you may not want to keep the files in the bbPress folder.<!--adsense-->
</p>
<p>
Once bbPress has been decompressed, go into the bbpress folder and make a copy of the config-sample.php file. Rename the copy to simply config.php. Next, open the file. There&#39;s a lot of things to change, so get ready.
</p>
<p>
First, change lines 4 to 7 (begin with &#39;define&#39;). Per the above, it&#39;ll be something like the following.
</p>
<blockquote>
	<p>
	 define(&#39;BBDB_NAME&#39;, &#39;bbPress&#39;); // The name of the database<br />
	define(&#39;BBDB_USER&#39;, &#39;bbPress&#39;); // Your MySQL username<br />
	define(&#39;BBDB_PASSWORD&#39;, &#39;bbpress&#39;); // ...and password<br />
	define(&#39;BBDB_HOST&#39;, &#39;localhost&#39;); // 99% chance you won&#39;t need to change this value
	</p>
</blockquote>
<p>
Line 15 will need to be changed as well. For my installation, it was as follows.
</p>
<blockquote>
	<p>
	 $bb-&gt;domain = &#39;http://localhost&#39;; // Example: &#39;http://bbpress.example.com&#39;
	</p>
</blockquote>
<p>
Line 17 was changed as well. This may vary for your installation.
</p>
<blockquote>
	<p>
	 $bb-&gt;path = &#39;/projects/bbpress/&#39;;				 // Example: &#39;/forums/&#39;
	</p>
</blockquote>
<p>
I&#39;m going to leave the name (line 20) as is, but change line 23, the email. Make sure you change your&#39;s accordingly.
</p>
<blockquote>
	<p>
	 $bb-&gt;admin_email = &#39;strivinglife@gmail.com&#39;;
	</p>
</blockquote>
<p>
Line 35 should also be changed, per your timezone.
</p>
<blockquote>
	<p>
	 $bb-&gt;gmt_offset = 0;
	</p>
</blockquote>
<p>
We&#39;ll leave everything else as is, for now. Let&#39;s make sure Apache is up and running, and we&#39;ll see what else we have to do. Head over to <a href="http://localhost/projects/bbpress/">http://localhost/projects/bbpress/</a>
</p>
<p>
Click the First Step link. Enter in a couple options for the Administrator. These include Login name, Website, Location, and Interests.
</p>
<p>
You&#39;ll also need to define your First Forum by giving it a Name and a Description.
</p>
<p>
Only Login name and Forum Name are required, so I entered &#39;admin&#39; and &#39;Test&#39;, respectively. Continue to the next step.
</p>
<p>
The Second Step creates the tables (8) and gives you a password. It&#39;s random, so hold on to it. In my case, it was <strong>cbe15b</strong>. You can click on either link to go to the bbPress page, which is available at <a href="http://localhost/projects/bbpress/">http://localhost/projects/bbpress/</a>, in my case.
</p>
<p>
You can now login to check out the Administrative interface, or you check out the topic that was created.
</p>
<!--nextpage-->
<h4>How&#39;s the code look?</h4>
<p>
Overall, the code validates pretty dang well. There&#39;s a minor issue with an opening and closing small tag, with nothing between, on the main interface view, and some tables missing summaries, but other than that ... code looks good.<!--adsense-->
</p>
<p>
As far as the internal PHP code, like WordPress, it&#39;s full. You&#39;ll need to reference files and documentation, back and forth, but that&#39;s to be expected, I suppose.
</p>
<h4>Upgrading and default layout</h4>
<p>
Unlike some of the other forums we&#39;ll be looking at, there&#39;s no upgrade-only installation file. Yuck. Upgrading WordPress is a beast, and it looks like that&#39;s going to be an issue with bbPress.
</p>
<p>
Where it gets really bad is when you look at the layout. The default layout, especially for the admin interface, could absolutely be better. Unfortunately, it looks like the styles are buried in multiple files, in multiple folders.
</p>
<p>
As with WordPress, it looks like upgrading is going to be a beast (with functions dropping and being added), but even more so because there doesn&#39;t appear to be a way to easily create your own styles, outside of the core files.
</p>
<h4>Administrative interface</h4>
<p>
The administrative interface, other than being rather ugly, is pretty simple. Unfortunately, there&#39;s no way, via the interface alone, to modify the styles or code.
</p>
<h4>The temporary conclusion</h4>
<p>
At this point, I&#39;m going to stop, since we&#39;ll want other forums to compare before we go any further. However, you should have a bbPress, version 0.73, forum setup.
</p>
<p>
Stay tuned for the next <a href="/words/post/PHP-Forum-Software-Showdown.aspx">PHP Forum</a> review.
</p>
<p>
<a href="/local-apache-server/">View all of the steps to creating a local Web server, for development.</a>
</p>

