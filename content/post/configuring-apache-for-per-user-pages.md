+++
title = "Configuring Apache for per-user pages"
description = "How to configure Apache 2.2.4 on Ubuntu 7.04 for per-user pages."
draft = false
comments = true
date = "2007-06-18T20:30:00-05:00"
slug = "Configuring-Apache-for-per-user-pages"
blogengine = "b95648b7-b4aa-4711-a5a5-e5ab94f543b6"
categories = ["article", "software", "tutorials / guides"]
tags = ["apache", "ubuntu"]
+++

<p>
In a previous post, <a href="/words/post/Quickie-Install-Apache-224-on-Ubuntu.aspx">I covered installing Apache 2.2.4 on Ubuntu</a>. Unfortunately, if you want to create content for this server, you need to either use the root account, or change the permissions on the /usr/local/apache2/htdocs directory. Let&#39;s keep things that way.<!--more-->
</p>
<p>
First, open the Apache configuration file.<!--adsense-->
</p>
<p>
<span class="code">sudo nano /usr/local/apache2/conf/httpd.conf</span>
</p>
<p>
Now find the following line, and remove the pound sign from the beginning of the line.
</p>
<p>
<span class="code">#Include conf/extra/httpd-userdir.conf</span>
</p>
<p>
Ctrl + X to save and exit.
</p>
<p>
If you want, you can open this file by running the following.
</p>
<p>
<span class="code">sudo nano /usr/local/apache2/conf/extra/httpd-userdir.conf</span>
</p>
<p>
But, there&#39;s no real reason to do this.
</p>
<p>
So, changes made, restart Apache.
</p>
<p>
<span class="code">sudo /usr/local/apache2/bin/apachectl restart</span>
</p>
<p>
If you head over to http://localhost/, it&#39;ll still display the files in your htdocs folder (including the ColdFusion file, if you&#39;ve got that created, and <a href="/words/post/Quickie-Install-ColdFusion-702-on-Ubuntu-704-with-Apache-224.aspx">ColdFusion up and running</a>).
</p>
<p>
However, you can now create a folder in your user directory and have direct access to your own content.
</p>
<p>
For example, if you have a <strong>bob</strong> user, you have a home directory at /home/bob/.
</p>
<p>
Create a public_html (the default setting, which can be changed in the above mentioned httpd-userdir.conf file). Now if you create files, you can access them by going to http://localhost/~bob/filename.ext
</p>
<p>
That&#39;s it, you&#39;re set. And yes, ColdFusion files will run (although it seems they run a tad bit slow ...).
</p>
<h4>Update, June 18, 2007 @ 21:11</h4>
<p>
Dan reminded me of no-ip, an account of which I had sitting around doing nothing. After messing around with it a bit, I&#39;ve configured the &quot;Dynamic Update Client.&quot; <span class="code_terminal">sudo make install</span> (after extracting) <span class="code_terminal">sudo noip2 -C</span> (all covered in the readme) Defaults all around. I haven&#39;t got this configured yet to start on startup. Dan, any good resources on this? Another good command, for a future reminder: <span class="code">sudo nmap -sV -O localhost</span> to check which ports are open (80 and 631 on my machine); can&#39;t figure out how to close port 631 yet, or why I really need CUPS 1.2 (printing related, but I don&#39;t use a printer - I print to PDF if anything ...)
</p>
<h4>Update, June 18, 2007 @ 21:55</h4>
<p>
By the way, the <a rel="nofollow" href="http://www.amazon.com/gp/product/0672328364/strivinglifen-20/" target="_blank">Apache Phrasebook</a> was helpful for easily setting these up (and is an overall great resource, if you&#39;re setting up / using Apache on Linux; the Windows information is there, but not as good as the Linux information).
</p>

