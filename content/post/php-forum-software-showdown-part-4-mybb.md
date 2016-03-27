+++
title = "PHP Forum Software Showdown Part 4: MyBB"
description = "In this article, we'll be going over how to install MyBB 1.2.1.  We'll also be looking at how MyBB stacks up to other PHP-based forum solutions."
draft = false
comments = true
date = "2006-11-22T21:00:00-06:00"
slug = "PHP-Forum-Software-Showdown-Part-4-MyBB"
blogengine = "d55bdb13-4095-45e4-bb3d-289314e4fb74"
categories = ["software", "tutorials / guides"]
tags = ["php", "mysql"]
+++

<p>
This time, we&#39;ll be looking at <a href="http://www.mybboard.com/">MyBB</a>. &ldquo;MyBB is a powerful, efficient and free forum package developed in PHP and MySQL. MyBB has been designed with the end users in mind, you and your subscribers. Full control over your discussion system is presented right at the tip of your fingers, from multiple styles and themes to the ultimate customisation of your forums using the template system.&rdquo;
</p>
<p>
In this article, we&#39;ll be installing MyBB version 1.2.1, which is the latest version, as of September 27, 2006.
</p>
<!--more-->
<h4>File and folder size</h4>
<p>
The zip file for MyBB weighs in at just over 1 MB. Unzipped, we&#39;re looking at almost 3 MB. The zip file does not contain a single folder, but rather two, so you&#39;ll want to unzip to a single MyBB folder. MyBB is also available in gzip and bzip formats.<!--adsense-->
</p>
<h4>Requirements</h4>
<p>
MyBB requirements were dang hard to find. That said, MyBB requires PHP 4.3.11+ and MySQL 4.0+. The PHP requirement actually seems a little high.
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
Since we&#39;re installing MyBB, we&#39;ll create a database called MyBB.
</p>
<blockquote>
	<p>
	 create database MyBB;
	</p>
</blockquote>
<p>
At this point, you&#39;ll be told that &ldquo;Query OK, 1 row affected&rdquo;, followed by the execution time.
</p>
<p>
Now, we&#39;ll create a user with privileges to access the database. Note that other than the bold text, this command is case-insensitive. Also, you may want to change &#39;<strong>mybb</strong>&#39; to something different (as this is the user&#39;s password).
</p>
<p>
Before you enter this, look it over, and then read the paragraph following, for an explanation.
</p>
<blockquote>
	<p>
	 GRANT select, insert, update, delete, index, alter, create, drop<br />
	ON <strong>MyBB</strong>.*<br />
	TO <strong>MyBB</strong> IDENTIFIED BY &#39;<strong>mybb</strong>&#39;;
	</p>
</blockquote>
<p>
The first line, &ldquo;GRANT select, insert, update, delete, index, alter, create, drop&rdquo;, states what privileges the user will be granted. The next line, &ldquo;ON <strong>MyBB</strong>.*&rdquo;, states what the privileges are applied to. Finally, &ldquo;TO <strong>MyBB</strong> IDENTIFIED BY &#39;<strong>mybb</strong>&#39;;&rdquo; states what user will get these privileges. Since the user doesn&#39;t exist yet, we&#39;re also giving a password to the user.
</p>
<p>
If the query is OK, enter the following command.
</p>
<blockquote>
	<p>
	 UPDATE mysql.user SET Password = OLD_PASSWORD(&#39;mybb&#39;) WHERE User = &#39;MyBB&#39;;
	</p>
</blockquote>
<p>
If this query is OK, and it works, type <strong>exit</strong>, and press Enter. Now attempt to login to the MyBB user. Once you&#39;ve logged in, enter the following command.
</p>
<blockquote>
	<p>
	 show databases;
	</p>
</blockquote>
<p>
You should be given an ASCII table that shows there&#39;s a database of mybb. Yippee.
</p>
<p>
Now, let&#39;s install MyBB.
</p>
<!--nextpage-->
<h4>Installing MyBB</h4>
<p>
First, unzip the downloaded zip file. The files are within two folders in the zip file, so make sure you create a folder to dump these into. I&#39;ll be using one called mybb.<!--adsense-->
</p>
<p>
Since we&#39;re installing locally, we don&#39;t have to worry about permissions. So, once MyBB has been decompressed, navigate to the MyBB root folder in your browser and then the upload/install folder. On my install, this is at <a href="http://localhost/projects/mybb/upload/install/">http://localhost/projects/mybb/install/</a>. I simply moved the upload folder&#39;s contents into the mybb folder.
</p>
<p>
You&#39;re in for it now. There&#39;s ten pages, from the initial look, that you&#39;ll have to go through. Here goes.
</p>
<p>
Read and Next along. There&#39;s a Requirements Check page which will tell you if you&#39;re set for requirements. If you&#39;ve followed along with my other tutorials, you will be set.
</p>
<p>
In Database Configuration, leave Host as is.
</p>
<blockquote>
	<p>
	Database Host: localhost<br />
	Database Username: MyBB<br />
	Database Password: mybb<br />
	Database Name: MyBB<br />
	Table Prefix: mybb_
	</p>
</blockquote>
<p>
Once this has been entered, and you&#39;ve pressed Next, the necessary tables (all fifty of them) will be created. Okay, so I was kidding about the fifty, but there&#39;s a whole lot. Yeesh. Next will populate these tables with some data, then setup the default theme.
</p>
<p>
Board Configuration is next, which will have some default settings. These will be fine, except the cookie path will have to be updated (why they couldn&#39;t do this, since they populated the others, we&#39;ll never know), followed by an email setting. Based on the URL of <a href="http://localhost/projects/mybb/">http://localhost/projects/mybb/</a>, my settings were as follows. Note that the domain is blank.
</p>
<blockquote>
	<p>
	Cookie Domain:<br />
	Cookie Path: /projects/mybb/
	</p>
</blockquote>
<p>
Next you&#39;ll create an Administrator Account. I used the same settings as I&#39;ve used for the previous forums.
</p>
<blockquote>
	<p>
	Username: admin<br />
	Password: cbe15b
	</p>
</blockquote>
<p>
At this point, MyBB will be setup. Yay. The installer will also be locked by the creation of a &#39;lock&#39; file. That is nice.
</p>
<!--nextpage-->
<h4>How&#39;s the code look?</h4>
<p>
Like most other forums, MyBB uses tables, and doesn&#39;t care to declare a summary. However, that looks like the only issue. Some of the admin pages are especially table-heavy.<!--adsense-->
</p>
<p>
Internally, some code is commented, while some is not. That&#39;s unfortunate, but from the MyBB site, it sounds like this will change.
</p>
<h4>Default layout and administrative interface</h4>
<p>
Once installed, MyBB setups up one category and no topics.
</p>
<p>
Unfortunately, the look is very boxy, and reminds me of the look of a number of other forums. There&#39;s really not that much, graphically, that separates it from the others.
</p>
<h4>Upgrading</h4>
<p>
Checking for updates, amongst other things, is quite easy from the interface. Unfortunately, when I attempted to check for updates, Apache started choking on me, specifically with problems in the php4ts.dll.
</p>
<p>
There&#39;s one download file, but it looks like they do state what files have been changed.
</p>
<h4>The temporary conclusion</h4>
<p>
MyBB has a nice administrative interface, but the default layout doesn&#39;t really get me excited. That&#39;s all I&#39;ll say, until we&#39;ve got the last two forums installed.
</p>
<p>
Stay tuned for the next <a href="/words/post/PHP-Forum-Software-Showdown.aspx">PHP Forum</a> review.
</p>
<p>
<a href="/local-apache-server/">View all of the steps to creating a local Web server, for development.</a>
</p>

