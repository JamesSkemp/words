+++
title = "Installing Apache 2.0.59 to a Windows-based computer, locally: Part 1"
description = "In this multi-part guide, we'll be porting over from an Apache 1.3.x Web server to an Apache 2.0.x Web server.  We'll also be going over how to add Perl support, and in later guides, how to setup both PHP 4 and 5, ColdFusion MX 6.1 and 7, as well as MySQL and PostgreSQL."
draft = false
comments = true
date = "2006-08-22T20:13:00-05:00"
modified = "2008-01-15T13:51:02-06:00"
slug = "Installing-Apache-2059-to-a-Windows-based-computer2c-locally-Part-1"
blogengine = "00e1be3f-809b-48d3-969c-aad2dbd9fc5c"
categories = ["software", "tutorials / guides"]
tags = ["apache", "perl"]
+++

<p>
In a previous article, I described <a href="/words/post/Installing-Apache-to-a-Windows-based-computer2c-locally.aspx">how to install Apache 1.3.34</a> to an average home computer, running Windows XP. Since then, only Apache 1.3.35 has been released that would allow me to update my guide, even though the current 1.3.x version is 1.3.37. There&#39;s also a desire on my part to use Apache 2.0, even though my host has not yet begun using them.
</p>
<p>
For that reason, I&#39;ll be walking through a second installation of Apache on a home computer, so that both Apache 1.3.x and Apache 2.0.x can run together (if not at the same time, then at least switchable, as I detailed how to do <a href="/words/post/Dual-installing-PHP-Running-PHP-5-and-4-on-the-same-local2c-Windows-based2c-Apache2c-server.aspx">with PHP</a>).
</p>
<p>
The environment I&rsquo;ll be using is as follows.
</p>
<p>
HP Pavilion a620n<br />
2.20 Ghz, 960 MB (1 GB) of RAM<br />
Windows XP Home, SP2
</p>
<h4>Why would I want to run both Apache 1.3.x and Apache 2.0.x?</h4>
<p>
You may not. In this case, you may simply want to remove Apache 1.3.x (make sure you backup your configuration files, first) and just install Apache 2.0.x. However, since my host uses Apache 1.3.x, I still need to have an older version that I can do testing on. In addition, since I want to write code that can be run on either Apache 1.3 or 2.0, I&#39;ll want to be able to switch between the two for testing purposes. I suppose it&#39;s the same reason I have both ColdFusion 6.1 and 7.0 on my machine.<!--adsense-->
</p>
<h4>Downloading Apache</h4>
<p>
The first thing to do is to download Apache 2.0 from <a href="http://www.apache.org/">http://www.apache.org/</a>. While we could download and run Apache 2.2, I&#39;d much rather install 2.0, since it&#39;s still being developed, and is probably the step most Apache 1.3.x hosts will take next (other than simply upgrading to a higher 1.3 release).
</p>
<p>
Since we&#39;re installing to Windows, we want to download the file apache_2.0.59-win32-x86-no_ssl.msi. This file is under 4.5 MB in size. If you&#39;ve been installing other software with me, then you&#39;ll want to download this to the same location as your other server-related downloads.
</p>
<p>
By the way, if you haven&#39;t been following along, or it&#39;s been a while since you have, you may want to review the &#39;Initial steps before installation area in my <a href="/words/post/Installing-Apache-to-a-Windows-based-computer%2c-locally.aspx">Apache 1.3.34 install guide</a>, as there&#39;s a number of steps you should do while you&#39;re waiting for the download to complete (update your anti-virus software, defragment your hard drive, and determine where you want your site to reside).
</p>
<p>
Once the download has finished, and you&#39;ve reviewed these steps, as necessary, it&#39;s time to start the installation.
</p>
<h4>Installing Apache 2.0.59</h4>
<p>
The first thing we want to do is temporarily stop Apache 1.3.x, if it&#39;s running, and backup the httpd.conf file. Next, start the installer.
</p>
<p>
It&#39;s pretty straightforward for the first two screens, but the third screen contains some information to read over. Eventually, you&#39;ll hit the Server Information screen. We&#39;re only going to run this on localhost, so we&#39;ll use that for the first two fields. Put your real email into the third field, and make sure that you&#39;re running Apache as a service for all users, on Port 80.
</p>
<p>
On the next screen, you can do either a Typical or a Custom install. Select Custom, so we know what is being installed where. First, you&#39;ll determine where Apache is installed. If you click on Apache HTTP Server 2.0.59, you&#39;ll see that the default location is C:\Program Files\Apache Group\. For the sub items, however, the location is C:\Program Files\Apache Group\Apache2\, which is exactly how we want things to be installed. After all, we don&#39;t want to lose our Apache 1.x installation.
</p>
<p>
That&#39;s the only item, so hit Install.
</p>
<p>
If you&#39;re using Windows XP SP2, you&#39;ll probably get prompted on whether you want to block Apache HTTP Server. Unblock this, since you do want the server to run.
</p>
<p>
Other than that, you&#39;ll see that the Installation Wizard has completed, and Apache will be up and running. You can confirm this by checking the running Services, or by looking in your Start panel, where you&#39;ll see the Apache feather near the time. You can also go to <a href="http://localhost/">http://localhost/</a> and see what comes up.
</p>
<h4>Setting up startup types</h4>
<p>
If you don&#39;t have two instances of Apache installed, then you may still want to read this section for the Services Monitor discussion.
</p>
<p>
Now that you&#39;ve got both Apache 1.3.x and Apache 2.0.x installed, you&#39;ve got a problem. Unless you changed Apache 1.3.x&#39;s startup type, it will automatically be starting with Windows. But, so too will Apache 2.0.x. We&#39;ll need to fix this by going to the Services panel, and changing the startup types so that either one or neither startup with Windows.
</p>
<p>
To get to the Services panel, you can either go through the Control Panel in Windows, the Start Menu, through a shortcut or MMC that you&#39;ve setup, or through the Apache Services Monitor. Let&#39;s go through the Apache Services Monitor.
</p>
<p>
You can open this by either using the item in your Start bar. Since you have both Apache and Apache 2, both will show up as Services. However, Apache will have a red dot, and Apache2 a green one.
</p>
<p>
Here we can start, stop, or restart a service. We can also open up the Windows Services panel by clicking on the Services button. For now, let&#39;s do that.
</p>
<p>
We now have to determine which service we want to run at startup, or if we&#39;d rather neither start. If you would rather that Apache 1.3.x start, then either double-click,, or right-click and select Properties, Apache2 and change Startup type to Manual. On the other hand, if you want Apache 2.0.x to start, do the same for the Apache service. If you don&#39;t want either one to start, then change the types for both to Manual.
</p>
<p>
If you wanted to, you could let both run at the same time. The only thing you would need to do is have one listen to one port, and the other listen to another. We setup the configuration file in a bit, we&#39;ll go over how to change the ports.
</p>
<h4>Setting up the Apache 2.0.59 configuration file</h4>
<p>
For now, stop both Apache and Apache2, if either is running, as we&#39;ll be setting up the necessary configuration file for Apache 2.0.59.
</p>
<p>
First find the file at C:\Program Files\Apache Group\Apache2\conf\httpd.conf and make a copy of it, making note in the new file name that this is an original. Now, open the httpd.conf file with Notepad. Note that you can also open this file using the Start menu, but since we&#39;re making a backup copy, it makes sense to go directly to it.
</p>
<p>
At this point you&#39;ll need to know where you&#39;re storing your Web files. I decided to install them directly into a folder off of the c drive, so I store my files in C:\home\, with a directory for each site, as necessary.
</p>
<p>
Do a search first for DocumentRoot. Following the standard given, change this to the folder where you are storing your files. So, in my example, this line was changed from
</p>
<blockquote>
	<p>
	DocumentRoot &quot;C:/Program Files/Apache Group/Apache2/htdocs&quot;
	</p>
</blockquote>
<p>
to
</p>
<blockquote>
	<p>
	DocumentRoot &quot;c:/home&quot;
	</p>
</blockquote>
<p>
Scroll down a little and you&#39;ll see the following line
</p>
<blockquote>
	<p>
	&lt;Directory &quot;C:/Program Files/Apache Group/Apache2/htdocs&quot;&gt;
	</p>
</blockquote>
<p>
which should also be changed to match what you used for DocumentRoot.
</p>
<p>
If you scroll up a little bit, you&#39;ll see a line that is as follows.
</p>
<blockquote>
	<p>
	Port 80
	</p>
</blockquote>
<p>
This is where you can change what port Apache2 should listen to. If you really want to, you can change this, otherwise I&#39;d just as soon recommend that you just run Apache or Apache2, but not at the same time. Since you&#39;re installing to a home computer, you don&#39;t really need to be running both at the same time. Besides, we can write a batch file which will automate the stopping and starting procedure for you, with one click (I&#39;ll detail this below).
</p>
<p>
For now, Start Apache2 (or if you didn&#39;t listen to me above, restart Apache2). Note that if you go to <a href="http://localhost/">http://localhost/</a> before you do this, you&#39;ll either go nowhere, or to the old DocumentRoot, depending upon whether you&#39;ll be starting or restarting Apache2. Changes to the httpd.conf file only take once Apache is restarted.
</p>
<p>
Once you start Apache2 and go back to <a href="http://localhost/">http://localhost/</a>, you&#39;ll find that you do go to the correct directory. Horray!
</p>
<h4>Moving along ...</h4>
<p>
At this point, things get a little tricky. Depending upon how many of my guides you&#39;ve followed, you&#39;ll need any of the following functionality added to Apache 2.0.59;
</p>
<ul>
	<li>Perl</li>
	<li>PHP (4 and/or 5)</li>
	<li>MySQL</li>
	<li>ColdFusion (6.1 and/or 7.0)</li>
	<li>PostgreSQL</li>
</ul>
<p>
There&#39;s also subdomains that you may have setup that will need to be re-setup.
</p>
<p>
Below, I&#39;ll detail how to do each of these steps. You can then select whatever applies to you. All we really have to do is setup Apache 2.0.59 to recognize the functionality above, since we&#39;ve already installed them once for Apache 1.3.x. However, it&#39;s also possible that you&#39;ll want to install some of these for the first time, using Apache 2.0.x instead of Apache 1.3.x.
</p>
<p>
In that case, you can either wait for me to go over it (which I do plan on doing) or take a look at both the original guide working with Apache 1.3.x and the steps I setup below to get Apache 2.0.x working. You can also email me personally, or post a comment on this article, or the previous articles. Either way I should get back to you with some kind of answer.
</p>
<p>
First, however, we&#39;ll setup the batch file that I mentioned above. Then we&#39;ll go over each of the above implementations.
</p>
<!--nextpage-->
<h4>Creating a batch file to switch between Apache and Apache2</h4>
<p>
As I stated above, we can either have Apache and Apache2 listen to both ports, or simply have one run at a time. To make switching easier, we can write a Windows batch file that will allow us to stop one version of Apache and start the other, with just a couple actions.<!--adsense-->
</p>
<p>
In a previous guide, we mentioned how to create a batch file that would restart Apache.
</p>
<blockquote>
	<p>
	net stop &ldquo;Apache&rdquo;<br />
	net start &ldquo;Apache&rdquo;
	</p>
</blockquote>
<p>
Now, we&#39;ll create a script that will start Apache, and stop Apache2, if it&#39;s running.
</p>
<blockquote>
	<p>
	net stop &ldquo;Apache&rdquo;<br />
	net stop &ldquo;Apache2&rdquo;<br />
	net start &ldquo;Apache&rdquo;
	</p>
</blockquote>
<p>
We want to stop both, just in case either one is running. We can then start Apache back up.
</p>
<p>
To start Apache2, and stop Apache, we just change that last line.
</p>
<blockquote>
	<p>
	net stop &ldquo;Apache&rdquo;<br />
	net stop &ldquo;Apache2&rdquo;<br />
	net start &ldquo;Apache2&rdquo;
	</p>
</blockquote>
<p>
And with that, we&#39;ve got the makings of two batch files that we can run.
</p>
<p>
Open Notepad and copy and paste the first block of three lines into it. Now, save this as something like _Apache_start1.bat. In a new file, copy and paste the second block of three lines into it, and call this one something like _Apache_start2.bat.
</p>
<p>
Now make sure these are where you can get to them easily, and run either one. Check either the Apache Services Monitor or the Services panel to verify that the batch file ran correctly. Navigating to <a href="http://localhost/">http://localhost/</a> should display correctly as well.
</p>
<p>
With this new script in place, you can now delete any old &#39;restart Apache&#39; batch files you may have had, since you&#39;ve now got a new, better, one. Of course, if you do opt to remove either Apache or Apache2, you&#39;ll want to remove the respective line from these files, since one less line is one less process (which will be a wasted process).
</p>
<p>
You&#39;ve now got two files that you can easily run to switch between Apache 1.3.x and Apache 2.0.x. In the later sections, we&#39;ll write a number of other batch files that we can run for similar effects.
</p>
<h4>The Perl installation</h4>
<p>
At this point, you&#39;ve probably already got ActivePerl installed (but if you don&#39;t, time to check out the first four paragraphs in the <a href="/words/post/Installing-Perl-on-a-local-Windows-based%2c-Apache%2c-server.aspx">previous guide covering the ActivePerl installation</a>).
</p>
<p>
Now that you&#39;ve got ActivePerl installed, we&#39;re going to hook it up with Apache 2.
</p>
<p>
Head-over to the location of the httpd.conf file (C:\Program Files\Apache Group\Apache2\conf\ if you&#39;ve been following along) and make a backup copy. You&#39;ve already made an original backup, so perhaps call this one httpd_basicsetup.conf (or whatever makes sense to you). Once the backup has been made, open up the httpd.conf file with Notepad.
</p>
<p>
Next, do a search for <em>ExecCGI</em>, and scroll down to the first uncommented line.
</p>
<blockquote>
	<p>
	Options Indexes FollowSymLinks
	</p>
</blockquote>
<p>
Add two words to the end of this, so that the line reads as follows.
</p>
<blockquote>
	<p>
	Options Indexes FollowSymLinks <strong>ExecCGI Includes</strong>
	</p>
</blockquote>
<p>
Next, do a search for <em>cgi-script</em>, which should place you in the following line.
</p>
<blockquote>
	<p>
	#AddHandler cgi-script .cgi
	</p>
</blockquote>
<p>
Simply remove the pound sign and add <em>.pl</em> at the end of the line to continue. Likewise, remove the pound sign from the following two lines as well, which are just a handful of lines further down.
</p>
<blockquote>
	<p>
	#AddType text/html .shtml<br />
	#AddOutputFilter INCLUDES .shtml
	</p>
</blockquote>
<p>
Finally, find the following line and add a pound sign in front of it (to comment it out).
</p>
<blockquote>
	<p>
	ScriptAlias /cgi-bin/ &quot;C:/Program Files/Apache Group/Apache2/cgi-bin/&quot;
	</p>
</blockquote>
<p>
This will allow you to run CGI scripts from any folder, and not just this one.
</p>
<p>
Now that we&#39;ve made these changes, save the httpd.conf file and restart Apache 2.
</p>
<p>
If you now go to <a href="http://localhost/">http://localhost/</a>, your DocumentRoot content should display. Next, open up a new Notepad file and add the following text.
</p>
<blockquote>
	<p>
	#!/usr/bin/perl<br />
	print &quot;Content-type:text/html\n\n&quot;;<br />
	print &quot;Hello world!&quot;; 
	</p>
</blockquote>
<p>
Save this into your DocumentRoot folder (for example, c:\home\ if you&#39;ve been following along) and call it something like TestCGI.cgi. If you hit this page, <a href="http://localhost/TestCGI.cgi">http://localhost/TestCGI.cgi</a>, the page should load with the text of &ldquo;Hello world!&rdquo;.
</p>
<p>
With the installation complete, you&#39;ll want to close the httpd.conf file and then make a copy of it, calling it something like httpd_perl.conf.
</p>
<p>
Now you&#39;ve got Perl hooked-up, so you can continue on with the additional components you need to add.
</p>
<!--nextpage-->
<h4>The mod_perl installation</h4>
<p>
Unfortunately, with the mod_perl installation, we&#39;re actually going to have to download a file from the Internet, since the mod_perl for Apache 1.x is not the same as the one for Apache 2.x.<!--adsense-->
</p>
<p>
Head over to <a href="http://perl.apache.org/">http://perl.apache.org/</a> and select the &ldquo;Download&rdquo; link. Next, select the &ldquo;Binary mod_perl distributions&rdquo; link, and Win32 Active Perl under &#39;How to get pre-compiled mod_perl 1.0&#39;. The linked to paragraph actually includes a link to the mod_perl 2.0 ppm, which eventually leads us to <a href="http://theoryx5.uwinnipeg.ca/ppms/x86/">http://theoryx5.uwinnipeg.ca/ppms/x86/</a>
</p>
<p>
Scroll to the bottom of the page and find the mod_perl.so file. FYI, the mod_perl1.so file is for Apache 1.x, the mod_perl-2.2.so file is for Apache 2.2.x, and this file, mod_perl.so, is for Apache 2.0.x. Download this file (Save as) to your standard server downloads folder (for example, c:\home\downloads\).
</p>
<p>
We&#39;ll install this file in just a couple of steps. First, open up the Services panel, if it&#39;s not already started. If you click on Apache2, you&#39;ll probably see a description of &#39;Apache/2.0.59 (Win32)&#39;. If you have Apache installed, click on Apache and see what the description is. This will be another way to determine whether our mod_perl installation has been successful.
</p>
<p>
Copy the mod_perl.so file into the modules folder under Apache2 (C:\Program Files\Apache Group\Apache2\modules\).
</p>
<p>
Next, go up to the conf folder and make sure that you&#39;ve got a recent backup of httpd.conf. Finally, open httpd.conf up and get ready for some editing.
</p>
<p>
The httpd.conf file updates are pretty easy. First, do a search for mod_foo. At the end of the LoadModule lines, add the following.
</p>
<blockquote>
	<p>
	LoadFile &quot;c:/usr/bin/perl58.dll&quot;<br />
	LoadModule perl_module modules/mod_perl.so 
	</p>
</blockquote>
<p>
Note that if perl58.dll (from ActivePerl) is in a different location, change this location.
</p>
<p>
If you&#39;ve followed by Perl guidelines, then you can skip the next step. Otherwise, search for cgi-script and add .pl to that line so that it reads as follows. Note, you may need to uncomment this line as well.
</p>
<blockquote>
	<p>
	AddHandler cgi-script .cgi .pl
	</p>
</blockquote>
<p>
Save httpd.conf and restart Apache2. The description should show that you&#39;ve correctly setup mod_perl.
</p>
<p>
If you&#39;ve successfully installed mod_perl, then backup your httpd.conf file (as httpd_mod_perl.conf, for example). And with that, you&#39;re ready to move on.
</p>
<h4>In the next part ...</h4>
<p>
In <a href="/words/post/Installing-Apache-2059-to-a-Windows-based-computer2c-locally-Part-2.aspx">part two</a>, we&#39;ll be covering PHP 4 and 5, as well as ColdFusion MX 6.1 and 7. We&#39;ll also be going over MySQL and PostgreSQL.
</p>
<p>
<a href="/local-apache-server/">View all of the steps to creating a local Web server, for development.</a>
</p>

