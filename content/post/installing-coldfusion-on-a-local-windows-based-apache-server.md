+++
title = "Installing ColdFusion on a local Windows-based, Apache, server"
description = "In this tutorial, we'll be working through an installation of ColdFusion MX 6.1, Developer's Edition, on a local, Windows-based, Apache server. On this server, we've setup Apache, PHP, and MySQL, but will also want to have the ability to work with ColdFusion code. We'll be doing this to experience a more corporate Web-programming language - corporate primarily because of the costs associated with ColdFusion."
draft = false
comments = true
date = "2006-02-27T10:51:00-06:00"
modified = "2007-09-02T11:11:04-05:00"
slug = "Installing-ColdFusion-on-a-local-Windows-based-Apache-server"
blogengine = "c3ca121b-66a5-45ee-ad8b-0514ef730904"
categories = ["software", "tutorials / guides"]
tags = ["apache", "coldfusion"]
+++

<div class="note">
<p>
<em>Note: For information on installing, or upgrading to ColdFusion MX 7.0.1, see <a href="/words/post/Installing-ColdFusion-MX-701-on-a-local-Windows-based%2c-Apache%2c-server.aspx">Installing ColdFusion MX 7.0.1 on a local Windows-based, Apache, server</a>.</em>
</p>
</div>
<p>
In this tutorial, we&#39;ll be working through an installation of ColdFusion MX 6.1, Developer&#39;s Edition, on a local, Windows-based, Apache server. On this server, we&#39;ve setup Apache, PHP, and MySQL, but will also want to have the ability to work with ColdFusion code (however, not necessarily on the same sites that we&#39;ll be using PHP). We&#39;ll be doing this to experience a more corporate Web-programming language &ndash; corporate primarily because of the costs associated with ColdFusion.
</p>
<!--more--><!--adsense-->
<p>
From the marketing, we see that &quot;the [ColdFusion MX 6.1] Developer Edition, [is] a fully functional server for local development purposes only that helps you learn ColdFusion MX 6.1 or deploy to third-party hosting providers. Access is limited to localhost and one remote IP address.&quot;.
</p>
<p>
We can download the Developer&#39;s Edition directly from Macromedia/Adobe - <a href="http://www.macromedia.com/software/coldfusionmx61/">http://www.macromedia.com/software/coldfusionmx61/</a>. However, you should know that the size of the download is over 150 MB. Also, as the above blurb notes, you most certainly cannot use the Developer&#39;s Edition on anything but a development machine. However, the code we write will work in a production environment.
</p>
<p>
Also note that you could download and install the current 7.x version of ColdFusion (again, Developer Edition) instead of ColdFusion 6.1. I&#39;ll be installing 6.1 simply because I&#39;d like to work in the older environment for purposes of getting help, and helping others. Also, ColdFusion 7 is said, by Macromedia/Adobe, to be an easy upgrade. So, if 7 becomes the one we want to develop for, we can always make the switch.
</p>
<h3>Installing ColdFusion MX 6.1 Developer Edition</h3>
<p>
Once you&#39;ve downloaded the beast of an installation file, you&#39;ll need to install it to use the installed and running Apache Web server. Once you launch the installer, you&#39;ll be able to choose a language (English in my case). Read the introduction, and read and agree to the license agreement.
</p>
<p>
On the next screen, Configure Installer, it will prompt you for a serial number, or will allow you to run the Developer Edition. On the next screen, we&#39;ll select Server configuration, followed by a screen asking us where to install ColdFusion MX. Leave this at the default directory of C:\CFusionMX.
</p>
<p>
Now, we&#39;ll have to select a Web server. We&#39;ll be configuring ColdFusion to use Apache here, so select Add. Select Apache, if it isn&#39;t already selected. In the Configuration Directory field, you&#39;ll want the conf folder in the Apache folder, which is probably something like C:\Program Files\Apache Group\Apache\conf. In the third field, Directory and file name of server binary, you&#39;ll need to tell CF where to find the Apache.exe, which is probably at C:\Program Files\Apache Group\Apache\Apache.exe (if you are using Apache 1.3.x). Click Ok now that the three fields are filled out, followed by a Next.
</p>
<p>
Now, we&#39;ll have to select the web root location for ColdFusion MX Administrator. This is used by ColdFusion to, interestingly enough, administer ColdFusion. We&#39;ll change this directory to our C:\home folder (which is what you&#39;ve set the <strong>DocumentRoot</strong> value to, if you&#39;ve been following along).
</p>
<div class="warning">
<p>
If you set DocumentRoot to something else, you&#39;ll want to make sure that you use that directory here as well.
</p>
<p>
If you&#39;re not sure what you&#39;re using for your directory, go to the Apache install directory and open the conf\httpd.conf file. For example, C:\Program Files\Apache Group\Apache\conf\httpd.conf. Next, do a search for <strong>DocumentRoot</strong>.
</p>
<p>
While you&#39;re here, you can also verify that this same directory is referred to a couple of lines down, which is &quot;&lt;Directory &quot;c:/home&quot;&gt;&quot;, where &#39;c:/home&#39; is your DocumentRoot directory.
</p>
<p>
Thanks to Mike Bryce for pointing this out.
</p>
</div>
<p>
Finally, you&#39;ll be able to review the installation. Note that ColdFusion MX is going to take over 500 MB of space on your hard drive. This is, by far, the most demanding installation on our local Web server. Click Install to begin the installation.
</p>
<p>
Around two hours later (or actually in less than five minutes), ColdFusion MX 6.1 will be up and running. You&#39;ll probably notice a hit to the memory, because ColdFusion is quite the memory hog. We&#39;ll discuss this before we close this post.
</p>
<p>
Once you see the Installation Complete message, you&#39;ll be given the ColdFusion MX Administrator location. If you try to get to it now, however, you may be asked if you want to download the CFM file. Whoops &ndash; not a good thing. What we&#39;ll need to do is configure Apache to recognize CFM files.
</p>
<h3>Configure Apache for ColdFusion</h3>
<p>
Hopefully, you should be able to just restart Apache via the Services panel, and then visit <a href="http://localhost/CFIDE/administrator/index.cfm">http://localhost/CFIDE/administrator/index.cfm</a> one more time. If you don&#39;t see the Configuration and Settings Migration Wizard, then you&#39;ll need to open the httpd.conf file (using either the Start menu or a shortcut you may have created), and do a search for mod_jrun. Verify that the line that contains this text, and &quot;LoadModule&quot;, is not commented out with a # as the first character. If it is, remove the pound sign, save the file, and restart Apache. Hit <a href="http://localhost/CFIDE/administrator/index.cfm">http://localhost/CFIDE/administrator/index.cfm</a> once again.
</p>
<p>
You can now do a search for DirectoryIndex, to verify that index.cfm has been added as a directory index. While you&#39;re here, you may also want to move it&#39;s placement up to after index.php, or even before if you&#39;d like.
</p>
<h3>Configure ColdFusion</h3>
<p>
Now, visit <a href="http://localhost/CFIDE/administrator/index.cfm">http://localhost/CFIDE/administrator/index.cfm</a>, and log in. You&#39;ll now be configuring ColdFusion settings. First, you&#39;ll have the option to disable RDS, which means absolutely nothing to me. An article on sitepoint, <a href="http://www.sitepoint.com/article/install-coldfusion-mx-windows/3">http://www.sitepoint.com/article/install-coldfusion-mx-windows/3</a>, says that there&#39;s little harm on allowing this on a development server. For the widest experience, we&#39;ll leave this as is, and use the same password we just created, for simplicity&#39;s sake.
</p>
<p>
ColdFusion will then install ODBC Services, followed by asking you if you&#39;d like to install example applications. Since this may be helpful, we&#39;ll go ahead and do so. These are installed in C:\home\cfdocs\exampleapps\. And with that, setup is complete. Press OK to load the ColdFusion Administrator (<a href="http://localhost/CFIDE/administrator/index.cfm">http://localhost/CFIDE/administrator/index.cfm</a>).
</p>
<p>
At this point, if you&#39;ve been doing so, you may want to make a backup copy of the httpd.conf file (in C:\Program Files\Apache Group\Apache\conf\). However, this is your call.
</p>
<p>
Now that we&#39;ve installed ColdFusion, we can go about creating sites were we&#39;ll be developing with CF files. Remember that to do this you may want to add VirtualDirectory items into your httpd.conf file, and new IP mappings in your hosts file. For now, have some fun looking at the example applications.
</p>
<p>
Finally, before I close this conversation, one point to add. As I mentioned above, you may have noticed a hit to your available memory after installing ColdFusion MX 6.1. If you open Windows Task Manager and take a look at the processes, you may notice that jrun.exe is using well over 50 MB. If you open up Services and Stop ColdFusion MX Application Server, you&#39;ll notice that this item disappears.
</p>
<p>
Depending upon your system, and how often you&#39;ll be working with ColdFusion (or Apache for that matter), you may want to disable ColdFusion MX from beginning when your computer starts up.
</p>
<p>
If you&#39;re interested in doing this, open the Services panel. Next, right click on the item you would like to stop from starting up on startup, and select Properties. Here, on the General tab, change Startup type from Automatic to Manual (not Disabled). This will ensure that this service only starts up when you manually start it. Note that if I manually start ColdFusion it takes about 30 seconds. If I let it start on startup, it increases my startup time by a little more than that. Again, if you won&#39;t be doing heavy development with ColdFusion, or if you restart your computer on a regular basis, think about changing ColdFusion, or Apache, to startup when you start them.
</p>
<p>
On one final note, you may even want to stop these services when you&#39;re not actively developing with them. Not only will it save memory, it will also close any security holes that these programs may have &ndash; not that that is of major concern.
</p>
<p>
In a future post, we&#39;ll discuss how to hook up MySQL with ColdFusion.
</p>
<p>
<a href="/local-apache-server/">View all of the steps to creating a local Web server, for development.</a>
</p>

