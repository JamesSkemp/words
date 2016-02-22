+++
title = "PHP Forum Software Showdown Part 6: phpBB"
summary = "In this article, we'll be going over how to install phpBB 2.0.21.  We'll also be looking at how phpBB stacks up to other PHP-based forum solutions."
draft = false
comments = true
date = "2006-11-25T18:30:00-06:00"
modified = "2009-11-07T21:15:26-06:00"
slug = "PHP-Forum-Software-Showdown-Part-6-phpBB"
blogengine = "0d5f11d0-ab1d-4071-a040-6a6c0e49f350"
categories = ["software", "tutorials / guides"]
tags = ["php", "mysql", "postgresql"]
+++

<p>It's that time again. This time, we'll be looking at <a rel="external" href="http://www.phpbb.com/">phpBB</a>. &ldquo;phpBB is a high powered, fully scalable, and highly customizable Open Source bulletin board package. phpBB has a user-friendly interface, simple and straightforward administration panel, and helpful FAQ. Based on the powerful PHP server language and your choice of MySQL, MS-SQL, PostgreSQL or Access/ODBC database servers, phpBB is the ideal free community solution for all web sites.&rdquo;</p>
<p>Lot's of features, so let's get to it. In this article, we'll be installing phpBB version 2.0.21, which is the latest version, as of June 9, 2006. A beta version of 3.0 came out a very short period before this article was written, otherwise I don't know that phpBB would have made it. Anywho, on with it.</p>
<h3>File and folder size</h3>
<p>The zip file for phpBB weighs in at around 650 KB. Unzipped, we're looking at almost 2 MB. The zip file contains a single phpBB2 folder, so extract away. phpBB is also available in gzip and bz2 formats.</p>
<h3>Requirements</h3>
<p>Check out these requirements. PHP 4.0.3+ and one of these database systems; MySQL 3.22+ or PostgreSQL 7.0.3+ or MS SQL Server 7+ or MS Access 2000+</p>
<h3>Installing on our local Web server</h3>
<p>Unlike past articles, for these forum reviews we're going to create the necessary users and databases using the command line interface of MySQL. If you're going to be installing these forums to a remote system, just create the user(s) and database(s) as usual (and that goes for if you're installing it locally as well).</p>
<h3>Creating the user and database via the command-line</h3>
<p>First, you'll need to login to MySQL. Open up the Run prompt by going to Start &gt; Run ... and type <strong>cmd</strong>, then press Enter. At the prompt, if you've setup MySQL correctly, you can type the following command, followed by pressing Enter.</p>
<pre class="code"><code class="powershell">mysql -h localhost -u root -p</code></pre>
<p>At this point, you'll be prompted to enter your password, which you'll have already setup. Enter your password and press Enter.</p>
<p>At this point, you're logged into MySQL. Now, we can create our database, create our user, and grant the user privilege to modify the database we created.</p>
<p>Since we're installing phpBB, we'll create a database called phpBB.</p>
<pre class="code"><code class="sql">create database phpBB;</code></pre>
<p>At this point, you'll be told that &ldquo;Query OK, 1 row affected&rdquo;, followed by the execution time.</p>
<p>Now, we'll create a user with privileges to access the database. Note that other than the bold text, this command is case-insensitive. Also, you may want to change '<strong>phpbb</strong>' to something different (as this is the user's password).</p>
<p>Before you enter this, look it over, and then read the paragraph following, for an explanation.</p>
<pre class="code"><code class="sql">GRANT select, insert, update, delete, index, alter, create, drop
ON <strong>phpBB</strong>.*
TO <strong>phpBB</strong> IDENTIFIED BY '<strong>phpbb</strong>';</code></pre>
<p>The first line, &ldquo;GRANT select, insert, update, delete, index, alter, create, drop&rdquo;, states what privileges the user will be granted. The next line, &ldquo;ON <strong>phpBB</strong>.*&rdquo;, states what the privileges are applied to. Finally, &ldquo;TO <strong>phpBB</strong> IDENTIFIED BY '<strong>phpbb</strong>';&rdquo; states what user will get these privileges. Since the user doesn't exist yet, we're also giving a password to the user.</p>
<p>If the query is OK, enter the following command.</p>
<pre class="code"><code class="sql">UPDATE mysql.user SET Password = OLD_PASSWORD('phpbb') WHERE User = 'phpBB';</code></pre>
<p>If this query is OK, and it works, type <strong>exit</strong>, and press Enter. Now attempt to login to the phpBB user. Once you've logged in, enter the following command.</p>
<blockquote>
<p>show databases;</p>
</blockquote>
<p>You should be given an ASCII table that shows there's a database of phpbb. Yippee.</p>
<p>Now, let's install phpBB.</p>
<h3>Installing phpBB</h3>
<p>First, unzip the downloaded zip file. I'll be using one called phpBB2.<!--adsense--></p>
<p>Since we're installing locally, we don't have to worry about permissions. So, once phpBB has been decompressed, navigate to the phpBB root folder in your browser. You'll be automatically be redirected to <a href="http://localhost/projects/phpbb2/install/install.php">http://localhost/projects/phpbb2/install/install.php</a></p>
<p>There's a form to fill-out, so let's get to it.</p>
<p>Database Type: MySQL 4.x/5.x<br />Choose your installation method: Install<br />Database Server Hostname/DSN: localhost<br />Your Database Name: phpBB<br />Database Username: phpBB<br />Database Password: phpbb<br />Prefix for tables in database: phpbb_<br />Admin Email Address: strivinglife@gmail.com<br />Domain Name: localhost<br />Server Port: 80<br />Script path: /projects/phpbb2/<br />Administrator Username: admin<br />Administrator Password: cbe15b</p>
<p>That's it. Woot. You'll have to delete or rename the install and contrib folders (I put an underscore before both). At this point, you can start bouncing around the forum. Woot?</p>
<h3>How's the code look?</h3>
<p>Like most other forums, phpBB uses tables, and doesn't care to declare a summary. There's also an issue with an 'invalid' target for the footer link.<!--adsense--></p>
<p>Internally, code is commented pretty darn well. However, the main comment header is the same copyright notice over and over. Yuck.</p>
<h3>Default layout and administrative interface</h3>
<p>Once installed, phpBB setups up one category, one forum, and one post.</p>
<p>Unfortunately, the look is very boxy, and reminds me of the look of a number of other forums. There's really not that much, graphically, that separates it from the others. Very similar look to MyBB and PunBB. Where's the admin interface? Oh, there's a link way down at the bottom of the page. Eh.</p>
<h3>Upgrading</h3>
<p>Checking for updates, amongst other things, is quite easy from the interface, and the install even had an option regarding upgrading. Hmm.</p>
<p>They do have archived files with the changed and patched files only available for download, which is quite nice.</p>
<h3>The temporary conclusion</h3>
<p>phpBB is pretty much like the others that we've reviewed. But, now that we've gone over all of them, as far as installation and first impressions, it's time to dig into them deeper.</p>
<p>Stay tuned for the next <a href="/words/post/PHP-Forum-Software-Showdown.aspx">PHP Forum</a> review article, where we start busting heads.</p>
<p><a href="/local-apache-server/">View all of the steps to creating a local Web server, for development.</a></p>
