+++
title = "PHP Forum Software Showdown Part 3: Simple Machines"
description = "In this article, we'll be going over how to install Simple Machines 1.0.9.  We'll also be looking at how Simple Machines stacks up to other PHP-based forum solutions."
draft = false
comments = true
date = "2006-11-21T18:00:00-06:00"
slug = "PHP-Forum-Software-Showdown-Part-3-Simple-Machines"
blogengine = "485c3893-24e4-4c8b-8bb1-4ef321eec0f4"
categories = ["software", "tutorials / guides"]
tags = ["php", "mysql"]
+++

<p>
Curiously, in late-September 2006, <a href="http://simplemachines.org/">Simple Machines Forum</a> turned three (it had been three years since 1.0 beta 1). That&#39;s curious because the current stable version of Simple Machines is 1.0.9, and there&#39;s a 1.1 RC3 out as well (as of late-October 2006).
</p>
<p>
In this article, we&#39;ll be installing Simple Machines version 1.0.9, so we can compare it to the other PHP forums that we&#39;ve installed, or will be installing.
</p>
<!--more-->
<h4>File and folder size</h4>
<p>
The zip file for Vanilla 1.0.1 weighs in at just over 1.1 MB. Wow. Of the six forums we review, this is the largest. However, this is for the full install. There&#39;s also update and upgrade versions, as well as two other compressed formats (tar.gz and tar.bz2). Unzipped, we&#39;re looking at just over 3 MB of file.<!--adsense-->
</p>
<h4>Requirements</h4>
<p>
Simple Machines requires PHP 4.1.0+ and MySQL 3.23.28+. Compared to the other forums we&#39;ll be going over, these requirements are pretty low (especially the MySQL requirement). There are a number of PHP settings that must be turned on or off, for Simple Machines to function. Bossy, aren&#39;t they? If you&#39;ve followed along, our server will have all of these options set as they require.
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
Since we&#39;re installing Simple Machines, we&#39;ll create a database called SimpleMachines.
</p>
<blockquote>
	<p>
	 create database SimpleMachines;
	</p>
</blockquote>
<p>
At this point, you&#39;ll be told that &ldquo;Query OK, 1 row affected&rdquo;, followed by the execution time.
</p>
<p>
Now, we&#39;ll create a user with privileges to access the database. Note that other than the bold text, this command is case-insensitive. Also, you may want to change &#39;<strong>simplemachines</strong>&#39; to something different (as this is the user&#39;s password).
</p>
<p>
Before you enter this, look it over, and then read the paragraph following, for an explanation.
</p>
<blockquote>
	<p>
	 GRANT select, insert, update, delete, index, alter, create, drop<br />
	ON <strong>SimpleMachines</strong>.*<br />
	TO <strong>SimpleMachines</strong> IDENTIFIED BY &#39;<strong>simplemachines</strong>&#39;;
	</p>
</blockquote>
<p>
The first line, &ldquo;GRANT select, insert, update, delete, index, alter, create, drop&rdquo;, states what privileges the user will be granted. The next line, &ldquo;ON <strong>SimpleMachines</strong>.*&rdquo;, states what the privileges are applied to. Finally, &ldquo;TO <strong>SimpleMachines</strong> IDENTIFIED BY &#39;<strong>simplemachines</strong>&#39;;&rdquo; states what user will get these privileges. Since the user doesn&#39;t exist yet, we&#39;re also giving a password to the user.
</p>
<p>
If the query is OK, enter the following command.
</p>
<blockquote>
	<p>
	 UPDATE mysql.user SET Password = OLD_PASSWORD(&#39;simplemachines&#39;) WHERE User = &#39;SimpleMachines&#39;;
	</p>
</blockquote>
<p>
If this query is OK, and it works, type <strong>exit</strong>, and press Enter. Now attempt to login to the SimpleMachines user. Once you&#39;ve logged in, enter the following command.
</p>
<blockquote>
	<p>
	 show databases;
	</p>
</blockquote>
<p>
You should be given an ASCII table that shows there&#39;s a database of simplemachines. Yippee.
</p>
<p>
Now, let&#39;s install Simple Machines.
</p>
<!--nextpage-->
<h4>Installing Simple Machines</h4>
<p>
First, unzip the downloaded zip file. The files are not within a directory in the zip file, so make sure you create a folder to dump these into. I&#39;ll be using one called SimpleMachines.<!--adsense-->
</p>
<p>
Since we&#39;re installing locally, we don&#39;t have to worry about permissions. So, once Simple Machines has been decompressed, navigate to the Simple Machines root folder in your browser. Since you haven&#39;t setup Simple Machines yet, it will redirect you to the installer, which is located at, in my install, <a href="http://localhost/projects/simplemachines/install.php">http://localhost/projects/simplemachines/install.php</a>.
</p>
<p>
You&#39;ll be prompted for Basic and MySQL Server settings. I left the Basic Settings as they were. MySQL Server Settings have been started, we just need to confirm and finish them.
</p>
<blockquote>
	<p>
	MySQL server name: localhost<br />
	MySQL username: SimpleMachines<br />
	MySQL password: simplemachines<br />
	MySQL database name: SimpleMachines<br />
	MySQL table prefix: smf_
	</p>
</blockquote>
<p>
Once you proceed, you should now be able to create your account. As before, I used the same username and password as I used in the previous forum installs.
</p>
<blockquote>
	<p>
	Your username: admin<br />
	Password: cbe15b<br />
	Password: cbe15b<br />
	Email Address: strivinglife@gmail.com
	</p>
</blockquote>
<p>
You&#39;ll also need to enter in the MySQL database password, which is the same as you used before (simplemachines in my case). With that, finish up. You should be told that the installation process is complete, and you can now delete the install file (possibly using the installer). You&#39;ll be automatically logged in. If install.php still exists, you&#39;ll be told so.
</p>
<!--nextpage-->
<h4>How&#39;s the code look?</h4>
<p>
Unfortunately, Simple Machines is very table heavy. Combined with the fact that they don&#39;t have summaries, the code isn&#39;t the cleanest. In addition, links use ids that start with numbers, which is not that good of a thing.<!--adsense-->
</p>
<p>
Inside, the code looks pretty darn good.
</p>
<h4>Default layout and administrative interface</h4>
<p>
Once installed, Simple Machines setups up one category and one topic (with one post). That&#39;s nice.
</p>
<p>
Unfortunately, the look is very, very, boxy. Some people like this, but I like things that flow a little more. There is another theme installed by default, which looks much better.
</p>
<h4>Upgrading</h4>
<p>
Checking for updates is quite easy from the interface. From the looks of it, upgrading is just as easy, since there&#39;s a separate file. Wow.
</p>
<h4>The temporary conclusion</h4>
<p>
I&#39;ve used Simple Machines before on Fractovia. I don&#39;t really care for it, since it feels and looks clunky. On the bright side, no configuration files to manually update. Thus far, three reviews down, I&#39;m siding heavily with Vanilla.
</p>
<p>
But, before we dig any further, we&#39;ll need to install some more forums.
</p>
<p>
Stay tuned for the next <a href="/words/post/PHP-Forum-Software-Showdown.aspx">PHP Forum</a> review.
</p>
<p>
<a href="/local-apache-server/">View all of the steps to creating a local Web server, for development.</a>
</p>

