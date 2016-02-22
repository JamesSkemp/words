+++
title = "Install Apache 2.2.9 to Windows Vista (Ultimate)"
summary = "Overview of installing Apache 2.2.9 to Windows Vista Ultimate, along-side IIS."
draft = false
comments = true
date = "2008-08-15T16:15:00-05:00"
modified = "2009-11-24T07:15:50-06:00"
slug = "Install-Apache-229-to-Windows-Vista-Ultimate"
blogengine = "8a793db4-57ba-4a6e-930b-ac5ec17e15b0"
categories = ["software", "tutorials / guides"]
tags = ["apache", "vista"]
+++

<p>In this article I'll be covering an installation of Apache 2.2.9 to Windows Vista Ultimate. I'll be installing Apache so that you can run IIS as well (hence, Apache will be on a different port). You may want to do this if you want to run Subversion on Apache (as I do).</p>
<h3>Installing Apache 2.2</h3>
<p>Currently the <a rel="external" href="http://httpd.apache.org/">Apache HTTP Server</a> has both a 2.0 and 2.2 version. For new development, the 2.2 version is the recommended verison, as it contains many new features. If you currently have Apache 2.0 or 1.3, you may want to determine whether you still require those older versions (such as for module support).</p>
<p>For this installation I'll be using the current Win32 binary, with SSL (Apache 2.2.9 with OpenSSL 0.9.8h). Download and run the MSI.</p>
<div class="note">
<p>I won't be covering the SSL aspect here, so feel free to go with the installer that doesn't have it, if you won't be needing it.</p>
</div>
<p>As with all installers, read through the screens, pressing Next as you go.</p>
<p>Eventually you'll come upon a Server Information screen, which you update like the below.</p>
<p><img title="Apache 2.2.9 Install Server Information" src="http://media.jamesrskemp.com/graphics/apache_http/apache_2.2.9_install_04.jpg" alt="Apache 2.2.9 Install Server Information" width="514" height="392" /></p>
<p>You can change all of these settings later.</p>
<p>Note that while IIS runs on port 80 by default,&nbsp;if you want Apache to run for all users, as a service, this is the&nbsp;easiest way to do so. Later, as we'll see,&nbsp;Apache&nbsp;won't be able to start, since IIS is already using port 80. However, we can&nbsp;change the port to get it working.</p>
<p><img title="Apache 2.2.9 Install - Apache fails to start" src="http://media.jamesrskemp.com/graphics/apache_http/apache_2.2.9_install_08.jpg" alt="Apache 2.2.9 Install - Apache fails to start" width="677" height="340" /></p>
<h3>Getting Apache to start</h3>
<p>To do this you'll need to open the <strong>httpd.conf</strong> file in the <strong>conf</strong> directory, within the Apache install directory.</p>
<p><img title="Apache 2.2.9 Install - httpd.conf" src="http://media.jamesrskemp.com/graphics/apache_http/apache_2.2.9_install_11.jpg" alt="Apache 2.2.9 Install - httpd.conf" width="541" height="342" /></p>
<p>If you've installed to the system drive (usually C), you'll be unable to save changes unless you run your editor as an administrator.</p>
<p>It's easiest to go to the Start menu, type Notepad, right-click on the application when it appears, and <strong>Run as administrator</strong>. You'll then be able to open the httpd.conf file and save your changes.</p>
<h3>What to change</h3>
<p>To have Apache listen on a different port you just need to find instances of port 80, and change them to another, un-used, port. 8080 is pretty common.</p>
<p>There will be one main instance, just a short distance down: <strong>Listen 80</strong></p>
<p>Change this to the new port (<strong>Listen 8080</strong>) and you should be able to start Apache through the Monitor.</p>
<div class="note">
<p>Of course, if you haven't installed IIS, you can leave the port as it is. Since the port is controlled by the httpd configuration file, it's relatively easy to update this as necessary.</p>
</div>
<h3>Testing</h3>
<p>Test the installation by visiting <strong>http://localhost:8080/.</strong> Assuming everything worked, you'll be presented with a message stating that "It works!"</p>
