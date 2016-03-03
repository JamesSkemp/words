+++
title = "Installing Python on a local  Windows-based, Apache, server"
summary = "In this article, we'll be installing Python on our local server via ActiveState's ActivePython."
draft = false
comments = true
date = "2006-10-07T08:11:00-05:00"
slug = "Installing-Python-on-a-local-Windows-based-Apache-server"
blogengine = "9924be2c-6376-4c44-b118-36396ebb5c54"
categories = ["tutorials / guides"]
tags = ["python"]
+++

<p>
In this article, we&#39;ll be installing Python on our local server via ActiveState&#39;s ActivePython. You can download the current version of ActivePython (2.4.3.12), as well as a select number of previous versions, from <a href="http://www.activestate.com/Products/ActivePython/">http://www.activestate.com/Products/ActivePython/</a>
</p>
<!--more-->
<p>
Since we&#39;re installing to Windows, download the 18.7 MB Windows (x86) MSI file (ActivePython-2.4.3.12-win32-x86.msi).
</p>
<p>
Once we&#39;ve download the file, open it. Read and accept the license, and on the next screen, leave the installed settings along, but change the Install to from C:\Python24\ to C:\usr\bin\python\. Finally, Install.<!--adsense-->
</p>
<p>
To test the installation, open Notepad and enter the following lines:
</p>
<blockquote>
	<p>
	print &quot;Hello world&quot;
	</p>
</blockquote>
<p>
Next, save this file at c:\helloworld.py. Now, open the Command Prompt (Start &gt; Run &gt; cmd) and type in the following.
</p>
<blockquote>
	<p>
	python c:\helloworld.py
	</p>
</blockquote>
<p>
You can also just type <strong>python</strong> to see version information. Press Ctrl + Z to exit python (if you just typed <strong>python</strong>) and <strong>exit</strong> to exit the command prompt.
</p>
<p>
Congrats. With that, you&#39;ve successfully installed ActivePython to your machine!
</p>
<p>
<a href="http://strivinglife.net/wordpress/a-local-apache-web-server-on-a-windows-xp-computer/">View all of the steps to creating a local Web server, for development.</a>
</p>

