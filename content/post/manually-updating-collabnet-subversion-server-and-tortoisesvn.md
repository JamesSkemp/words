+++
title = "Manually updating CollabNet Subversion Server and TortoiseSVN"
description = "Manually upgrading CollabNet Subversion Server and TortoiseSVN."
draft = false
comments = true
date = "2010-04-27T21:23:00-05:00"
modified = "2010-10-28T07:55:46-05:00"
slug = "Manually-updating-CollabNet-Subversion-Server-and-TortoiseSVN"
blogengine = "ff13dc06-e617-4fca-99ba-8f45d99b6041"
categories = ["tutorials / guides"]
tags = ["subversion", "tortoisesvn", "svn", "resume"]
+++

<p>With CollabNet releasing a new version of Subversion Server (1.6.11), and TortoiseSVN having a release a few days earlier, it's time to do an actual update, instead of a comment like I did <a href="http://strivinglife.com/words/post/Installing-CollabNet-Subversion-Sever-163-and-TortoiseSVN-163-on-Windows-Server-2003.aspx">last time</a>.</p>
<h3>Environment</h3>
<p>I'm currently running CollabNet Subversion Server version 1.6.9.1 on Windows 7 Home Premium, 64-bit.</p>
<p>The install directory is C:\Program Filies (x86)\CollabNet\Subversion Server\, and I'm installing version 1.6.9.11. These instructions should work, with minor changes, for other versions of CollabNet Subversion and Windows.</p>
<h3>Backups and downloads</h3>
<p>First make sure <a href="http://strivinglife.com/words/post/Example-batch-file-to-dump-Subversion-repositories.aspx">you've backed up your repositories</a>, just in case you need to roll back.</p>
<p>Next <a rel="external" href="http://www.open.collab.net/products/subversion/getit.html">download CollabNet Subversion Server</a> for your environment. You can also go ahead and and start <a rel="external" href="http://tortoisesvn.net/downloads/">downloading TortoiseSVN</a>.</p>
<p>Browse to the CollabNet Subversion Server install directory (C:\Program Filies (x86)\CollabNet\Subversion Server\ on my system) and make sure you make a backup of the Apache configuration file, httpd\conf\httpd.conf.</p>
<h3>Upgrading CollabNet Subversion Server</h3>
<p>In the CollabNet Subversion Server install directory open httpd\bin\ApacheMonitor.exe and stop the currently running instance of Apache, then exit out of Apache Monitor.</p>
<p>Open the Services listing (Administrative Tools &gt; Services) and stop CollabNet Subversion svnserve (or you won't be able to update any DLLs, without uninstalling first).</p>
<p>Start the CollabNet Subversion Server installer and when prompt, click Yes to upgrade.</p>
<p>Go ahead and click through the installer. Since we're upgrading, the settings should be just fine as they are.</p>
<p>Start Apache Monitor back up, and start the instance, or just start the CollabNet Subversion Apache service (you can stop it via this as well).</p>
<p>Test you can access the repository by browsing to it, if enabled, or going into a checked out repository and looking at the log.</p>
<h3>Upgrading TortoiseSVN</h3>
<p>Start the TortoiseSVN installer, clicking through <a href="http://strivinglife.com/words/?tag=/tortoisesvn">as usual</a>. To finish, TortoiseSVN will require a restart.</p>
<p>Once your system is back up, browse to a checked out directory and verify that you're able to use base functionality, even going so far as to commit changes to a test repository, as needed.</p>
