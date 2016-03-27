+++
title = "Installing MySQL Query Browser 1.1.20 on a local Windows-based, Apache, server"
description = "In this guide, we'll be installing the MySQL Query Browser, version 1.1.20."
draft = false
comments = true
date = "2006-07-08T20:12:00-05:00"
modified = "2007-07-23T22:18:06-05:00"
slug = "Installing-MySQL-Query-Browser-1120-on-a-local-Windows-based-Apache-server"
blogengine = "876902c0-9380-41bd-9525-161d20c89177"
categories = ["tutorials / guides"]
tags = ["mysql"]
+++

<p>
In a previous guide, we installed <a href="http://strivinglife.net/wordpress/?p=53">MySQL</a> and the <a href="http://strivinglife.net/wordpress/?p=55">MySQL Administrator</a>. In this guide, we&#39;ll be installing the MySQL Query Browser, version 1.1.20.
</p>
<!--more-->
<p>
First, we&#39;ll need to download a copy of the latest version from <a href="http://dev.mysql.com/downloads/query-browser/">http://dev.mysql.com/downloads/query-browser/</a> At the time of this writing, that is version 1.1.20. The Windows, x86, version is just over 5 MB, for a MSI file. Once the file has downloaded, open it.<!--adsense-->
</p>
<p>
When you&#39;re presented with the license agreement, read through it and accept to continue. You may as well keep the installation path as the default of C:\Program Files\MySQL\MySQL Query Browser 1.1\, unless you&#39;ve installed the Administrator tool to a different location.
</p>
<p>
For Setup Type, select either Complete or Custom. There&#39;s only one option, so there&#39;s not a real big difference. I&#39;ll select Custom. The Browser will take a little over 10 MB of space, once installed; certainly not a big deal.
</p>
<p>
Finally, press Install, followed by Finish, once the installation is done; it won&#39;t take long.
</p>
<p>
At this point, you may want to create a shortcut to the Browser, in your /home/ directory, as you may have done for the Administrator tool. Another alternative is to create a shortcut to the MySQL System Tray Monitor, which will allow you to launch either of the two tools from the tray.
</p>
<p>
Once you&rsquo;ve done this, or not, start MySQL Query Browser. You can find it either in the installation directory, or in the Start menu, under MySQL. When you start Query Browser up, you&rsquo;ll be asked to supply some information.
</p>
<p>
Server Host: localhost<br />
Username: root<br />
Password: (your password)<br />
Default Schema: (leave blank)
</p>
<p>
You&#39;ll be warned that you should choose a default schema, but let&#39;s just Ignore that for the moment.
</p>
<p>
Since you haven&#39;t selected a default schema, you&#39;ll have to select a schema from the schemata area. Double click on any of the available schemata. Once you do this, the schema will be bold.
</p>
<p>
Now that you&#39;ve selected a schema, you can run a query on the tables to produce some results. If you haven&#39;t already used tables, we can quickly create, and then delete, a table to show how this works.
</p>
<p>
The following query will create a test table.
</p>
<blockquote>
	<p>
	CREATE TABLE IF NOT EXISTS TestDatabase (<br />
	TestColumn1 varchar(100) default &#39;&#39;,<br />
	TestColumn2 int(10) NOT NULL auto_increment,<br />
	PRIMARY KEY (TestColumn2)<br />
	)
	</p>
</blockquote>
<p>
Enter this code, and press Execute. In the bottom left corner, you&#39;ll see that your query returned no results. In addition, it doesn&#39;t look like the database had a table added to it. Right click on the database you&#39;ve selected, and select Refresh. Your test table will now display.
</p>
<p>
You can now run a select on the table, which won&#39;t display any rows, but will display the column names.
</p>
<p>
Finally, we&#39;ll remove the table by running the following query.
</p>
<blockquote>
	<p>
	DROP TABLE TestDatabase
	</p>
</blockquote>
<p>
While no results will be returned, the query will run, and a refresh on the database will show that the table no longer exists.
</p>
<p>
And with that, you&#39;ve got a new way to run queries on your tables, without creating an application file in PHP or ColdFusion.
</p>
<p>
<a href="http://strivinglife.net/wordpress/a-local-apache-web-server-on-a-windows-xp-computer/">View all of the steps to creating a local Web server, for development.</a>
</p>

