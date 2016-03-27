+++
title = "Installing mod_perl on a local Windows-based, Apache server"
description = "Installing mod_perl."
draft = false
comments = true
date = "2006-04-08T08:41:00-05:00"
slug = "Installing-mod_perl-on-a-local-Windows-based-Apache-server"
blogengine = "9acb75bb-6e91-40a0-b102-cc0baab837a9"
categories = ["software", "tutorials / guides"]
tags = ["perl", "apache"]
+++

<p>
The home page of mod_perl gives a great explanation of what mod_perl is, and what it provides. We&#39;ll be installing mod_perl simply because it will help us install other functionality as time goes by.
</p>
<!--more-->
<h4>Download mod_perl</h4><!--adsense-->
<p>
The home of mod_perl is located at <a href="http://perl.apache.org/">http://perl.apache.org/</a>. Select Download &gt; Binary mod_perl distributions, and find Win32 Active Perl &gt; Win32 mod_perl 1.0 ppm packages. This will lead you to <a href="http://theoryx5.uwinnipeg.ca/ppms/x86/">http://theoryx5.uwinnipeg.ca/ppms/x86/</a>, where you can download mod_perl-1.so Save to c:\home\downloads\.
</p>
<h4>Installing mod_perl</h4>
<p>
First place a copy of the mod_perl-1.so file into C:\Program Files\Apache Group\Apache\modules\, and change it&#39;s filename to mod_perl.so.
</p>
<p>
Next, open httpd.conf, and search for mod_foo.so.
</p>
<p>
At the end of the LoadModule calls, add the following:
</p>
<blockquote>
	<p>
	LoadFile &quot;c:/usr/bin/perl58.dll&quot;<br />
	LoadModule perl_module modules/mod_perl.so
	</p>
</blockquote>
<p>
Now scroll down a bit and add to the end of the AddModule calls the following:
</p>
<blockquote>
	<p>
	AddModule mod_perl.c
	</p>
</blockquote>
<p>
If you installed ActivePerl to a location other than c:\usr\, then your dll file may be in a different location. Also, if you installed a different version, you&#39;ll need to verify the perl dll version. It should be in the format of perlxx.dll.
</p>
<p>
Search for .cgi, and add .pl to the end of this line. You&#39;ll end up with the following.
</p>
<blockquote>
	<p>
	AddHandler cgi-script .cgi .pl
	</p>
</blockquote>
<p>
Finally, save httpd.conf and restart Apache.
</p>
<h4>Testing the install of mod_perl</h4>
<p>
Now, create a document with the following text:
</p>
<blockquote>
	<p>
	 #!/usr/bin/perl<br />
	print &quot;Content-type: text/plain\n\n&quot;;<br />
	print &quot;mod_perl rules!\n&quot;;
	</p>
</blockquote>
<p>
Save this as mod_perl_test.pl, in your Web root folder (c:\home\ if you&#39;ve been following along). Now load <a href="http://localhost/mod_perl_test.pl">http://localhost/mod_perl_test.pl</a> Once you do, you should simply see &quot;mod_perl rules!&quot;.
</p>
<p>
Additionally, load up <a href="http://localhost/phpinfo.php">http://localhost/phpinfo.php</a> and scroll down to the apache heading. You should see, in the Apache Version, mod_perl/1.29_01-dev (or something similar to this, depending upon what version you installed).
</p>
<p>
You&#39;ve now successfully installed mod_perl.
</p>
<p>
<a href="/local-apache-server/">View all of the steps to creating a local Web server, for development.</a>
</p>

