+++
title = "Windows Server 2008 R2, SQL Server Express 2008 R2, and LINQPad"
summary = "Quick steps on getting SQL Server Express 2008 R2 configured on Windows Server 2008 R2 (using Web Platform Installer for installation) so that we can use LINQPad to query it on another server."
draft = false
comments = true
date = "2010-06-26T21:00:00-05:00"
modified = "2010-06-26T17:06:14-05:00"
slug = "Windows-Server-2008-R2-SQL-Server-Express-2008-R2-and-LINQPad"
blogengine = "52c86ad1-702b-4c7b-b7a7-dd82caf54166"
categories = ["tutorials / guides"]
tags = ["linqpad", "sql server express 2008 r2", "windows server 2008 r2"]
+++

<p>This weekend I finally installed SQL Server 2008 R2 to my Windows Server 2008 R2 machine. After a bit of back-and-forth about which version to install (since my MSDN subscription allows me to install seemingly every version), I opted to just install SQL Server Express 2008 R2. Being part of the Web Platform Installer, the entire process was extremely easy.</p>
<p>Step 1: Start Web Platform Installer.</p>
<p>Step 2: Select SQL Server Express 2008 R2 and SQL Server 2008 R2 Management Studio Express from under Database.</p>
<p>Step 3: Press Install.</p>
<p>Step 4: Enter a password for the sa account (since Mixed Mode is what we want for development purposes).</p>
<p>Step 5: Open Windows Firewall and allow C:\Program Files\Microsoft SQL Server\MSSQL10_50.SQLEXPRESS\MSSQL\Binn\sqlservr.exe .</p>
<p>Step 6: Open SQL Server Configuration Manager and turn on the TCP/IP protocol, under Protocols from SQLEXPRESS.</p>
<p>Step 7: Open the TCP/IP protocol and verify that under IPAll TCP Dynamic Ports is set to something over 0. Make note of the port (in my case it was 49306).</p>
<p>Step 8: Still in Configuration Manager, click on SQL Server Services and restart the SQL Server process (the only one that's running).</p>
<p>Step 9: Connect to the instance via Microsoft SQL Server Management Studio, from the server (server name is <strong>.\sqlexpress</strong>).</p>
<p>Step 10: Open LINQPad (4.0 in my case).</p>
<p>Step 11: On the left-hand side select 'Add connection.'</p>
<p>Step 12: LINQ to SQL should already be selected, so press Next.</p>
<p>Step 13: Set the server to the IP of your server \SQLEXPRESS,port. For example: 192.168.1.104\SQLEXPRESS,49306</p>
<p>Step 14: Select SQL Authentication from Log on details, and enter your credentials. Press OK when finished.</p>
<p>And with that, you're set.</p>
