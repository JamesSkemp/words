+++
title = "Upgrading our installation of ColdFusion MX 7.0.1 on a local Windows-based, Apache, server"
description = "In a previous guide, we installed ColdFusion MX 6.1 and ColdFusion MX 7.0.1. In this guide, we'll be leaving our installation of ColdFusion MX 6.1, and upgrading our installation of ColdFusion MX 7.0.1 to 7.0.2."
draft = false
comments = true
date = "2006-07-12T20:16:00-05:00"
modified = "2007-09-06T22:20:13-05:00"
slug = "Upgrading-our-installation-of-ColdFusion-MX-701-on-a-local-Windows-based-Apache-server"
blogengine = "3b9a26cf-685f-4b5e-9423-20ff8fa3a2d1"
categories = ["tutorials / guides"]
tags = ["coldfusion"]
+++

<p>
In a previous guide, we installed <a href="http://strivinglife.com/words/post/Installing-ColdFusion-on-a-local-Windows-based%2c-Apache%2c-server.aspx">ColdFusion MX 6.1</a> and <a href="http://strivinglife.com/words/post/Installing-ColdFusion-MX-701-on-a-local-Windows-based%2c-Apache%2c-server.aspx">ColdFusion MX 7.0.1</a>. In this guide, we&#39;ll be leaving our installation of ColdFusion MX 6.1, and upgrading our installation of ColdFusion MX 7.0.1 to 7.0.2.
</p>
<h4>Downloading the updater</h4>
<p>
ColdFusion MX 7.0.2 can either be downloaded as a full installer, or as a simple updater. Since we&#39;ve already installed 7.0.1, we can just use the updater. Go to <a href="http://www.adobe.com/support/coldfusion/downloads_updates.html">http://www.adobe.com/support/coldfusion/downloads_updates.html</a> and download the current updater, ColdFusion MX 7 Updater 2 (7.0.2) for Windows. The size of this file is almost 50 MB, so you may have a bit of wait.
</p>
<h4>Preparation</h4>
<p>
If you&#39;re running both ColdFusion MX 6.1 and 7, you&#39;ll want to make sure that you&#39;ve stopped 6.1, and the correct 7 folders in their right place. The best way to test this is to start ColdFusion MX 7.0.1 and visit the ColdFusion Administrator.
</p>
<p>
You may also want to make a backup of your httpd.conf files for Apache (at C:\Program Files\Apache Group\Apache\conf).
</p>
<h4>Updating</h4>
<p>
Once you&#39;ve verified that your folders are in the correct places, you can start the updater.
</p>
<p>
Read the Introduction, and the license agreement, and either agree or not with the latter, clicking Next as you go.
</p>
<p>
When you&#39;re asked to &ldquo;select the ColdFusion MX 7 installation configuration that you want to update&rdquo;, select &ldquo;Server configuration&rdquo;. Click Next.
</p>
<p>
On the next screen, you&#39;ll be told to &ldquo;shut down all ColdFusion MX 7 services and web server services&rdquo;. So, head over to Services, and stop &ldquo;ColdFusino MX 7 Application Server&rdquo;, &ldquo;ColdFusion MX 7 ODBC Agent&rdquo;, &ldquo;ColdFusion MX 7 ODBC Server&rdquo;, and &ldquo;ColdFusion MX 7 Search Server&rdquo;. You&#39;ll also want to stop Apache. Continue.
</p>
<p>
If you changed the install folder for ColdFusion MX 7, then you&#39;ll need to enter that on the next screen. Otherwise, accept the default of &#39;C:\CFusionMX7&#39;. You&#39;ll also need to select the CFIDE directory.
</p>
<p>
The Updater will then report the required and available disk space on your computer. If you&#39;ve enough space, &#39;Install&#39;. Once the install has finished, you can press Done to finish the installation.
</p>
<p>
The Application Server should automatically start, but you&#39;ll have to start the remaining ColdFusion services, and Apache.
</p>
<h4>Verifying the update</h4>
<p>
Once you&#39;ve started the necessary services, log into the ColdFusion Administrator. You should notice that ColdFusion has been updated to 7.0.2 (via System Information). You can also verify your Data Sources to verify that you&#39;re still able to connect.
</p>
<p>
If you&#39;ve installed ColdFusion MX 6.1, and still have it installed, you may want to also verify that you&#39;re still able to switch correctly.
</p>
<p>
The update should not have had any effect upon your httpd.conf file, but you&#39;ll want to verify this for yourself, and make any necessary backups.
</p>
<p>
Assuming everything checks out, you&#39;ve safely upgraded ColdFusion MX 7.0.1 to ColdFusion MX 7.0.2!
</p>
<p>
<a href="http://strivinglife.com/local-apache-server/">View all of the steps to creating a local Web server, for development.</a>
</p>

