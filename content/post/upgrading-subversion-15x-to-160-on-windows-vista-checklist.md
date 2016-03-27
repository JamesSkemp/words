+++
title = "Upgrading Subversion 1.5.x to 1.6.0 on Windows Vista - checklist"
description = "Subversion 1.6.0 released a short time ago, and all the Windows binaries are ready to go. Here's a checklist (which should be applicable for future use) on Subversion, Apache, and TortoiseSVN upgrading."
draft = false
comments = true
date = "2009-03-23T20:40:00-05:00"
modified = "2009-07-22T21:46:32-05:00"
slug = "Upgrading-Subversion-15x-to-160-on-Windows-Vista-checklist"
blogengine = "5b239e61-853b-4a85-a9a6-71ff78f3f158"
categories = ["article", "tutorials / guides"]
tags = ["apache", "tortoisesvn", "subversion", "svn"]
+++

<p>The following is how I went about performing an upgrade of Subversion 1.5.4 to Subversion 1.6.0.</p>
<p>For this I'll be continuing to use the current Windows build of Apache 2.2.x, TortoiseSVN, and of course Subversion. At this time, that's Subversion 1.6.0, TortoiseSVN 1.6.0, and Apache 2.2.11.</p>
<ol>
<li>
<div>Determine current setup.</div>
<ol>
<li>
<div>Opening the Apache Service Monitor will show the version of Apache and Subversion. In my case, that's 2.2.10 and 1.5.4, respectively.</div>
</li>
<li>
<div>Opening TortoiseSVN's menu and selecting About will display the current version. In my case that's 1.5.8.</div>
</li>
</ol></li>
<li>
<div>Confirm that all applications will work with the new versions of the other applications.</div>
<ol>
<li>
<div>Simply check each application's site. In this case, they all appear to work fine with each other.</div>
</li>
</ol></li>
<li>
<div>Download all installers.</div>
<ol>
<li>
<div>Apache: <a href="http://httpd.apache.org/">http://httpd.apache.org/</a></div>
<ol>
<li>
<div>Win32 Binary including OpenSSL 0.9.8i (MSI Installer)</div>
</li>
</ol></li>
<li>
<div>Subversion: <a href="http://subversion.tigris.org/">http://subversion.tigris.org/</a></div>
<ol>
<li>
<div>Win32 binaries for Apache 2.2.x</div>
</li>
</ol></li>
<li>
<div>TortoiseSVN: <a href="http://tortoisesvn.tigris.org/">http://tortoisesvn.tigris.org/</a> or <a href="http://tortoisesvn.net/">http://tortoisesvn.net/</a>&nbsp;(you'll end up at the latter anyways)</div>
<ol>
<li>
<div>32 Bit</div>
</li>
</ol></li>
</ol></li>
<li>
<div>Backup Apache configuration.</div>
<ol>
<li>
<div>You can find the httpd.conf file in the conf directory, in the install directory.</div>
<ol>
<li>
<div>Example: c:\Program Files\Apache Software Foundation\Apache2.2\conf\httpd.conf</div>
</li>
</ol></li>
</ol></li>
<li>
<div>Stop Apache.</div>
<ol>
<li>
<div>Open the Apache Service Monitor, select the Apache2.2 service, and press the Stop button.</div>
</li>
</ol></li>
<li>
<div>Uninstall Apache.</div>
<ol>
<li>
<div>Unfortunately, the installer for a higher version can't seem to run with Apache already installed. So, we have to uninstall it first.</div>
</li>
</ol></li>
<li>
<div>Install Apache.</div>
<ol>
<li>
<div>localhost is your friend. If you're installing along-side IIS, keep it at the 'All Users, on Port 80, as a Service' as we'll change this later.</div>
</li>
<li>
<div>Typical install is fine, at the default location, but feel free to change as needed.</div>
</li>
<li>
<div>See my <a href="/words/post/Install-Apache-229-to-Windows-Vista-Ultimate.aspx">Install Apache 2.2.9 to Windows Vista (Ultimate)</a> for a full guide.</div>
</li>
</ol></li>
<li>
<div>Verify Apache settings.</div>
<ol>
<li>
<div>My install ran fine, with no configuration settings lost. However, if your httpd.conf is changed, you'll want to do a compare of your backup copy, with the new version.</div>
<ol>
<li>
<div>TortoiseMerge or WinMerge are two excellent applications that will help with this.</div>
</li>
</ol></li>
<li>
<div>Remember to stop the Apache service if you need to make changes.</div>
</li>
<li>
<div>For this guide, I assume you're running at localhost on port 8080.</div>
</li>
<li>
<div>The Apache Service Monitor should also display the current version, when the service is selected.</div>
</li>
</ol></li>
<li>
<div>Backup Subversion repositories.</div>
<ol>
<li>
<div>I do this in two ways.</div>
<ol>
<li>
<div>First, I backup all repository directories. In my case, I have all my repos in b:\repos\. I simply make a copy of this directory.</div>
</li>
<li>
<div>Next, I do a dump of all repositories. This basically means I run the following command: <strong>svnadmin dump StrivingLife &gt; ..\repos_dump\StrivingLife.dump</strong></div>
<ol>
<li>
<div><strong>dir &gt; list.txt</strong> will give me a listing of all repos, which, after a bit of deleting and pasting, ends up with a usable batch file. Add <strong>PAUSE</strong> to allow yourself some time to read over the results.</div>
</li>
</ol></li>
</ol></li>
</ol></li>
<li>
<div>Stop Apache (if it's running).</div>
</li>
<li>
<div>Extract the zip contents to your Subversion application directory.</div>
<ol>
<li>
<div>Backup the old version of those files, if you so choose.</div>
</li>
<li>
<div>I installed to C:\Program Files\Subversion\</div>
</li>
</ol></li>
<li>
<div>Copy necessary files from Subversion directory to Apache.</div>
<ol>
<li>
<div>In the Subversion bin directory, copy <strong>mod_authz_svn.so</strong> and <strong>mod_dav_svn.so</strong> to the Apache modules directory.</div>
</li>
<li>
<div>In the Subversion bin directory, copy <strong>intl3_svn.dll</strong> and <strong>libsvn_fs-1.dll</strong> (or <em>libdb44.dll</em> for Berkeley DB support) to the Apache bin directory.</div>
</li>
<li>
<div>If you need to make Apache changes (you haven't installed Subversion before), see my <a href="/words/post/Installing-Subversion-binaries-for-Apache-22x.aspx">Installing Subversion binaries for Apache 2.2.x</a>, otherwise you should be set.</div>
</li>
</ol></li>
<li>
<div>Start Apache.</div>
</li>
<li>
<div>Confirm SVN version in Apache Services Monitor.</div>
<ol>
<li>
<div>You may need to Exit and restart the monitor application to see the change.</div>
</li>
</ol></li>
<li>
<div>Uninstall TortoiseSVN and restart your computer.</div>
</li>
<li>
<div>Install TortoiseSVN and restart your computer.</div>
<ol>
<li>
<div>Sigh.</div>
</li>
<li>
<div>The third window has changed, but otherwise see <a href="/words/post/Installing-TortoiseSVN-to-Windows-Vista.aspx">Installing TortoiseSVN to Windows Vista</a> for specifics.</div>
</li>
</ol></li>
<li>
<div>Do a test checkout, or browse some repositories.</div>
</li>
<li>
<div>Checkout a working copy of a repository. We've got TortoiseSVN, so let's use it.</div>
</li>
<li>
<div>You can also use the Repository Browser to take a look at some repos.</div>
</li>
<li>
<div>You can also use your browser to browse the repos via the Apache component. Lots of options.</div>
</li>
<li>
<div>Use <strong>svnadmin verify <em>repoName</em></strong> to use Subversion to verify revisions.</div>
</li>
<li>
<div>Consider upgrading your repositories.</div>
<ol>
<li>
<div>svnadmin upgrade repoName is the shortcut to upgrade your repository, to get access to any new features.</div>
<ol>
<li>You'll want to be careful your tools can interact with the new repository version. In our case, we're fine doing so.</li>
<li>Taking the batch file we created to dump all our repositories, and tweaking it slightly, will enable us to upgrade all our repos as well.</li>
</ol></li>
<li>
<div>Dumping and loading is another way, which keeps things a little cleaner.</div>
</li>
</ol></li>
<li>
<div>Celebrate, because you've successfully upgraded.</div>
</li>
</ol>
<p>Questions/comments/concerns are always appreciated.&nbsp;</p>
<p>This <em>original</em> piece of content was written from 7:40 PM (CT) to&nbsp;9:45 PM (CT), on March 23 2009.</p>
