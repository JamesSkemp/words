+++
title = "Upgrading (our local install of) ActivePerl"
summary = "In a previous guide, we walked through installing ActivePerl on a local machine. This time, we'll be upgrading ActivePerl. For this guide, we'll be upgrading from ActivePerl 5.8.7.815 to 5.8.8.817.  Note that this guide can also be used in the upgrade to, or installation of, ActivePerl 5.8.8.819."
draft = false
comments = true
date = "2006-05-26T18:36:00-05:00"
modified = "2009-11-07T20:41:04-06:00"
slug = "Upgrading-(our-local-install-of)-ActivePerl"
blogengine = "604840f6-fd00-4675-83e1-dbdbedcc00f3"
categories = ["software", "tutorials / guides"]
tags = ["perl"]
+++

<p>In a <a href="http://strivinglife.com/words/post/Installing-Perl-on-a-local-Windows-based-Apache-server.aspx">previous guide</a>, we walked through installing ActivePerl on a local machine. This time, we'll be upgrading ActivePerl. For this guide, we'll be upgrading from ActivePerl 5.8.7.815 to 5.8.8.817. However, since the installation requires the uninstallation of previous versions of ActivePerl, we'll simply be installing a new version of ActivePerl. If you have not installed Perl before, you can skip ahead to "Installing Perl" below. Please note that this guide will work equally well for the installation of, or upgrade to, ActivePerl 5.8.8.819.</p>
<h3>Uninstalling Perl</h3>
<p>To upgrade Perl, we'll first need to uninstall Perl. Head over to the Windows Control Panel and Add or Remove Programs. Select ActivePerl 5.8.7 Build 815 and Remove the program.</p>
<p>Once the uninstall has finished, you'll need to manually remove every directory in your installation folder with the exception of the site\lib folder. So, if you followed by advice, leave C:\usr\html\site\lib\, but remove everything else. Note that if you haven't done much with ActivePerl, you may want to simply rename the usr folder to usr2, or delete it completely.</p>
<h3>Installing Perl</h3>
<p>Now that we've uninstalled our previous version of Perl, we can install Perl. To install Perl, we're going to download ActivePerl from ActiveState. Navigate to <a rel="external" href="http://www.activestate.com/Products/Download/Download.plex?id=ActivePerl">http://www.activestate.com/Products/Download/Download.plex?id=ActivePerl</a>, and download the MSI file for Windows. When writing this, the current version is 5.8.8.817, and the download size is very large 12.8 MB.</p>
<p>Once we've downloaded this file, we'll open it. Read and accept the license, and on the next screen, leave the installed settings alone, but change the Location from C:\Perl\ to C:\usr\. We'll be doing that in order to keep with Linux (just like we installed our content to C:\home\).</p>
<p>On the next screen, keep the first two boxes checked, and leave everything else unchecked. Finally, hit the Install button to begin the installation.</p>
<p>Once the rather long installation has finished, we may need to modify the Apache httpd.conf file so it can recognize Perl. Note that if you've already installed Perl, you may skip this step safely. However, you may still want to restart Apache.</p>
<h3>Setting up Apache</h3>
<p>To setup Apache to recognize ActivePerl, open up the httpd.conf file as before, using the Start menu or the shortcut in your main Web folder. Now, search for "ExecCGI". Scroll down to the first uncommented line, and add the following information, displayed as bold text.</p>
<blockquote>
<p>Options Indexes FollowSymLinks MultiViews <strong>ExecCGI Includes</strong></p>
</blockquote>
<p>Now do a search for "AddHandler". Scroll down a couple of lines until you reach the commented lines below.</p>
<blockquote>
<p># To use CGI scripts:<br />#<br />#AddHandler cgi-script .cgi<br /><br />#<br /># To use server-parsed HTML files<br />#<br />#AddType text/html .shtml<br />#AddHandler server-parsed .shtml</p>
</blockquote>
<p>Remove the comments from the three lines so that the above becomes the following. Note that lines changed are bold. We'll also add the .pl extension to the end of the first uncommented line, to allow another file type to be run.</p>
<p># To use CGI scripts:</p>
<blockquote>#<br /><strong>AddHandler cgi-script .cgi .pl</strong><br /><br />#<br /># To use server-parsed HTML files<br />#<br /><strong>AddType text/html .shtml</strong><br /><strong>AddHandler server-parsed .shtml</strong></blockquote>
<p>The last two lines will allow us to add simple server-side pages to our site. These files are created on the server, and then displayed to the user. Using server-parsed HTML files, we can create a standard header and footer that is displayed on every page (so long as we tell the page to include it).</p>
<p>Finally, do a search for "ScriptAlias /cgi-bin/" and comment this line. So, when you're done, it should read as follows.</p>
<blockquote>
<p>#ScriptAlias /cgi-bin/ "C:/Program Files/Apache Group/Apache/cgi-bin/"</p>
</blockquote>
<p>This change will allow us to place, and run, CGI scripts in any folder, not just the above folder.</p>
<p>Once these changes have been made, save the httpd.conf file, and restart Apache. Now that Apache has been restarted, we'll test our installation of Perl. To do this, open Notepad and copy or type the following text into it.</p>
<blockquote>
<p>#!/usr/bin/perl<br />print "Content-type:text/html\n\n";<br />print "Hello world!";</p>
</blockquote>
<p>Save this file into C:\home\, and call it TestCGI.cgi. Now, go to <a href="http://localhost/TestCGI.cgi">http://localhost/TestCGI.cgi</a>. The page should load with the text of "Hello world!".</p>
<p><a href="http://strivinglife.net/wordpress/a-local-apache-web-server-on-a-windows-xp-computer/">View all of the steps to creating a local Web server, for development.</a></p>
