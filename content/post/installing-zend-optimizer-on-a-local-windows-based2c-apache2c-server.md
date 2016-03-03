+++
title = "Installing Zend Optimizer on a local Windows-based, Apache, server"
summary = "This time, we'll be installing Zend Optimizer, to decrease the load time of most of our PHP pages."
draft = false
comments = true
date = "2006-02-26T18:27:00-06:00"
modified = "2008-01-15T13:48:34-06:00"
slug = "Installing-Zend-Optimizer-on-a-local-Windows-based2c-Apache2c-server"
blogengine = "0eebc6e5-83e9-4690-891a-5c2500a0093f"
categories = ["software", "tutorials / guides"]
tags = ["php", "zend optimizer"]
+++

<div class="note">
<p>
<em>Note: This guide should work equally well for Zend Optimizer 3.0.1 and above.  For a guide on upgrading this 2.6.2 install, see <a href="/words/post/Upgrading-to-Zend-Optimizer-301-on-a-local-Windows-based2c-Apache2c-server.aspx">Upgrading to Zend Optimizer 3.0.1 on a local Windows-based, Apache, server</a>.</em>
</p>
</div>
<p>
From Zend&#39;s FAQ,
</p>
<blockquote>
	<p>
	<strong>Why use the Zend Optimizer; isn&#39;t PHP supposed to be quite fast already?</strong>
	</p>
	<p>
	The standard Zend run-time compiler used by PHP is indeed extremely fast, generating code that is usually 2 to 10 times faster. But an application that uses the Zend Optimizer typically executes another 40% to 100% faster.
	</p>
</blockquote>
<p>
So, Zend Optimizer will help decrease the time spent on processing code. If you run the file we created a few steps back, probably called <a href="http://localhost/phpinfo.php">http://localhost/phpinfo.php</a> (which basically runs &lt;?php phpinfo(); ?&gt;), you&#39;ll notice a line that says &quot;This program makes use of the Zend Scripting Language Engine: Zend Engine v1.3.0, Copyright (c) 1998-2004 Zend Technologies&quot;. This is the standard Zend run-time compiler that is mentioned above. Once we download and install the Zend Optimizer, we&#39;ll see some additional lines here.
</p>
<!--more--><!--adsense-->
<p>
<strong>Download Zend Optimizer</strong>
</p>
<p>
The first thing we&#39;ll be doing is downloading Zend Optimizer. You can download a copy at <a href="http://www.zend.com/products/zend_optimizer/">http://www.zend.com/products/zend_optimizer/</a>. Based upon the system requirements, we&#39;ll be able to install the, at the time of this writing, current version, version 2.6. In order to download this, you will have to create an account.
</p>
<p>
After creating an account (or logging into your existing one), you&#39;ll want to download the Windows x86 version of Zend Optimizer 2.6.2 (or the current version that works with our version of PHP, 4.4.2). It&#39;s over 4.5 MB, so you may be in for a wait. Again, I recommend you download this file into the folder you created for these guides. Once the download has finished, open the executable file.
</p>
<p>
<strong>Installing Zend Optimizer</strong>
</p>
<p>
You&#39;ll first have to read and agree to the license agreement. After doing so, you&#39;ll need to choose an installation directory, which we&#39;ll leave as the default (C:\Program Files\Zend\ZendOptimizer-2.6.2). On the next screen, verify that the installer successfully detects the Web server (in our case, Apache 1.3.34).
</p>
<p>
Next, verify that the folder containing the php.ini file is correct. If you&#39;ve followed the guide thus far, it&#39;s probably in c:\windows\, which is what the installer will probably have. Next, you&#39;ll have to choose the &quot;root folder of your Web server&quot;, and the default will be something like C:\Program Files\Apache Group\Apache, which is correct. Next, we&#39;ll have to choose the &quot;document root folder of your Web server&quot;, which is where our Web sites are located. It will choose C:\Program Files\Apache Group\Apache\htdocs, but we&#39;ll need to change this to C:\home, since this is where our Web sites are located.
</p>
<p>
Finally, you&#39;ll be asked to verify the installation, and Install. When the installation occurs, it will be making a copy of the php.ini file, and creating a new version with some modifications. In order to do this, it will have to stop and then start Apache, which is absolutely fine.
</p>
<p>
Once the installation has finished, we can make a quick backup copy of the php.ini file, as well as the file it created (which it would have notified us of). In my case, the backup was called &quot;php.ini.ZendOptimizer-2.6.2_bak&quot;.
</p>
<p>
If we now visit <a href="http://localhost/phpinfo.php">http://localhost/phpinfo.php</a>, we&#39;ll notice that the bit on Zend has been increased to something like &quot;This program makes use of the Zend Scripting Language Engine: Zend Engine v1.3.0, Copyright (c) 1998-2004 Zend Technologies with Zend Extension Manager v1.0.9, Copyright (c) 2003-2006, by Zend Technologies with Zend Optimizer v2.6.2, Copyright (c) 1998-2006, by Zend Technologies&quot;.
</p>
<p>
And, with that, you&#39;ve successfully installed Zend. While you may not notice a change, especially if you haven&#39;t created a lot of PHP files, there is one, one which you would notice once you begin developing larger PHP implementations. In the future, you may want to even uninstall Zend, to see just how pages change.
</p>
<p>
This in fact brings up a very good point. Now that Zend has created a backup of the pre-Zend php.ini file, you&#39;ll want to make a note of any changes you make in the php.ini file. I recommend you keep the pre-Zend php.ini file as it is, but create a copy where you make any modifications you may make to the post-Zend php.ini file.
</p>
<p>
The modification, in case you wondering, is simply the addition of the below at the very end of the php.ini file.
</p>
<blockquote>
	<p>
	[Zend]<br />
	zend_extension_manager.optimizer_ts=&quot;C:\Program Files\Zend\ZendOptimizer-2.6.2\lib\Optimizer-2.6.2&quot;<br />
	zend_extension_ts=&quot;C:\Program Files\Zend\ZendOptimizer-2.6.2\lib\ZendExtensionManager.dll&quot;
	</p>
</blockquote>
<p>
Since you may make additional changes to this file down the line (such as if you look at installing another database solution when I do), it&#39;s important to know.
</p>
<p>
And with that, we&#39;ve completed this tutorial, as we&#39;ve successfully installed Zend Optimizer.
</p>
<p>
<a href="http://strivinglife.net/wordpress/a-local-apache-web-server-on-a-windows-xp-computer/">View all of the steps to creating a local Web server, for development.</a>
</p>

