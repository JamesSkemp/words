+++
title = "PHP Forum Software Showdown Part 2: Vanilla"
summary = "In this article, we'll be going over how to install Vanilla 1.0.1.  We'll also be looking at how Vanilla stacks up to other PHP-based forum solutions."
draft = false
comments = true
date = "2006-11-20T09:00:00-06:00"
slug = "PHP-Forum-Software-Showdown-Part-2-Vanilla"
blogengine = "25fbbaec-33bb-4404-b532-0ed7f56c844b"
categories = ["software", "tutorials / guides"]
tags = ["php", "mysql"]
+++

<p>
While the <a href="http://getvanilla.com/">Vanilla</a> forum&#39;s are fairly unknown, it&#39;s been around for a little over a year. &ldquo;Vanilla is an open-source, standards-compliant, multi-lingual, fully extensible discussion forum for the web.&rdquo; The version we&#39;ll be installing, 1.0.1, was released in late-August 2006.
</p>
<!--more-->
<h4>File and folder size</h4>
<p>
The zip file for Vanilla 1.0.1 (which is the only download type) weighs in at just under 400 KB. Unzipped, it&#39;s almost 1.2 MB in size. Overall, that&#39;s pretty small.<!--adsense-->
</p>
<h4>Requirements</h4>
<p>
Vanilla requires PHP 4.1+ and MySQL 3.23+. Compared to the other forums we&#39;ll be going over, these requirements are pretty low (especially the MySQL requirement).
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
Since we&#39;re installing Vanilla, we&#39;ll create a database called Vanilla.
</p>
<blockquote>
	<p>
	 create database Vanilla;
	</p>
</blockquote>
<p>
At this point, you&#39;ll be told that &ldquo;Query OK, 1 row affected&rdquo;, followed by the execution time.
</p>
<p>
Now, we&#39;ll create a user with privileges to access the database. Note that other than the bold text, this command is case-insensitive. Also, you may want to change &#39;<strong>vanilla</strong>&#39; to something different (as this is the user&#39;s password).
</p>
<p>
Before you enter this, look it over, and then read the paragraph following, for an explanation.
</p>
<blockquote>
	<p>
	 GRANT select, insert, update, delete, index, alter, create, drop<br />
	ON <strong>Vanilla</strong>.*<br />
	TO <strong>Vanilla</strong> IDENTIFIED BY &#39;<strong>vanilla</strong>&#39;;
	</p>
</blockquote>
<p>
The first line, &ldquo;GRANT select, insert, update, delete, index, alter, create, drop&rdquo;, states what privileges the user will be granted. The next line, &ldquo;ON <strong>Vanilla</strong>.*&rdquo;, states what the privileges are applied to. Finally, &ldquo;TO <strong>Vanilla</strong> IDENTIFIED BY &#39;<strong>vanilla</strong>&#39;;&rdquo; states what user will get these privileges. Since the user doesn&#39;t exist yet, we&#39;re also giving a password to the user.
</p>
<p>
If the query is OK, enter the following command.
</p>
<blockquote>
	<p>
	 UPDATE mysql.user SET Password = OLD_PASSWORD(&#39;vanilla&#39;) WHERE User = &#39;Vanilla&#39;;
	</p>
</blockquote>
<p>
If this query is OK, and it works, type <strong>exit</strong>, and press Enter. Now attempt to login to the Vanilla user. Once you&#39;ve logged in, enter the following command.
</p>
<blockquote>
	<p>
	 show databases;
	</p>
</blockquote>
<p>
You should be given an ASCII table that shows there&#39;s a database of vanilla. Yippee.
</p>
<p>
Now, let&#39;s install Vanilla.
</p>
<!--nextpage-->
<h4>Installing Vanilla</h4>
<p>
First, unzip the downloaded zip file. The files are all included in a Vanilla.1.0.1 folder. For this guide, we&#39;ll be keeping it in that folder, since we&#39;ll be installing a number of forums, but changing the name to remove the version information.<!--adsense-->
</p>
<p>
Once Vanilla has been decompressed, navigate to the Vanilla root folder in your browser. Since you haven&#39;t setup Vanilla yet, it will redirect you to the installer, which is located at, in my install, <a href="http://localhost/projects/vanilla/setup/index.html">http://localhost/projects/vanilla/setup/index.html</a>.
</p>
<p>
Here, there&#39;s a couple of options. You can either install fresh (which is what we&#39;ll be doing) or find out how to upgrade from a previous version. For now, let&#39;s click on the link to &ldquo;install a completely brand new version of Vanilla&rdquo;. These steps will walk you through the setup almost completely.
</p>
<p>
First, you&#39;ll need to assure that permissions have been setup correctly on files and folders. We&#39;re okay in this respect, so check the permissions and continue.
</p>
<p>
Next, you&#39;ll need to enter in information regarding MySQL. If you&#39;ve been following along, these are as follows.
</p>
<p>
MySQL Server: localhost<br />
MySQL Database Name: Vanilla<br />
MySQL User: Vanilla<br />
MySQL Password: vanilla
</p>
<p>
Click on the link to continue.
</p>
<p>
Finally, you&#39;ll need to create an administrative account, setup a contact email, and confirm cookie options. What follows are my options, but customize as needed. Note that for password, I simply used the password I was given for bbPress.
</p>
<p>
Username: admin<br />
Password: cbe15b<br />
Support Contact Name: James Skemp<br />
Support Email Address: strivinglife@gmail.com<br />
Forum Name: Vanilla<br />
Cookie Domain: localhost<br />
Cookie Path: /projects/vanilla/
</p>
<p>
One final click, and you&#39;re ready to go. You can either login, as they direct, or just take a look at the main page. <a href="http://localhost/projects/vanilla/">http://localhost/projects/vanilla/</a>
</p>
<!--nextpage-->
<h4>How&#39;s the code look?</h4>
<p>
All-in-all, the code validates beautifully, and is a pleasure to read. The random code files I pulled up were extremely well documented. I&#39;ve rarely seen code such as this.<!--adsense-->
</p>
<h4>Default layout and administrative interface</h4>
<p>
Like the code, the default layout is beautiful. Simple, simple, simple. The administrative interface uses the same wrapper as the main site, so ditto for it. And, what&#39;s this, no tables?
</p>
<p>
Unfortunately, entering into some options, you lose your left-side navigation, and there&#39;s no way to go back via a link. Fortunately, this isn&#39;t the case for all of the options.
</p>
<p>
No forums or topics are already setup, for better or worse. On the one hand, it makes clean-up easy, but it also means you have to do this yourself just to get a look.
</p>
<h4>Upgrading</h4>
<p>
Checking for updates is quite easy from the interface. Unfortunately, upgrading basically involves reinstalling Vanilla. If you&#39;ve made modifications, you&#39;ll need to re-add them. However, they do say that you can see what files have changed, which means you can do a compare to add in the new changes. Not too shabby.
</p>
<h4>The temporary conclusion</h4>
<p>
I like Vanilla based on my first impression. Editing configuration files is no fun, especially for people who can&#39;t code. Vanilla makes all of this really easy.
</p>
<p>
Yet, on the other hand, it&#39;s MySQL connection step doesn&#39;t provide much help to the person who doesn&#39;t know any of this. Default to localhost, since that will usually be what the user needs.
</p>
<p>
Before we dig any further, we&#39;ll need to install some more forums.
</p>
<p>
Stay tuned for the next <a href="/words/post/PHP-Forum-Software-Showdown.aspx">PHP Forum</a> review.
</p>
<p>
<a href="/local-apache-server/">View all of the steps to creating a local Web server, for development.</a>
</p>

