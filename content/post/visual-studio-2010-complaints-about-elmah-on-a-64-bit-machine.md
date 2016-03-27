+++
title = "Visual Studio 2010 complaints about ELMAH on a 64-bit machine - fixed"
description = "I recently added ELMAH to an ASP.NET MVC 2 site, but started getting Visual Studio 2010 warnings after. Here's how I resolved the issue."
draft = false
comments = true
date = "2010-08-23T13:44:00-05:00"
modified = "2010-08-23T13:50:18-05:00"
slug = "Visual-Studio-2010-complaints-about-ELMAH-on-a-64-bit-machine"
blogengine = "d53b1f6a-20bb-42b4-8340-22592590ce9a"
categories = ["tutorials / guides"]
tags = ["asp.net", "elmah", "sqlite"]
+++

<p>My laptop has quickly become my development machine for smaller projects, especially after I purchased a low-end desktop to host the Subversion repositories.</p>
<p>I recently added ELMAH support to one of my sites, but since I run 64-bit, and have been using the built-in&nbsp;Cassini for quick development, I started getting a message in Visual Studio 2010 saying "ASP.NET runtime error: Could not load file or assembly 'System.Data.SQLite' or one of its dependencies. An attempt was made to load a program with an incorrect format."</p>
<p>While my low-end desktop has Server 2008 R2 installed on it for research and development purposes (thank you MSDN subscription), having a laptop means I won't always have this resource available. So, since <a rel="external" href="http://stackoverflow.com/questions/1278929/could-not-load-file-or-assembly-system-data-sqlite">Stack Overflow</a> states that this is an issue with Cassini, and I'm running Windows 7 Home Premium, it was time to install IIS 7 on the machine. After a minimal click in the Control Panel and with the hep of Microsoft Web Platform Installer, my IIS instance was setup correctly.</p>
<p>Unfortunately, that requires that Visual Studio 2010 run as administrator (I was afraid I was going to have to update each of my pinned solutions; thankfully you need to (and can only) update this on the main application shortcut), and my MVC 2 project was failing horribly.</p>
<p>Instead of trying to debug this further I kept searching and found another post on <a rel="external" href="http://stackoverflow.com/questions/2814101/unwanted-sqlite-inserted-in-bin">Stack Overflow</a>. After updating my&nbsp;'shared' directory to contain a folder with all of the&nbsp;ELMAH files and&nbsp;another with just the necessary ones, I'm happy to report the errors (warnings)&nbsp;are gone.</p>
<p>My one site is still a mash of the old and new, so I had to manually remove the items from the Bin directory to verify, but things seem just fine.</p>
