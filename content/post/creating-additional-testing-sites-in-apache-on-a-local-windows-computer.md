+++
title = "Creating additional testing sites in Apache, on a local Windows computer"
summary = "It may happen that you'd like to test multiple sites on one machine.  There's a number of ways to do this.  Following our previous tutorial, Installing Apache to a Windows-based computer, locally, we can either dump additional folders in our Apache root, or we can create additional subdomains under localhost."
draft = false
comments = true
date = "2006-02-18T09:44:00-06:00"
slug = "Creating-additional-testing-sites-in-Apache-on-a-local-Windows-computer"
blogengine = "7ec11eb3-51d3-4b47-940d-10fc5684f14a"
categories = ["software", "tutorials / guides"]
tags = ["apache"]
+++

<p>
It may happen that you&#39;d like to test multiple sites on one machine.  There&#39;s a number of ways to do this.  Following our previous tutorial, Installing Apache to a Windows-based computer, locally, we can either dump additional folders in our Apache root, or we can create additional subdomains under localhost.<!--more-->
</p>
<p>
That is, Google has a number of different subdomains.  News.google.com, mail.google.com, and regular old www.google.com.  With an Apache and Windows change, we can replicate this as well.<!--adsense-->
</p>
<p>
First, let&#39;s open up our Apache configuration file.  If you followed the steps in the Installing Apache to a Windows-based computer, locally guide, you can find this file at  C:\Program Files\Apache Group\Apache\conf\httpd.conf, or via the Start menu (detailed in the previous article).
</p>
<p>
We&#39;re also going to open the Windows hosts file, in Notepad, at C:\WINDOWS\system32\drivers\etc\hosts  Note that there is no extension for this file, it&#39;s just &quot;hosts&quot;.  If you&#39;re like most people, this is going to be pretty empty, perhaps only with the following line uncommented (a # at the beginning of a line is typically a comment):
</p>
<blockquote>
	127.0.0.1       localhost
</blockquote>
<p>
Lastly, open up Windows Explorer and navigate to our Web site folder.  Again, following the previous guide, this would be C:\home\website\public_html\.  If an index.html file exists, open it in Notepad.  If one doesn&#39;t exist, open Notepad and paste or type the following.  If the file exists, add only the <strong>bold</strong> text.
</p>
<blockquote>
	&lt;html&gt;<br />
	<strong>&lt;head&gt;<br />
	&lt;title&gt;website&lt;/title&gt;<br />
	&lt;/head&gt;</strong><br />
	&lt;body&gt;<br />
	&lt;p&gt;Hello world!&lt;/p&gt;<br />
	&lt;/body&gt;<br />
	&lt;/html&gt;
</blockquote>
<p>
Save the file if it already existed, or save the file as index.html (in the C:\home\website\public_html\ folder).  Close this document and go back to C:\home\.  Make a copy of the website folder, and rename the copy to website2.  Go into the website2\public_html folder and open the index.html file in Notepad.  Change &ldquo;website&rdquo; to &ldquo;website2&rdquo;.  We now have two websites, with a noticeable difference.
</p>
<p>
In the httpd.conf file, scroll all the way to the bottom of the file.  You&#39;ll notice there&#39;s a section on VirtualHost, which is what we&#39;re going to change here.  Add the following additional lines.
</p>
<blockquote>
	&lt;virtualhost 127.0.0.1&gt;<br />
	ServerName website.localhost<br />
	DocumentRoot C:\home\website\public_html<br />
	&lt;/virtualhost&gt;<br />
	<br />
	&lt;virtualhost 127.0.0.2&gt;<br />
	ServerName website2.localhost<br />
	DocumentRoot C:\home\website2\public_html<br />
	&lt;/virtualhost&gt;
</blockquote>
<p>
Save the changes and switch to the hosts file.  We&#39;re now going to change the one uncommented line, and add an additional line.
</p>
<blockquote>
	127.0.0.1	localhost	website.localhost<br />
	127.0.0.2	website2.localhost
</blockquote>
<p>
Note that the spaces are tabs.  Save the changes to this file as well.
</p>
<p>
Now, we&#39;re going to restart Apache by using the Services Control Panel (under Administrative Tools).  Once Apache has restarted, we&#39;re going to go to the following three sites, one after the other.  Note that the title of the page has changed, even though the text on the page is the same.  For the first two sites, the title should read website, while the third will read website2.  <a href="http://localhost/">http://localhost/</a>, <a href="http://website.localhost/">http://website.localhost/</a>, <a href="http://website2.localhost/">http://website2.localhost/</a>.
</p>
<p>
Note that this may not make the most sense.  In this case, we&#39;ve set website to be our fall-back position, or our core Web site.  It may make more sense to point localhost towards C:\home\.  This way, we can add additional Web sites to the C:\home\ folder and not have to setup additional VirtualHost entries.  Since this makes more sense to me, we&#39;re going to go ahead and change this.
</p>
<p>
First, in the httpd.conf file, search for DocumentRoot.  We&#39;re going to change the line with the second occurrence from:
</p>
<blockquote>
	DocumentRoot &quot;C:/home/website/public_html&quot;
</blockquote>
<p>
to:
</p>
<blockquote>
	DocumentRoot &quot;C:/home&quot;
</blockquote>
<p>
Scrolling down a bit, we&#39;re also going to change the following line:
</p>
<blockquote>
	&lt;directory &quot;C:/home/website/public_html&quot;&gt;
</blockquote>
<p>
to:
</p>
<blockquote>
	&lt;directory &quot;C:/home&quot;&gt;
</blockquote>
<p>
At the end of this same file, we&#39;re going to change the new lines we added.  Change these two to:
</p>
<blockquote>
	&lt;virtualhost 127.0.0.2&gt;<br />
	ServerName website.localhost<br />
	DocumentRoot C:\home\website\public_html<br />
	&lt;/virtualhost&gt;<br />
	<br />
	&lt;virtualhost 127.0.0.3&gt;<br />
	ServerName website2.localhost<br />
	DocumentRoot C:\home\website2\public_html<br />
	&lt;/virtualhost&gt;
</blockquote>
<p>
In the hosts file, replace the two uncommented lines with:
</p>
<blockquote>
	127.0.0.1	localhost<br />
	127.0.0.2	website.localhost<br />
	127.0.0.3	website2.localhost
</blockquote>
<p>
Finally, restart Apache, and hit the three URLs again - <a href="http://localhost/">http://localhost/</a>, <a href="http://website.localhost/">http://website.localhost/</a>, <a href="http://website2.localhost/">http://website2.localhost/</a>.  If we hit the first URL, we&#39;ll be presented with a directory listing, which you can click through to see the individual sites.  If we hit the last two URLs, we&#39;ll see each of the site&#39;s index.html files.
</p>
<p>
Now that we&#39;ve gone through it step-by-step, here&#39;s the short version of what we would need to do to add additional Web sites.
</p>
<ol>
	<li>Create the new folder(s) in the C:\home\ folder.</li>
	<li>Open the httpd.conf file and add a new VirtualHost for the new site.</li>
	<li>Open the hosts file and add a new IP mapping for the VirtualHost.</li>
	<li>Save all files and restart Apache.</li>
</ol>
<p>
For ease, you could create shortcuts in your C:\home\ folder for each of these three items &ndash; the httpd.conf file, the hosts file, and the Services control panel.
</p>

