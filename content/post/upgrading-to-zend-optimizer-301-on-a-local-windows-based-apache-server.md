+++
title = "Upgrading to Zend Optimizer 3.0.1 on a local Windows-based, Apache, server"
description = "Guide to upgrading Zend Optimizer 2.6.2 to Zend Optimizer 3.0.1 on Apache 1.x, running on Windows and with PHP 4.4.2."
draft = false
comments = true
date = "2006-06-08T19:37:00-05:00"
modified = "2009-11-07T20:47:14-06:00"
slug = "Upgrading-to-Zend-Optimizer-301-on-a-local-Windows-based-Apache-server"
blogengine = "99eb45ce-1214-4016-9833-8914ab70ad0a"
categories = ["software", "tutorials / guides"]
tags = ["apache", "php"]
+++

<p>In a <a href="http://strivinglife.com/words/post/Installing-Zend-Optimizer-on-a-local-Windows-based2c-Apache2c-server.aspx">previous guide, we installed Zend Optimizer 2.6.2 to a local Windows-based Apache 1.x server, running PHP 4.4.2</a>. This time, we'll be upgrading Zend Optimizer from 2.6.2 to 3.0.1.</p>
<h3>Downloading and backups</h3>
<p>First, we'll need to download a copy from <a rel="external" href="http://www.zend.com/products/zend_optimizer/">http://www.zend.com/products/zend_optimizer/</a>. We've already setup an account when we downloaded 2.6.2, so we can simply log in. Of course, if you've forgotten your password you can request assistance, and if you haven't downloaded Zend Optimizer before, you can setup an account.</p>
<p>Since we're installing to Windows, we'll download Zend Optimizer 3.0.1 for Windows x86. Save this to the same location you save your other server downloads. This time you'll be looking at a 7.5 MB download.</p>
<p>While we're waiting for the download, we can start making some backups. Head over to C:\WINDOWS\, and find the php.ini file. While Zend will be making a backup, let's make one for ourselves as well. We can store this where we store our other server-system backups.</p>
<h3>Upgrading</h3>
<p>We now have two upgrade options. First, we can uninstall Zend Optimizer 2.6.2 and then reinstall Zend Optimizer 3.0.1. Otherwise, we can simply install Zend Optimizer 3.0.1 and see how it handles the previous installation.</p>
<p>One problem is that we installed Zend Optimizer 2.6.2 to a directory that contained the version number; C:\Program Files\Zend\ZendOptimizer-2.6.2\</p>
<p>If we start the installation file that we just downloaded, we'll find that it will first attempt to remove the previous version Zend Optimizer. Not too bad. So, after verifying that we've backed up our necessary files, let's let it do it's work.</p>
<p>It will need to stop Apache, so make sure you let it. You'll also be prompted whether you'd like to restore your old php.ini file. If you've made serious modifications, you can say no. Otherwise, yes works.</p>
<p>Apache will be restarted, and now you can start the installation once again; this time you'll really be able to install.</p>
<h3>Installing</h3>
<p>Read the user agreement and agree to the default installation. Yes, once again we'll be installing to a directory that contains a version number. However, you could certainly change this so that a version number is not listed.</p>
<p>The installer should detect the version of Apache you're using, but if it did not, make that selection on the next screen. You should be able to just click Next on the rest of the screens, until you're ready to hit the Install button.</p>
<p>Once the installation has completed you can read the Readme file, and/or Finish.</p>
<h3>Checking the installation and backups</h3>
<p>Now, load up <a rel="nofollow" href="http://localhost/phpinfo.php">http://localhost/phpinfo.php</a> in your browser to check the current version of Zend Optimizer. You should see version 3.0.1.</p>
<p>Now make sure you go back to the WINDOWS folder and backup both php.ini files. All that this installation really changed here was the version number contained on two lines.</p>
<p>With that, you've successfully upgraded Zend Optimizer 2.6.2 to 3.0.1.</p>
<p><a href="/local-apache-server/">View all of the steps to creating a local Web server, for development.</a></p>
