+++
title = "Upgrading Subversion and TortoiseSVN on Windows (1.4.0 to 1.4.2)"
summary = "In this article, we'll be upgrading our Subversion installation from 1.4.0 to 1.4.2."
draft = false
comments = true
date = "2006-11-26T12:00:00-06:00"
modified = "2009-07-22T21:52:24-05:00"
slug = "Upgrading-Subversion-and-TortoiseSVN-on-Windows-(140-to-142)"
blogengine = "79dac9b1-2f72-46e6-bce6-4a7026507a45"
categories = ["tutorials / guides"]
tags = ["subversion", "tortoisesvn", "svn"]
+++

<p>In a previous article, <a href="/words/post/Installing-Subversion-and-TortoiseSVN-to-a-Windows-XP-Home-Edition-SP2-local-machine-with-Dreamweaver-8.aspx">Installing Subversion and TortoiseSVN to a Windows XP, Home Edition, SP2, local machine with Dreamweaver 8</a>, we installed Subversion 1.4.0 and TortoiseSVN 1.4.0 to our Windows machine. This time, we'll be quickly going over how to upgrade our installation.<!--more--></p>
<h3>Upgrading Subversion</h3>
<p>The Subversion upgrade is a quick installation because all you really need to do is install the new setup file. You can get the file from <a href="http://subversion.tigris.org/">Tigris</a>, which is called svn-1.4.2-setup.exe. Once the 3.5 MB file has been downloaded, run it.</p>
<div class="note">
<p>You can also uninstall Subversion and then run the new installer, if you so desire.</p>
</div>
<p><!--adsense-->You can continue through the installation, reading as you do. When you get to a Select Additional Tasks window, make sure that the checkbox next to the lone Apache module option is unchecked. Of course, if you're using Apache, check it (but in my previous article, we/I decided not to use this module).</p>
<p>Once the installation begins, files will be replaced. If you setup Subversion as a service, you may run into an error message when svnserve can't be replaced. Make sure that you stop the service and then retry. Once the installation has finished, you can restart the service.</p>
<p>Note that you shouldn't need to upgrade any previous repositories.</p>
<h3>Upgrading TortoiseSVN</h3>
<p>First, of course, download the most recent version of TortoiseSVN, 1.4.1 for Subversion 1.4.2, from <a href="http://tortoisesvn.tigris.org/">Tigris</a>.</p>
<p>To upgrade TortoiseSVN, you do not have to uninstall previous versions (per the documentation). So, start up the 8 MB installer and work through the steps. Nothing surprising here.</p>
<p>Once the installer is finished, you'll need to restart your computer (but the documentation suggests you can just log off and then log back on). Restart, and you should be set.</p>
