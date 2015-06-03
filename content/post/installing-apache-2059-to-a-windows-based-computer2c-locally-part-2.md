+++
title = "Installing Apache 2.0.59 to a Windows-based computer, locally: Part 2"
description = "In part two of this multi-part guide, we'll be porting over from an Apache 1.3.x Web server to an Apache 2.0.x Web server by adding support for ColdFusion MX 6.1 and 7.0, without having to reinstall either application.  In later guides, we'll be going over how to set back up both PHP 4 and 5, as well as MySQL and PostgreSQL."
draft = false
comments = true
date = "2006-08-25T18:30:00-05:00"
modified = "2009-12-21T08:06:37-06:00"
slug = "Installing-Apache-2059-to-a-Windows-based-computer2c-locally-Part-2"
blogengine = "8adb450b-69cf-43dc-b8bd-85f14111f933"
categories = ["software", "tutorials / guides"]
tags = ["apache", "coldfusion"]
+++

<p>In <a href="http://strivinglife.net/wordpress/2006/08/22/198/installing-apache-2059-to-a-windows-based-computer-locally-part-1/">Part 1 of this Apache 2.0.59 guide</a>, we setup Apache 2.0.59 on a Windows XP SP2 machine. We also setup Perl and mod_perl, attempting to mimic our Apache 1.3.34 install. This time, we'll be continuing in our quest by installing ColdFusion MX 6.1 and 7.</p>
<!--more-->
<h3>Assumptions</h3>
<p>First, I assume that you've already installed ColdFusion MX. Of course, you may not have installed 6.1 and 7, but I'm going to assume you've installed at least one. If you've installed neither, then you may want to check out my <a href="http://strivinglife.net/wordpress/2006/02/27/58/installing-coldfusion-on-a-local-windows-based-apache-server/">guides on ColdFusion MX 6.1</a> and/or <a href="http://strivinglife.net/wordpress/2006/07/12/159/upgrading-our-installation-of-coldfusion-mx-701-on-a-local-windows-based-apache-server/">ColdFusion MX 7</a>.<!--adsense--></p>
<p>Since you'll be making modifications to the httpd.conf file for Apache 2.0.x, you'll also want to back this file up.</p>
<p>It's also important to determine how many installations of ColdFusion MX you'll be doing. You'll need to know this to determine whether or not you'll need to switch between one version of ColdFusion and another. I'm going to assume that you'll be enabling both, so feel free to skip whatever steps as necessary below.</p>
<p>Keep in mind that if you're just going to install ColdFusion MX, then the steps below will not be necessary. This is only if you've already installed ColdFusion MX for Apache 1.3.x.</p>
<h3>Hooking up ColdFusion MX 6.1</h3>
<p>Start by creating a backup copy of the httpd.conf.</p>
<p>When ColdFusion MX 6.1 is installed, it inserts the following lines into the httpd.conf file.</p>
<blockquote>
<p># JRun Settings<br />LoadModule jrun_module "C:/CFusionMX/runtime/lib/wsconfig/1/mod_jrun.so"<br />&lt;IfModule mod_jrun.c&gt;<br />JRunConfig Verbose false<br />JRunConfig Apialloc false<br />JRunConfig Ssl false<br />JRunConfig Ignoresuffixmap false<br />JRunConfig Serverstore "C:/CFusionMX/runtime/lib/wsconfig/1/jrunserver.store"<br />JRunConfig Bootstrap 127.0.0.1:51010<br />#JRunConfig Errorurl &lt;optionally redirect to this URL on errors&gt;<br />AddHandler jrun-handler .jsp .jws .cfm .cfml .cfc<br />&lt;/IfModule&gt;</p>
</blockquote>
<p>Unfortunately, Apache 2.0.x requires a different mod_jrun.so file altogether. This means that we'll need to get a copy of this file, and point our httpd.conf file to it.</p>
<p>What we're first going to do is copy this text into the Apache 2.0.x httpd.conf file. On Apache 1.3.x, ColdFusion MX adds this after the BrowserMatch content, so we'll do a search for BrowserMatch, from the bottom of the file, and add the above lines after the following line.</p>
<blockquote>
<p>BrowserMatch "^Dreamweaver-WebDAV-SCM1" redirect-carefully</p>
</blockquote>
<p>There's some modifications that we'll need to make. As you can see below, I've pointed to the /2/ folder, and mod_jrun20.so file (which doesn't yet exist).</p>
<blockquote>
<p># JRun Settings<br />LoadModule jrun_module "C:/CFusionMX/runtime/lib/wsconfig/2/mod_jrun20.so"<br />&lt;IfModule mod_jrun20.c&gt;<br />JRunConfig Verbose false<br />JRunConfig Apialloc false<br />JRunConfig Ssl false<br />JRunConfig Ignoresuffixmap false<br />JRunConfig Serverstore "C:/CFusionMX/runtime/lib/wsconfig/2/jrunserver.store"<br />JRunConfig Bootstrap 127.0.0.1:51010<br />#JRunConfig Errorurl &lt;optionally redirect to this URL on errors&gt;<br />AddHandler jrun-handler .jsp .jws .cfm .cfml .cfc<br />&lt;/IfModule&gt;</p>
</blockquote>
<p>Now save httpd.conf. Next, head over to the C:\CFusionMX\runtime\lib\wsconfig\ folder. Within this folder there will be a '1' folder, and three files (jrunwin32.dll, wsconfig.log, and wsconfig.properties).</p>
<p>First, create a copy of the '1' folder and call the copy '2'. Next, make a backup copy of the wsconfig.properties file, and open the original in Notepad.</p>
<p>This file currently contains the following information.</p>
<blockquote>
<p>#JRun/ColdFusion MX Web Server Configuration File<br />#Thu Feb 23 19:08:04 GMT-06:00 2006<br />1=Apache,C:/Program Files/Apache Group/Apache/conf,"",C:\\Program Files\\Apache Group\\Apache\\Apache.exe,""<br />1.srv=localhost,"default"<br />1.cfmx=true,&lt;null&gt;</p>
</blockquote>
<p>What we're going to do is copy the last three lines (they all start with '1') to the end of the this file. We're then going to enter a bunch of '2's so that we have the following in this file.</p>
<blockquote>
<p>#JRun/ColdFusion MX Web Server Configuration File<br />#Thu Feb 23 19:08:04 GMT-06:00 2006<br />1=Apache,C:/Program Files/Apache Group/Apache/conf,"",C:\\Program Files\\Apache Group\\Apache\\Apache.exe,""<br />1.srv=localhost,"default"<br />1.cfmx=true,&lt;null&gt;<br />2=Apache,C:/Program Files/Apache Group/Apache2/conf,"",C:\\Program Files\\Apache Group\\Apache2\\Apache.exe,""<br />2.srv=localhost,"default"<br />2.cfmx=true,&lt;null&gt;</p>
</blockquote>
<p>Save and close wsconfig.properties. Now open the '2' folder. There's a mod_jrun.so file here, but as I said earlier, this won't work with Apache 2.0.x. So, we'll need to get the mod_jrun20.so file for Apache 2.0.x. You can get this file by installing ColdFusion and selecting Apache 2.0.x as the server. Since it's not particularly helpful in this case, I did so on another box, and have attached a zip file containing this file here (<a title="mod_jrun20.so" rel="attachment" href="http://strivinglife.com/files/2006/08/mod_jrun20.zip">mod_jrun20.zip</a>).</p>
<p>Save all necessary files and start the Apache2 service (either through the Services panel or through the Apache Services Monitor). Apache 2 should start, and you should be able to access the ColdFusion MX 6.1 Administrator Login.</p>
<p>Now, make a backup copy of the httpd.conf file and call it something like httpd_CFMX6.1.conf. With that, you're ready to either hook-up ColdFusion MX 7, or begin working on ColdFusion on Apache 2.0.x.</p>
<!--nextpage-->
<h3>Hooking up ColdFusion MX 7.0.2</h3>
<p>Start by creating a backup copy of the httpd.conf. If you went through the above steps, then you'll want to grab the pre-ColdFusion MX 6.1 httpd.conf backup file. Otherwise, you can just change the lines that we added above.</p>
<p>When ColdFusion MX 7 is installed, it inserts the following lines into the httpd.conf file.<!--adsense--></p>
<blockquote>
<p># JRun Settings<br />LoadModule jrun_module "C:/CFusionMX7/runtime/lib/wsconfig/1/mod_jrun.so"<br />&lt;IfModule mod_jrun.c&gt;<br />JRunConfig Verbose false<br />JRunConfig Apialloc false<br />JRunConfig Ssl false<br />JRunConfig Ignoresuffixmap false<br />JRunConfig Serverstore "C:/CFusionMX7/runtime/lib/wsconfig/1/jrunserver.store"<br />JRunConfig Bootstrap 127.0.0.1:51011<br />#JRunConfig Errorurl &lt;optionally redirect to this URL on errors&gt;<br />#JRunConfig ProxyRetryInterval 600<br />#JRunConfig ConnectTimeout 15<br />#JRunConfig RecvTimeout 300<br />#JRunConfig SendTimeout 15<br />AddHandler jrun-handler .jsp .jws .cfm .cfml .cfc .cfr .cfswf<br />&lt;/IfModule&gt;</p>
</blockquote>
<p>Unfortunately, Apache 2.0.x requires a different mod_jrun.so file altogether. This means that we'll need to get a copy of this file, and point our httpd.conf file to it.</p>
<p>What we're first going to do is copy this text into the Apache 2.0.x httpd.conf file. On Apache 1.3.x, ColdFusion MX adds this after the BrowserMatch content, so we'll do a search for BrowserMatch, from the bottom of the file, and add the above lines after the following line.</p>
<p>BrowserMatch "^Dreamweaver-WebDAV-SCM1" redirect-carefully</p>
<p>There's some modifications that we'll need to make. As you can see below, I've pointed to the /2/ folder, the mod_jrun20.so file (which doesn't yet exist), and the mod_jrun20.c module.</p>
<blockquote>
<p># JRun Settings<br />LoadModule jrun_module "C:/CFusionMX7/runtime/lib/wsconfig/2/mod_jrun20.so"<br />&lt;IfModule mod_jrun20.c&gt;<br />JRunConfig Verbose false<br />JRunConfig Apialloc false<br />JRunConfig Ssl false<br />JRunConfig Ignoresuffixmap false<br />JRunConfig Serverstore "C:/CFusionMX7/runtime/lib/wsconfig/2/jrunserver.store"<br />JRunConfig Bootstrap 127.0.0.1:51011<br />#JRunConfig Errorurl &lt;optionally redirect to this URL on errors&gt;<br />#JRunConfig ProxyRetryInterval 600<br />#JRunConfig ConnectTimeout 15<br />#JRunConfig RecvTimeout 300<br />#JRunConfig SendTimeout 15<br />AddHandler jrun-handler .jsp .jws .cfm .cfml .cfc .cfr .cfswf<br />&lt;/IfModule&gt;</p>
</blockquote>
<p>Now save httpd.conf. Next, head over to the C:\CFusionMX7\runtime\lib\wsconfig\ folder. Within this folder there will be a '1' folder, and three files (wsconfig.log, and wsconfig.properties).</p>
<p>First, create a copy of the '1' folder and call the copy '2'. Next, make a backup copy of the wsconfig.properties file, and open the original in Notepad.</p>
<p>This file currently contains the following information.</p>
<blockquote>
<p>#JRun/ColdFusion MX Web Server Configuration File<br />#Thu Mar 30 17:54:42 GMT-06:00 2006<br />1=Apache,C:/Program Files/Apache Group/Apache/conf,"",C:\\Program Files\\Apache Group\\Apache\\Apache.exe,"",false<br />1.srv=localhost,"coldfusion"<br />1.cfmx=true,&lt;null&gt;</p>
</blockquote>
<p>What we're going to do is copy the last three lines (they all start with '1') to the end of the this file. We're then going to enter a bunch of '2's so that we have the following in this file.</p>
<blockquote>
<p>#JRun/ColdFusion MX Web Server Configuration File<br />#Thu Feb 23 19:08:04 GMT-06:00 2006<br />1=Apache,C:/Program Files/Apache Group/Apache/conf,"",C:\\Program Files\\Apache Group\\Apache\\Apache.exe,""<br />1.srv=localhost,"default"<br />1.cfmx=true,&lt;null&gt;<br />2=Apache,C:/Program Files/Apache Group/Apache2/conf,"",C:\\Program Files\\Apache Group\\Apache2\\Apache.exe,"",false<br />2.srv=localhost,"coldfusion"<br />2.cfmx=true,&lt;null&gt;</p>
</blockquote>
<p>Save and close wsconfig.properties. Now open the '2' folder. There's a mod_jrun.so file here, but as I said earlier, this won't work with Apache 2.0.x. So, we'll need to get the mod_jrun20.so file for Apache 2.0.x. You can get this file by installing ColdFusion and selecting Apache 2.0.x as the server. Since it's not particularly helpful in this case, I did so on another box, and have attached a zip file containing this file here (<a title="mod_jrun20.so" rel="attachment" href="http://strivinglife.net/wordpress/?attachment_id=200">mod_jrun20.zip</a>).</p>
<p>Save all necessary files and make sure that you rename the cfdocs and cfide folders as necessary (that is, you'll need to make sure you have the CFMX 7 folders available to start ColdFusion MX 7). Start the Apache2 service (either through the Services panel or through the Apache Services Monitor). Apache 2 should start, and you should be able to access the ColdFusion MX 7.0 Administrator Login.</p>
<p>Now, make a backup copy of the httpd.conf file and call it something like httpd_CFMX7.0.conf. With that, you're ready to begin working on ColdFusion on Apache 2.0.x.</p>
<h3>In the next part ...</h3>
<p>In <a href="/words/post/Installing-Apache-2059-to-a-Windows-based-computer-locally-Part-3.aspx">Part 3</a>, we'll go over the PHP 4 and 5 installation. We also still have to connect to MySQL and PostgreSQL (which may end up being Part 4). Until then, have fun in ColdFusion MX on Apache 2!</p>
<p><a href="/local-apache-server/">View all of the steps to creating a local Web server, for development.</a></p>
