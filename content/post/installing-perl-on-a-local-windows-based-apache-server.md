+++
title = "Installing Perl on a local Windows-based, Apache, server"
description = "Now that we've added Apache, configured our log files, and setup a log file analysis tool, it's time to install Perl. Perl will allow us to expand our horizons, and specifically will help us install a better log analyzer."
draft = false
comments = true
date = "2006-02-21T19:12:00-06:00"
modified = "2007-07-31T06:12:15-05:00"
slug = "Installing-Perl-on-a-local-Windows-based-Apache-server"
blogengine = "46c8fc1e-9dde-4d9a-b274-65323e899659"
categories = ["tutorials / guides"]
tags = ["perl", "apache"]
+++

<div class="note">
<p>
<em>Note: This guide should work equally well for ActivePerl 5.8.8.817 and above.  For a guide on upgrading this 5.8.7.815 install, see <a href="http://strivinglife.net/wordpress/?p=142">Upgrading (our local install of) ActivePerl</a>.</em>
</p>
</div>
<p>
Now that we&#39;ve <a href="http://strivinglife.net/wordpress/2006/02/16/45/installing-apache-to-a-windows-based-computer-locally/">installed Apache</a>, configured our log files, and setup a log file analysis tool, it&#39;s time to install Perl. Perl will allow us to expand our horizons, and specifically will help us install a better log analyzer.
</p>
<!--more-->
<p>
To install Perl, we&#39;re going to download ActivePerl from ActiveState. Navigate to <a href="http://www.activestate.com/Products/Download/Download.plex?id=ActivePerl" onclick="window.open(this.href);return false;">http://www.activestate.com/Products/Download/Download.plex?id=ActivePerl</a>, and download the MSI file for Windows. When writing this, the current version is 5.8.7.815, and the download size is very large 12.7 MB.
</p>
<!--adsense-->
<p>
Once we&#39;ve downloaded this file, we&#39;ll open it. Read and accept the license, and on the next screen, leave the installed settings alone, but change the Location from C:\Perl\ to C:\usr\. We&#39;ll be doing that in order to keep with Linux (just like we installed our content to C:\home\).
</p>
<p>
On the next screen, keep the first two boxes checked, and leave everything else unchecked. Finally, hit the Install button to begin the installation.
</p>
<p>
Once the rather long installation has finished, we&#39;ll need to modify the Apache httpd.conf file so it can recognize Perl.
</p>
<p>
To do this, open up the httpd.conf file as before, using the Start menu or the shortcut in your main Web folder. Now, search for &quot;ExecCGI&quot;. Scroll down to the first uncommented line, and add the following information, displayed as bold text.
</p>
<blockquote>
	<p>
	Options Indexes FollowSymLinks MultiViews <strong>ExecCGI Includes</strong>
	</p>
</blockquote>
<p>
Now do a search for &quot;AddHandler&quot;. Scroll down a couple of lines until you reach the commented lines below.
</p>
<blockquote>
	<p>
	# To use CGI scripts:<br />
	#<br />
	#AddHandler cgi-script .cgi<br />
	<br />
	#<br />
	# To use server-parsed HTML files<br />
	#<br />
	#AddType text/html .shtml<br />
	#AddHandler server-parsed .shtml
	</p>
</blockquote>
<p>
Remove the comments from the three lines so that the above becomes the following. Note that lines changed are bold. We&#39;ll also add the .pl extension to the end of the first uncommented line, to allow another file type to be run.
</p>
<p>
# To use CGI scripts:
</p>
<blockquote>
	#<br />
	<strong>AddHandler cgi-script .cgi .pl</strong><br />
	<br />
	#<br />
	# To use server-parsed HTML files<br />
	#<br />
	<strong>AddType text/html .shtml</strong><br />
	<strong>AddHandler server-parsed .shtml</strong>
</blockquote>
<p>
The last two lines will allow us to add simple server-side pages to our site. These files are created on the server, and then displayed to the user. Using server-parsed HTML files, we can create a standard header and footer that is displayed on every page (so long as we tell the page to include it).
</p>
<p>
Finally, do a search for &quot;ScriptAlias /cgi-bin/&quot; and comment this line. So, when you&#39;re done, it should read as follows.
</p>
<blockquote>
	<p>
	#ScriptAlias /cgi-bin/ &quot;C:/Program Files/Apache Group/Apache/cgi-bin/&quot;
	</p>
</blockquote>
<p>
This change will allow us to place, and run, CGI scripts in any folder, not just the above folder.
</p>
<p>
Once these changes have been made, save the httpd.conf file, and restart Apache. Now that Apache has been restarted, we&#39;ll test our installation of Perl. To do this, open Notepad and copy or type the following text into it.
</p>
<blockquote>
	<p>
	#!/usr/bin/perl<br />
	print &quot;Content-type:text/html\n\n&quot;;<br />
	print &quot;Hello world!&quot;;
	</p>
</blockquote>
<p>
Save this file into C:\home\, and call it TestCGI.cgi. Now, go to http://localhost/TestCGI.cgi. The page should load with the text of &quot;Hello world!&quot;.
</p>
<a href="http://strivinglife.net/wordpress/a-local-apache-web-server-on-a-windows-xp-computer/">View all of the steps to creating a local Web server, for development.</a>

