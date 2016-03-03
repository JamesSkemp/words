+++
title = "The problem with installing SQL Server Express via the Microsoft Web Platform Installer"
summary = "If you use Web Platform Installer to install SQL Server Express, you might be in for a surprise if you try to install AdventureWorks."
draft = false
comments = true
date = "2010-12-26T20:15:00-06:00"
modified = "2010-12-26T20:24:44-06:00"
slug = "The-problem-with-installing-SQL-Server-Express-via-the-Microsoft-Web-Platform-Installer"
blogengine = "0f22f08e-3d77-4e64-a857-4caa86ab61d0"
categories = ["software"]
tags = ["microsoft web platform installer", "mssql"]
+++

<p>In <a href="http://strivinglife.com/words/?tag=/microsoft-web-platform-installer">the past</a> I've talked up Microsoft's <a rel="external" href="http://www.microsoft.com/web/">Web Platform Installer</a>. With this tool installed you can easily get an IIS server correctly setup.</p>
<p>However, as I work my way through Pete Brown's <a rel="external" href="http://www.amazon.com/gp/product/1935182374?tag=strivinglifen-20">Silverlight 4 in Action</a> I found myself needing to install AdventureWorks (something I had looked into in the past as well). Unfortunately, Web Platform Installer installs one of the 'lower' versions of SQL Server Express, without the advanced services, which is required for AdventureWorks.</p>
<p>You might expect that you'd be able to upgrade via the full installer, but after a couple hours of trying to get that to work, that just doesn't seem to be the case. It doesn't appear that you can install over it, nor select the new installer in add/remove programs, which means that I've had to uninstall SQL Server Express, then completely re-install it with the missing features.</p>
<p>Very disappointing, to say the least.</p>
<p>For development purposes I probably won't use the Web Platform Installer to install SQL Server locally again, but will definitely use it for remote servers, assuming that I don't require the functionality built into the Advanced Services installer (which I undoubtedly will not). Of course, since I have an MSDN subscription, I believe I can install a more robust version of SQL Server for development purposes anyways, so perhaps this will push me over the edge.</p>
