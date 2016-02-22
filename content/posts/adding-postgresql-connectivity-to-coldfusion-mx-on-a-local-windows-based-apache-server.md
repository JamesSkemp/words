+++
title = "Adding PostgreSQL connectivity to ColdFusion MX on a local Windows-based, Apache, server"
summary = "Having already added MySQL support for ColdFusion MX, it's time to look at adding PostgreSQL. For many of the same reasons we installed PostgreSQL with PHP, we'll be doing this to add to our potential resources. However, unlike our connection of MySQL with ColdFusion MX, we'll need to install some additional features to ColdFusion MX."
draft = false
comments = true
date = "2006-03-19T06:18:00-06:00"
modified = "2009-12-20T18:30:19-06:00"
slug = "Adding-PostgreSQL-connectivity-to-ColdFusion-MX-on-a-local-Windows-based-Apache-server"
blogengine = "496af382-5a35-4f12-a90e-0604a69b958a"
categories = ["tutorials / guides"]
tags = ["postgresql", "coldfusion"]
+++

<p>Having already <a href="http://strivinglife.com/words/post/Adding-MySQL-connectivity-to-ColdFusion-MX-on-a-local-Windows-based-Apache-server.aspx">added MySQL support for ColdFusion MX</a>, it's time to look at adding PostgreSQL. For many of the same reasons we installed PostgreSQL with PHP, we'll be doing this to add to our potential resources. However, unlike our connection of MySQL with ColdFusion MX, we'll need to install some additional features to ColdFusion MX.</p>
<p>(This guide assumes you've already <a href="http://strivinglife.com/words/post/Installing-PostgreSQL-on-a-local-Windows-based-Apache-server.aspx">installed PostgreSQL</a>.)</p>
<h3>Downloading and installing the JDBC Driver</h3>
<p>The first thing we'll need to do is install a special driver for ColdFusion. This driver can be found at <a href="http://jdbc.postgresql.org/">http://jdbc.postgresql.org/</a>. Select Download from the left-side navigation, and you'll be presented with a lot of options. Before we go any further, we'll need to determine what version we'll need to download, which will involve determining our version of JDK.</p>
<p>To determine this, find where you installed ColdFusion MX, and look in the runtime\jre\ folder. If you're not sure of where this is, make sure ColdFusion is started and open the ColdFusion Administrator (<a href="http://localhost/CFIDE/administrator/index.cfm">http://localhost/CFIDE/administrator/index.cfm</a> if you've been following along).</p>
<p>Now, select Java and JVM under SERVER SETTINGS, on the left side. You'll now see a box detailing the Java Virtual Machine Path. Go to this location and open the README.txt file. Here, you'll be able to determine the version. You can also determine your version by checking the Server Information under ColdFusion Administrator. If you've been following along, you're probably using version 1.4.2. Because of this, and because we're using PostgreSQL 8.1, we'll download the JDBC 3, 8.1 Build 405 version (8.1-405 JDBC 3), which is about 400 KB. Save this to your downloads directory.</p>
<p>Now copy this file and move it to C:\CFusionMX\wwwroot\WEB-INF\classes, if you've installed ColdFusion to c:\CFusionMX\. Otherwise, substitute as necessary.</p>
<p>Now, enter the path and name of this file into the Class Path field in ColdFusion Administrator, with a comma at the end. For example, "C:/CFusionMX/wwwroot/WEB-INF/classes/postgresql-8.1-405.jdbc3.jar," (no quotes). Note that we've replaced the '\' with '/' in the path. Now Submit Changes.</p>
<p>Next, open the file at C:\CFusionMX\lib\neo-query.xml in Notepad. Do a search for postgresql, and scroll through until you find the following:</p>
<pre class="code"><code class="xml">&lt;var name='handler'&gt;&lt;string&gt;postgresql.cfm&lt;/string&gt;&lt;/var&gt;</code></pre>
<p>Change this to:</p>
<pre class="code"><code class="xml">&lt;var name='handler'&gt;&lt;string&gt;default.cfm&lt;/string&gt;&lt;/var&gt;</code></pre>
<p>Finally, restart ColdFusion via the Services panel. Note that it may take a little longer for ColdFusion to start, since we've added a new class for ColdFusion to load.</p>
<p>Finally, log back into ColdFusion Administrator and select Data Sources under DATA &amp; SERVICES.</p>
<h3>Creating a new database in PostgreSQL</h3>
<p>The first thing we'll need to do is create a new database in PostgreSQL. Start pgAdmin and connect to the PostgreSQL Database Server 8.1.</p>
<p>Once you've connected, right click on Databases (1), and select New Database. Type in a Name (I used ColdFusion), select an Owner (we'll just use postgres for now), and select a Tablespace (pg_default). Now hit OK.</p>
<h3>Adding PostgreSQL as a data source</h3>
<p>We'll now add PostgreSQL as a data source in ColdFusion Administrator. In the Data Source Name, type in PostgreSQL, and select other for Driver. Now hit Add.</p>
<p>JDBC URL: jdbc:postgresql://localhost:5432/ColdFusion<br />Driver Class: org.postgresql.Driver<br />Driver Name: PostgreSQL<br />Username: postgres<br />Password: your_password (note, this will have been the second password you used, not the first)<br />Description: PostgreSQL database for ColdFusion MX 6.1. (or whatever you want to type)</p>
<p>Note that for JDBC URL, 'ColdFusion' should match the name of the database you created in PostreSQL above. Other than that and Username, your settings should match mine above. Once you do this, it should verify as OK. You can optionally Verify All Connections to verify them all.</p>
<p>Creating a PostgreSQL table in ColdFusion</p>
<p>We'll now create a new file in Notepad and paste the following text within it, to test our ColdFusion to PostgreSQL connection.</p>
<pre class="code"><code class="coldfusion">&lt;cfquery name="CreateNewDatabase" datasource="PostgreSQL"&gt;
CREATE TABLE TestDatabase (
	TestColumn1 text,
	TestColumn2 text
);
CREATE UNIQUE INDEX TestDatabase_TestColumn1_TestColumn2_uidx ON TestDatabase (TestColumn1,TestColumn2);
&lt;/cfquery&gt;
&lt;cfoutput&gt;If you see this, the table has been created&lt;/cfoutput&gt;</code></pre>
<p>Save and run this file (<a href="http://localhost/coldfusionmx6_1/CreatePostgreSQLTable.cfm">http://localhost/coldfusionmx6_1/CreatePostgreSQLTable.cfm</a>), and you should see a notification that the table has been created.</p>
<p>If pgAdmin isn't still running, start it up and dig way down to find this table: PostgreSQL Database Server 8.1 &gt; Databases &gt; ColdFusion &gt; Schemas &gt; public &gt; Tables &gt; testdatabase. Whew.</p>
<p>Note that if you run this file again, you'll receive an error message, saying that the table already exists. Because we haven't added a check into this code to verify whether the table already exists, we'll hit a wall. Obviously, we'd have to add this code in in the real world.</p>
<h3>Dropping/deleting our test table</h3>
<p>Once you've verified that you can create a table, it's time to delete it. Add the following code to the end of the existing code, or create a new document with this code:</p>
<pre class="code"><code class="coldfusion">&lt;cfquery name="DropNewDatabase" datasource="PostgreSQL"&gt;
	DROP TABLE TestDatabase
&lt;/cfquery&gt;
&lt;cfoutput&gt;If you see this, the table has been dropped&lt;/cfoutput&gt;</code></pre>
<p>Run this code, and check pgAdmin to verify that the table no longer exists.</p>
<p>Again, note that if you run this code (just this last part), and the table already has been dropped, you'll get an error. Again, something that would have to be fixed in the real world.</p>
<p>Congratulations once again, as you've successfully setup ColdFusion and PostgreSQL.</p>
<p>As with MySQL, you can access any tables you setup in ColdFusion with PHP, and vice versa, so long as ColdFusion has the data source entered into ColdFusion Administrator.</p>
<p><a href="http://strivinglife.net/wordpress/a-local-apache-web-server-on-a-windows-xp-computer/">View all of the steps to creating a local Web server, for development.</a></p>
