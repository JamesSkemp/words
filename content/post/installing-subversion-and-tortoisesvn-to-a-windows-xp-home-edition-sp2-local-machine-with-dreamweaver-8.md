+++
title = "Installing Subversion and TortoiseSVN to a Windows XP, Home Edition, SP2, local machine with Dreamweaver 8"
description = "In this guide, I'll be installing Subversion and TortoiseSVN to a Windows XP machine, running SP2 and the Home Edition of XP. I'll be hooking it up to Dreamweaver 8, thanks to Nearly Geek's SVN4DW extension."
draft = false
comments = true
date = "2006-09-16T22:45:00-05:00"
modified = "2010-02-12T22:35:21-06:00"
slug = "Installing-Subversion-and-TortoiseSVN-to-a-Windows-XP-Home-Edition-SP2-local-machine-with-Dreamweaver-8"
blogengine = "56914b81-4279-4012-a772-c0057226c237"
categories = ["software", "tutorials / guides"]
tags = ["subversion", "dreamweaver", "svn"]
+++

<div class="note">
<p>The <a href="/words/post/Installing-Subversion-to-Windows-Vista.aspx">Subversion</a> aspect has been updated for Windows Vista.&nbsp;So too has the <a href="/words/post/Installing-TortoiseSVN-to-Windows-Vista.aspx">TortoiseSVN</a> installation. The&nbsp;Dreamweaver&nbsp;aspect has not been touched.</p>
<p>I also have <a href="/words/post/Playing-around-with-Subversion-with-a-test-repository.aspx">an article about <em>using</em> Subversion</a>.&nbsp;</p>
</div>
<p>When projects become large, or you have the need to keep information on what files you've modified, for any coding project, you may look for some kind of version control system. There's software like Microsoft's SourceSafe, but that can be costly, and according to some, it's a clunky solution. Open source is always a worthwhile solution, and luckily, there's a number of these alternatives out there.</p>
<p>In this guide, I'll be installing Subversion and TortoiseSVN to a Windows XP machine, running SP2 and the Home Edition of XP. I'll be hooking it up to Dreamweaver 8, thanks to Nearly Geek's SVN4DW extension. Note that while a '1-Click Setup' exists (SVN 1-Click Setup), I'll actually be going through the setup of the Subversion and TortoiseSVN separately. I do this primarily because the 1-click setup is a bit out-of-date at the time of this writing.</p>
<h4>Downloading Subversion and TortoiseSVN</h4>
<p>The first thing we'll need to do is download a copy of Subversion and TortoiseSVN. Both are available for free at Tigris.org, Subversion at <a href="http://subversion.tigris.org/">http://subversion.tigris.org/</a> and TortoiseSVN at <a href="http://tortoisesvn.tigris.org/">http://tortoisesvn.tigris.org/</a>. At the time of this writing, Subversion is version 1.4.0 and TortoiseSVN is also at version 1.4.0. Download both to your standard downloads folder (if you've followed any of my other guides, this would be c:\home\downloads\).<!--adsense--></p>
<p>For Subversion, we'll download the file svn-1.4.0-setup.exe, which contains the installer.</p>
<h4>Installing Subversion 1.4.0</h4>
<p>Once we've downloaded svn-1.4.0-setup.exe, we can begin the setup. Before we do this, make sure that if you're running Apache, it's stopped. We're stopping Apache since we don't want Subversion to use Apache as it's server. Instead, we want to use the server that comes with it, svnserve. If we wanted to use Apache, we could use Apache 2.0.x, but not 1.3 or 2.2.</p>
<p>Setup is pretty easy. You'll be asked if you want to setup Subversion. Continue through with the steps, reading and selecting next as you go, until you get to &ldquo;Select Additional Tasks&rdquo;. Here, you'll want to uncheck the Apache modules option, since we won't be using Apache for subversion.</p>
<p>Continue through to the rest of the installation using the defaults. Once Subversion has been installed, open the command prompt by selecting Run from the Windows Start menu. Now type &ldquo;svnserve.exe -d&rdquo;, without the quotes. This will start the server, which will listen on port 3690. You should be able to go to <a href="http://localhost:3690/">http://localhost:3690/</a> now and see something similar to the following. (Note that if you are using SP2 of Windows XP, you'll be prompted on whether you want to Unblock Subversion or not. If you don't, you won't be able to access Subversion, obviously.)</p>
<blockquote>
<p>( success ( 1 2 ( ANONYMOUS ) ( edit-pipeline svndiff1 absent-entries ) )</p>
</blockquote>
<p>Unfortunately, the command prompt window stays open, but we can look into fixing that shortly. First, we've got to install TortoiseSVN.</p>
<h4>Installing TortoiseSVN 1.4.0</h4>
<p>Start by running the install file, TortoiseSVN-1.4.0.7501-win32-svn-1.4.0.msi for example. You should be able to just read the various windows and accept all the default options. Once the installation has finished, however, you will need to restart your computer. Save whatever you're doing, and restart.</p>
<h4>Installing SvnService</h4>
<div class="note">
<p>Note that this next step is not necessary. <a rel="nofollow" href="http://www.webpusher.ie/">Mark Lennox</a> pointed out on 10/23/2006 that there's a way to do this via Windows. Very cool.</p>
</div>
<p>As we noticed previously, in order to run svnserve, we need to have a window open while it's running. Instead of using that method, we can use a 'wrapper' to make svnserve into a Windows service, just like our other services like Apache.</p>
<p>In order to do that, we'll need to download a file from <a href="http://tortoisesvn.tigris.org/files/documents/406/29202/SVNServiceDT.zip">http://tortoisesvn.tigris.org/files/documents/406/29202/SVNServiceDT.zip</a>. Extract the file SVNService.exe, in the Release folder, to the same folder as Subversion &ndash; so C:\Program Files\Subversion\bin\ if you've been following along.</p>
<p>Now go to Start &gt; Run, and type 'cmd', no quotes. At the prompt, type the following.</p>
<blockquote>
<p>cd c:\program files\subversion\bin\</p>
</blockquote>
<p>Now switch over to Windows Explorer and create a new directory in the c drive, called svnrepo. So, c:\svnrepo\. This will contain our Subversion repositories. Back to the command prompt, where we type the following.</p>
<blockquote>
<p>svnservice -install &ldquo;c:\program files\subversion\bin\svnserve.exe&rdquo; &ldquo;-d -r c:\svnrepo&rdquo;</p>
</blockquote>
<p>Note that if you ever want to remove svnserve as a service, simply use the following command.</p>
<blockquote>
<p>svnservice -remove</p>
</blockquote>
<p>SVNService will now display in your services panel, and should automatically start when you start Windows. Depending upon your needs, this may or may not be a good thing. Keep in mind that you can always change the startup to what you'd prefer. You can now exit out of the command prompt.</p>
<h4>Downloading Subversion for Dreamweaver (SVN4DW)</h4>
<p>A copy of the extension that we'll be using to add Subversion support to Dreamweaver can be downloaded from <span style="text-decoration: line-through;">Nearly Geek<!--http://www.nearlygeek.com/tools/subversion-for-dreamweaver/introduction/--></span> <a rel="nofollow" href="http://strivinglife.com/files/2006/09/svn4dw.zip">this site</a>.</p>
<p>Once the mxp file has downloaded (save this to your downloads directory as well), you can install the extension by running it. Once the extension has finished installing, open Dreamweaver 8. You'll have a new menu item, SVN, where you can perform your SVN tasks.</p>
<h4>Conclusion</h4>
<p>And with that, you've successfully setup Subversion, TortoiseSVN, and Dreamweaver 8 to work together. You will need to setup a repository, as well as configure user access, for which you can view the documentation resources under &ldquo;Resources of interest,&rdquo; below.</p>
<h4>Resources of interest</h4>
<p>Some resources you may be interested in, for additional information, include the following.</p>
<p>The O'Reilly book <cite>Version Control with Subversion</cite> can be found at <a href="http://svnbook.red-bean.com/">http://svnbook.red-bean.com/</a>. While it's slightly out-of-date, it's still quite applicable, especially for some of the general information that it provides.</p>
<p>TortoiseSVN and TortoiseMerge documentation can be found at <a href="http://tortoisesvn.net/doc_release">http://tortoisesvn.net/doc_release</a></p>
