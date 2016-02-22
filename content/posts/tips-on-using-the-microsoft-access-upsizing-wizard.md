+++
title = "Tips on using the Microsoft Access Upsizing Wizard"
summary = "Some tips I have now that I've successfully imported data from Microsoft Access (XP/2002) to SQL Server Express (2005). [slnet0514:9ff303ee-acf3-49b5-9fe1-0ff6d7b6a9c3]"
draft = false
comments = true
date = "2008-02-24T13:15:00-06:00"
modified = "2009-10-20T17:58:42-05:00"
slug = "Tips-on-using-the-Microsoft-Access-Upsizing-Wizard"
blogengine = "9ff303ee-acf3-49b5-9fe1-0ff6d7b6a9c3"
categories = ["software", "tutorials / guides"]
tags = []
+++

<p>
In no particular order, here are some tips if you&#39;re using the Microsoft Access Upsizing Wizard to convert your Access database to SQL (SQL Express 2005, in my case). 
</p>
<h3>The tips</h3>
<p>
Make sure you&#39;ve downloaded the Microsoft SQL Server Management Studio Express tools as well. 
</p>
<p>
When connecting with the above, make note of the server you&#39;re connecting to; you&#39;ll need this for later. For example, <strong>PAVA620N\SQLEXPRESS</strong> (that&#39;s computer name \ instance name of SQL Server). 
</p>
<p>
Setup the ODBC connection before attempting to move the data over. Administrative Tools &gt; Data Sources (ODBC) 
</p>
<p>
Close out of all tables and forms before using the Upsizing Wizard (not a big deal, as it&#39;ll prompt you). 
</p>
<p>
When connecting to the SQL Server, use the computer name \ instance name, instead of <strong>(local)</strong>. At least, it didn&#39;t work for me. 
</p>
<p>
Supposedly there may be issues if you try to&nbsp;upsize tables with date columns. 
</p>
<p>
The error you get when a table doesn&#39;t get upsized is not helpful.&nbsp;&quot;Table was skipped or export failed.&quot;&nbsp; Yeah ... 
</p>
<p>
Are you using any OLE Object columns?&nbsp;That was my problem. Check also for date columns. 
</p>
<p>
If you use an existing database, it&#39;ll import the new table(s) into whatever you&#39;ve setup as your default db for the ODBC connection. 
</p>

