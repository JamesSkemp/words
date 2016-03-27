+++
title = "Adding MySQL connectivity to ColdFusion MX on a local Windows-based, Apache, server"
description = "This time, we'll be setting up MySQL 4.1.18 and ColdFusion MX 6.1 on our local server. Because of some of the choices that we've made before, this installation is going to be fairly quick."
draft = false
comments = true
date = "2006-03-18T08:55:00-06:00"
modified = "2009-12-20T18:37:35-06:00"
slug = "Adding-MySQL-connectivity-to-ColdFusion-MX-on-a-local-Windows-based-Apache-server"
blogengine = "c43d7017-10a9-4251-bdc4-0ac71b458186"
categories = ["tutorials / guides"]
tags = ["coldfusion", "mysql"]
+++

<p>Until now, we've yet to setup a connection to MySQL from ColdFusion MX. This has meant that while we can do cool database things in PHP (like WordPress), we can't in ColdFusion. Until now.</p>
<p>This time, we'll be setting up MySQL 4.1.18 and ColdFusion MX 6.1 on our local server. Because of some of the choices that we've made before, this installation is going to be fairly quick.</p>
<h3>Setting up MySQL database and user</h3>
<p>First, we'll need to setup a MySQL database and user for ColdFusion. So, start MySQL Administrator and create a new catalog called COLDFUSIONMX. While MySQL Administrator will down-cap the name, we'll enter it in all-caps, just because.</p>
<p>Setup a new MySQL User ColdFusionMX, and add the localhost domain, and assign all privileges to the COLDFUSIONMX schema.</p>
<p>Now, close out of MySQL Administrator, and go to the command line (Window + R, and cmd) and type the following, as we've done before.</p>
<pre class="code"><code class="powershell">mysql -u root -p</code></pre>
<p>Press enter, and type in the root password. Finally, we'll change the password for ColdFusionMX for all hosts. Password should be 16 characters or less.</p>
<blockquote>
<p>UPDATE mysql.user SET Password = OLD_PASSWORD('your_password') WHERE User = 'ColdFusionMX';<br />FLUSH PRIVILEGES;</p>
</blockquote>
<p>Exit out of this and the command line ("exit", enter, "exit", enter).</p>
<h3>Setting up in ColdFusion MX Administrator</h3>
<p>Now that we've setup our database and user in MySQL, we'll need to setup the datasource in ColdFusion MX. If ColdFusion isn't already started, start ColdFusion via Services.</p>
<p>Log in to ColdFusion MX Administrator (<a href="http://localhost/CFIDE/administrator/index.cfm">http://localhost/CFIDE/administrator/index.cfm</a> if you've been following along), and select Data Sources under DATA &amp; SERVICES on the left side navigation.</p>
<p>Enter the Data Source name of MySQLDatabase, and select MySQL under Driver. Hit Add.</p>
<p>On the resulting screen, enter the following information. Make sure you enter in your_password the password you used above.</p>
<p>Database: COLDFUSIONMX<br />Server: localhost, leave Port to 3306<br />Username: ColdFusionMX<br />Password: your_password<br />Description: MySQL database for ColdFusion MX 6.1. (or whatever you want to type)</p>
<p>Hit Submit.</p>
<p>Now, Verify All Connections. This will test the three Access databases (if you set up the samples for ColdFusionMX) as well as your new MySQL database. You should get a Status of OK after doing this (and you may get an OK after initially setting up the database).</p>
<p>Before we continue, note that we can only connect to MySQL this easily because of the OLD_PASSWORD function we do on our password. Since we've been doing this all along, it's the easiest solution. The other solution is to update some files, which we won't go into since we don't have to.</p>
<h3>Create a test table in MySQL with ColdFusion</h3>
<p>Now, we'll be creating a ColdFusion file to test our connection to MySQL via ColdFusion. Copy and paste the following text into a new file in Notepad.</p>
<pre class="code"><code class="coldfusion">&lt;cfquery name="CreateNewDatabase" datasource="MySQLDatabase"&gt;
	CREATE TABLE IF NOT EXISTS TestDatabase (
		TestColumn1 varchar(100) default '',
		TestColumn2 int(10) NOT NULL auto_increment,
		PRIMARY KEY (TestColumn2)
	)
&lt;/cfquery&gt;
&lt;cfoutput&gt;If you see this, the table has been created&lt;/cfoutput&gt;</code></pre>
<p>Save this to c:\home\coldfusionmx6_1\CreateMySQLTable.cfm. Hit this page (<a rel="nofollow" href="http://localhost/coldfusionmx6_1/CreateMySQLTable.cfm">http://localhost/coldfusionmx6_1/CreateMySQLTable.cfm</a>), and you should see a message saying "If you see this, the table has been created".</p>
<p>Now log in to MySQL Adminstrator, click on Catalogs, and then on coldfusionmx schemata and you should see your table, with 0 rows and about 16 kB of data length.</p>
<p>If you hit this page again (refresh), you'll notice that you still get the same message, and the table doesn't increase in size, and you don't get another table called TestDatabase.</p>
<h3>Dropping (removing) our test table in MySQL with ColdFusion</h3>
<p>Now, we'll quickly go over deleting, or dropping, TestDatabase.</p>
<p>Create a new CFM file, or add the following to the bottom of the existing CFM file, and save the file.</p>
<pre class="code"><code class="coldfusion">&lt;cfquery name="DropNewDatabase" datasource="MySQLDatabase"&gt;
	DROP TABLE IF EXISTS TestDatabase
&lt;/cfquery&gt;
&lt;cfoutput&gt;If you see this, the table has been dropped&lt;/cfoutput&gt;</code></pre>
<p>If you now run the new file, or the old file with this addition, you'll see a run-on sentence saying that the table has been created, and has been dropped.</p>
<p>If you move into MySQL Administrator, you'll notice that the table has now disappeared.</p>
<p>Congratulations &ndash; you've now setup ColdFusion MX 6.1 to work with MySQL. In a future tutorial, we'll go over setting up PostgreSQL to connect with ColdFusion MX 6.1, and in another tutorial, how to create a form in ColdFusion that will use MySQL data.</p>
<p>Before we leave, note that the table we've setup could also be used by PHP, if we wanted. Additionally, any of the previous tables we've setup in PHP could be accessed by ColdFusion, if we enter them as a data source in ColdFusion Administrator.</p>
<p><a href="http://strivinglife.net/wordpress/a-local-apache-web-server-on-a-windows-xp-computer/">View all of the steps to creating a local Web server, for development.</a></p>
