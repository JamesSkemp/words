+++
title = "Quickie: Install Apache 2.2.4 on Ubuntu"
summary = "Quickie of how I installed Apache 2.2.4 to Ubuntu."
draft = false
comments = true
date = "2007-06-15T19:04:00-05:00"
modified = "2007-09-01T09:10:37-05:00"
slug = "Quickie-Install-Apache-224-on-Ubuntu"
blogengine = "898b0ef7-f617-45ab-bce6-4ecf8607cf25"
categories = ["article", "software", "tutorials / guides"]
tags = ["apache", "ubuntu"]
+++

<p>
May not be the best, but ... here&#39;s how I installed Apache 2.2.4 on Ubuntu (7.04), based on David Winter&#39;s guide <a rel="nofollow" href="http://davidwinter.me.uk/articles/2006/10/17/building-apache-22-from-source-for-ubuntu-dapper/" target="_blank"><em>Building Apache 2.2 from source for Ubuntu Dapper</em></a>.
</p>
<p>
All <span class="code_terminal">code</span> from a terminal, unless otherwise noted.<!--adsense-->
</p>
<p>
<span class="code_terminal">sudo apt-get install build-essential</span>
</p>
<p>
<span class="code_terminal">cd<br />
mkdir src<br />
cd src</span>
</p>
<p>
I downloaded zlib from http://www.zlib.net/ (zlib source code, version 1.2.3, tar.gz format) into the src folder, and extracted it to the same.
</p>
<p>
<span class="code_terminal">cd zlib-1.2.3/<br />
./configure --prefix=/usr/local<br />
make<br />
sudo make install</span>
</p>
<p>
At http://httpd.apache.org/download.cgi, I downloaded Unix Source: httpd-2.2.4.tar.gz, saved it to the src directory, and extracted it to the same.
</p>
<p>
<span class="code_terminal">cd httpd-2.2.3/</span>
</p>
<p>
<span class="code_terminal">./configure --prefix=/usr/local/apache2 --enable-mods-shared=all --enable-deflate --enable-proxy --enable-proxy-balancer --enable-proxy-http</span>
</p>
<p>
<span class="code_terminal">make</span> (which took a long time)
</p>
<p>
<span class="code_terminal">sudo make install</span>
</p>
<p>
<span class="code_terminal">sudo /usr/local/apache2/bin/apachectl start</span>, followed by heading over to http://localhost/, which worked.
</p>
<p>
<span class="code_terminal">sudo /usr/local/apache2/bin/apachectl stop</span>
</p>
<p>
<span class="code_terminal">sudo cp /usr/local/apache2/bin/apachectl /etc/init.d/apachectl<br />
sudo chmod +x /etc/init.d/apachectl</span>
</p>
<p>
<span class="code_terminal">sudo nano /etc/init.d/apachectl</span>
</p>
<p>
The top of the page should look like this, after the bold text is added.
</p>
<p>
<span class="code_terminal">#!/bin/sh<br />
#<br />
<strong># chkconfig: - 85 15<br />
# description: Apache is a web server.</strong></span>
</p>
<p>
Ctrl + X will exit, during which you&#39;ll be prompted to save (do so).
</p>
<p>
<span class="code_terminal">sudo /usr/sbin/update-rc.d apachectl defaults</span>
</p>
<p>
<span class="code_terminal">sudo adduser --system apache</span>
</p>
<p>
<span class="code_terminal">sudo nano /usr/local/apache2/conf/httpd.conf</span>
</p>
<p>
Find the following:
</p>
<p>
<span class="code_terminal">User daemon<br />
Group daemon</span>
</p>
<p>
Change it to the following:
</p>
<p>
<span class="code_terminal">User apache<br />
Group nogroup</span>
</p>
<p>
Save, as above.
</p>
<p>
<span class="code_terminal">sudo /usr/local/apache2/bin/apachectl start</span>
</p>
<p>
<span class="code_terminal">ps -aux | grep httpd</span>
</p>
<p>
I&#39;ve yet to reboot the machine and verify that apache is running on this boxes&#39; IP - I&#39;ll do so later.
</p>
<p>
Now the question I have is, how would I go about removing Apache 2.2.4?  Research time ...
</p>

