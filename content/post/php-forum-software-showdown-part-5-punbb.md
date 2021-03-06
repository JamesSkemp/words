+++
title = "PHP Forum Software Showdown Part 5: PunBB"
description = "In this article, we'll be going over how to install PunBB 1.2.14.  We'll also be looking at how PunBB stacks up to other PHP-based forum solutions."
draft = false
comments = true
date = "2006-11-24T09:00:00-06:00"
slug = "PHP-Forum-Software-Showdown-Part-5-PunBB"
blogengine = "f4d7a12f-8baf-499f-9ff8-6137d1400938"
categories = ["software", "tutorials / guides"]
tags = ["php", "mysql", "postgresql"]
+++

<p>
Almost there. This time, we&#39;ll be looking at <a href="http://www.punbb.org/">PunBB</a>. First, I did donate to PunBB development some time ago. At the time, I liked PunBB, and received some great support. It&#39;s been sometime since that time, so I don&#39;t know how things stand.
</p>
<p>
Anywho, &ldquo;PunBB is a fast and lightweight PHP-powered discussion board. It is released under the GNU General Public License. Its primary goals are to be faster, smaller and less graphically intensive as compared to other discussion boards. PunBB has fewer features than many other discussion boards, but is generally faster and outputs smaller, semantically correct XHTML-compliant pages.&rdquo;
</p>
<p>
In this article, we&#39;ll be installing PunBB version 1.2.14, which is the latest version, as of October 15, 2006.
</p>
<!--more-->
<h4>File and folder size</h4>
<p>
The zip file for MyBB weighs in at around 250 KB. Unzipped, we&#39;re looking at a bit over 800 KB. The zip file does not contain a single folder, but rather three, so you&#39;ll want to unzip to a single PunBB folder. PunBB is also available in gzip and bz2 formats.<!--adsense-->
</p>
<h4>Requirements</h4>
<p>
Best requirements thus far. PHP 4.1.0+ and MySQL 3.23.17+, or PHP 4.3.0+ and PostgreSQL 7.0+, or SQLite. Not to shabby, as this is the first we&#39;ve reviewed that supports something other than just MySQL for the database.
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
Since we&#39;re installing PunBB, we&#39;ll create a database called PunBB.
</p>
<blockquote>
	<p>
	 create database PunBB;
	</p>
</blockquote>
<p>
At this point, you&#39;ll be told that &ldquo;Query OK, 1 row affected&rdquo;, followed by the execution time.
</p>
<p>
Now, we&#39;ll create a user with privileges to access the database. Note that other than the bold text, this command is case-insensitive. Also, you may want to change &#39;<strong>punbb</strong>&#39; to something different (as this is the user&#39;s password).
</p>
<p>
Before you enter this, look it over, and then read the paragraph following, for an explanation.
</p>
<blockquote>
	<p>
	 GRANT select, insert, update, delete, index, alter, create, drop<br />
	ON <strong>PunBB</strong>.*<br />
	TO <strong>PunBB</strong> IDENTIFIED BY &#39;<strong>punbb</strong>&#39;;
	</p>
</blockquote>
<p>
The first line, &ldquo;GRANT select, insert, update, delete, index, alter, create, drop&rdquo;, states what privileges the user will be granted. The next line, &ldquo;ON <strong>PunBB</strong>.*&rdquo;, states what the privileges are applied to. Finally, &ldquo;TO <strong>PunBB</strong> IDENTIFIED BY &#39;<strong>punbb</strong>&#39;;&rdquo; states what user will get these privileges. Since the user doesn&#39;t exist yet, we&#39;re also giving a password to the user.
</p>
<p>
If the query is OK, enter the following command.
</p>
<blockquote>
	<p>
	 UPDATE mysql.user SET Password = OLD_PASSWORD(&#39;punbb&#39;) WHERE User = &#39;PunBB&#39;;
	</p>
</blockquote>
<p>
If this query is OK, and it works, type <strong>exit</strong>, and press Enter. Now attempt to login to the PunBB user. Once you&#39;ve logged in, enter the following command.
</p>
<blockquote>
	<p>
	 show databases;
	</p>
</blockquote>
<p>
You should be given an ASCII table that shows there&#39;s a database of punbb. Yippee.
</p>
<p>
Now, let&#39;s install PunBB.
</p>
<!--nextpage-->
<h4>Installing PunBB</h4>
<p>
First, unzip the downloaded zip file. The files are within three folders in the zip file, so make sure you create a folder to dump these into. I&#39;ll be using one called punbb.<!--adsense-->
</p>
<p>
Since we&#39;re installing locally, we don&#39;t have to worry about permissions. So, once PunBB has been decompressed, navigate to the PunBB root folder in your browser. You&#39;ll be told that config.php doesn&#39;t exist, and be given a link to the install file. <a href="http://localhost/projects/punbb/install.php">http://localhost/projects/punbb/install.php</a>
</p>
<p>
There&#39;s a form to fill-out, so let&#39;s get to it.
</p>
<p>
You can select your database type, which we&#39;ll leave at MySQL Standard. Database server hostname can be left at localhost.
</p>
<p>
Database name: PunBB<br />
Database username: PunBB<br />
Database password: punbb<br />
Table prefix: punbb_<br />
Administrator username: admin<br />
Password: cbe15b<br />
Administrator&#39;s e-mail: strivinglife@gmail.com<br />
Base URL: http://localhost/projects/punbb
</p>
<p>
At this point, start the installation. Once that&#39;s done, you&#39;ll need to copy some text into a new config.php file, and then you can hit the main forum page at <a href="http://localhost/projects/punbb/">http://localhost/projects/punbb/</a> (for example).
</p>
<!--nextpage-->
<h4>How&#39;s the code look?</h4>
<p>
Like most other forums, PunBB uses a table, and doesn&#39;t care to declare a summary. However, that looks like the only issue.<!--adsense-->
</p>
<p>
Internally, code is commented pretty darn well. Not too shabby at all.
</p>
<h4>Default layout and administrative interface</h4>
<p>
Once installed, PunBB setups up one category, one forum, and one post.
</p>
<p>
Unfortunately, the look is very boxy, and reminds me of the look of a number of other forums. There&#39;s really not that much, graphically, that separates it from the others. The look is very similar to MyBB, but much flatter.
</p>
<h4>Upgrading</h4>
<p>
Checking for updates, amongst other things, is quite easy from the interface. Unfortunately, when I attempted to check for updates, Apache started choking on me, specifically with problems in the php4ts.dll (as it did with MyBB).
</p>
<p>
They do have archived files with the changed files only available for download, which is quite nice.
</p>
<h4>The temporary conclusion</h4>
<p>
PunBB is pretty much like the others that we&#39;ve reviewed. Until we get into the last forum, and start comparing all six, we&#39;ll leave it at that.
</p>
<p>
Stay tuned for the next <a href="/words/post/PHP-Forum-Software-Showdown.aspx">PHP Forum</a> review.
</p>
<p>
<a href="/local-apache-server/">View all of the steps to creating a local Web server, for development.</a>
</p>

