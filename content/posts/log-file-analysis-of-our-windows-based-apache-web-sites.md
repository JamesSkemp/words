+++
title = "Log file analysis of our Windows-based, Apache, Web sites"
summary = "In our previous articles, we walked through installing Apache to a Windows XP home computer.  This time, we'll be setting up our log files for analysis, and installing a way to view the log file information."
draft = false
comments = true
date = "2006-02-20T20:58:00-06:00"
slug = "Log-file-analysis-of-our-Windows-based-Apache-Web-sites"
blogengine = "a4fdb7ee-048d-4612-b749-6ff91732c78f"
categories = ["software", "tutorials / guides"]
tags = ["apache", "analytics"]
+++

<p>
In our previous articles, we walked through installing Apache to a Windows XP home computer.&nbsp; This time, we&#39;ll be setting up our log files for analysis, and installing a way to view the log file information.
</p>
<p>
Log files are created by Web sites to track page views and visitors.&nbsp; For example, if we go to a page on one of our local Web sites with Firefox, like http://website.localhost/, it adds the following lines to a file called access.log.
</p>
<blockquote>
	<p>
	127.0.0.2 - - [18/Feb/2006:09:29:43 -0600] &quot;GET / HTTP/1.1&quot; 200 94<br />
	127.0.0.2 - - [18/Feb/2006:09:29:43 -0600] &quot;GET /favicon.ico HTTP/1.1&quot; 404 291<br />
	127.0.0.2 - - [18/Feb/2006:09:29:43 -0600] &quot;GET /favicon.ico HTTP/1.1&quot; 404 291
	</p>
</blockquote>
<p>
This tells us that someone requested the root page at 127.0.0.2 (which is website.localhost), and was able to get the file, and 94 bytes of it (the total size of the file, in this case).&nbsp; They also requested a file called favicon.ico twice, but were unable to download the file (Apache returned a 404, or file not found, error).&nbsp; The size of the file they received from those requests was 291 bytes.
</p>
<p>
While we can certainly read through this file line by line, there&#39;s an easier way to handle these.
</p>
<p>
Before we install a program to look through these, let&#39;s go ahead and setup our log files.&nbsp; In order to do this, we&#39;re going to open up the httpd.conf file once again.
</p>
<h3>Setting up our log files</h3>
<p>
If you followed our previous guides, you may have a shortcut in the C:\home\ folder.&nbsp; Otherwise, you can access it via the Start menu, or by going to the file through Windows Explorer.
</p>
<p>
In the httpd.conf file, we&#39;re going to search for logs.&nbsp; If we do this enough, we&#39;ll end up at a couple lines that states:
</p>
<blockquote>
	<p>
	# ErrorLog: The location of the error log file.<br />
	# If you do not specify an ErrorLog directive within a &lt;VirtualHost&gt;<br />
	# container, error messages relating to that virtual host will be<br />
	# logged here.&nbsp; If you *do* define an error logfile for a &lt;VirtualHost&gt;<br />
	# container, that host&#39;s errors will be logged there and not here.
	</p>
</blockquote>
<p>
So, if we want to, we can declare where we want to store log files in the VirtualHost container (which, recall, is at the end of the httpd.conf file).&nbsp; If we go down a little further, first, we see some information about the format the logs file be stored in (LogFormat).
</p>
<p>
Find this line:
</p>
<blockquote>
	<p>
	CustomLog logs/access.log common
	</p>
</blockquote>
<p>
and change it to:
</p>
<blockquote>
	<p>
	#CustomLog logs/access.log common
	</p>
</blockquote>
<p>
In other words, we&#39;ve commented it out.&nbsp; Then, scroll down a couple lines and change
</p>
<blockquote>
	<p>
	#CustomLog logs/access.log combined
	</p>
</blockquote>
<p>
to:
</p>
<blockquote>
	<p>
	CustomLog logs/access.log combined
	</p>
</blockquote>
<p>
In other words, we&#39;ve uncommented this line.&nbsp; By commenting one line, and uncommenting another, we&#39;ve effectively increased what is being stored in our log files.&nbsp; If we save the httpd.conf file and restart Apache (using the Services control panel), and hit one of our pages again, we&#39;ll notice a much longer line of information.
</p>
<blockquote>
	<p>
	127.0.0.2 - - [18/Feb/2006:09:37:55 -0600] &quot;GET / HTTP/1.1&quot; 200 94 &quot;-&quot; &quot;Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.8.0.1) Gecko/20060111 Firefox/1.5.0.1&quot;
	</p>
</blockquote>
<p>
We now have referrer information and user agent information.&nbsp; The first is helpful for understanding where people came from to get to the page, and the second is useful for understanding who is making the request.
</p>
<p>
Now that we&#39;ve added more information to the logs, we&#39;re going to change where the log files for our subdomains is stored.
</p>
<p>
The first thing to note is that if we tell Apache to store our files in a folder that doesn&#39;t exist, it won&#39;t be able to create the folder, and won&#39;t be able to start.&nbsp; So, we need to determine where we want to store our log files.&nbsp; For now, let&#39;s go ahead and create a folder for each of our Web sites, in the current log file folder.&nbsp; With our current settings, this would be C:\Program Files\Apache Group\Apache\logs\.&nbsp; In this folder, create a website and a website2 folder.
</p>
<p>
Now, go to the VirtualHost containers at the bottom of the httpd.conf file.&nbsp; Add the following bold lines to the current content (which is not bold).
</p>
<blockquote>
	&lt;VirtualHost 127.0.0.2&gt;<br />
	ServerName website.localhost<br />
	DocumentRoot C:\home\website\public_html<br />
	<strong>ErrorLog logs/website/error.log<br />
	TransferLog logs/website/access.log</strong><br />
	&lt;/VirtualHost&gt;<br />
	<br />
	&lt;VirtualHost 127.0.0.3&gt;<br />
	ServerName website2.localhost<br />
	DocumentRoot C:\home\website2\public_html<br />
	<strong>ErrorLog logs/website2/error.log<br />
	TransferLog logs/website2/access.log</strong><br />
	&lt;/VirtualHost&gt;
</blockquote>
<p>
Save the httpd.conf file, and restart Apache.&nbsp; If Windows tells you that it can&#39;t start the service, make sure that you&#39;ve created the folders and typed everything in correctly.&nbsp; If we look in the website and website2 folders, we&#39;ll see that empty error.log and access.log files have been created.&nbsp; There is also one of each of these files in the main logs folder.&nbsp; If we now hit our Web sites, we&#39;ll notice that the size of the log files will increase slightly, and we&#39;ll have information about what content we viewed.
</p>
<p>
Now, let&#39;s hit each of our three Web sites a couple times.&nbsp; http://localhost/, http://website.localhost/, http://website2.localhost/
</p>
<p>
Now, we have effectively created some data, albeit data from only a small number of pages.&nbsp; Yet, it is data nonetheless, and since it&#39;s so small, we&#39;ll be able to easily look through our log files for information.
</p>
<p>
Before we go on, however, note that if you ever need to delete log files, you can do so by stopping Apache, deleting the files, and then starting Apache.
</p>
<h3>Installing a log file analyzer</h3>
<p>
For now, we&#39;re going to install a fairly simple log analyzer, Analog.&nbsp; You can download Analog at <a href="http://www.analog.cx/" target="_blank">http://www.analog.cx/</a>, or the nearest mirror (which I highly recommend you use).&nbsp; For now, I recommend downloading the zip file, if possible.&nbsp; Remember to download this into the folder you downloaded the Apache installer into.&nbsp; The download is about 2 MB.
</p>
<p>
In this case, I&#39;ve downloaded Analog 6.0.&nbsp; Once you&#39;ve downloaded Analog, extract the main Analog folder to C:\home\.&nbsp; We&#39;ll do this temporarily (just like how we&#39;ll only be using Analog temporarily) for ease.
</p>
<p>
Once you&#39;ve extracted the folder her, open up C:\home\analog 6.0\analog.cfg with Notepad.&nbsp; The first uncommented line will read as follows.
</p>
<blockquote>
	<p>
	LOGFILE logfile.log
	</p>
</blockquote>
<p>
We&#39;re going to put the following lines in it&#39;s place.
</p>
<blockquote>
	LOGFILE &quot;C:\Program Files\Apache Group\Apache\logs\access.log&quot; http://localhost<br />
	LOGFILE &quot;C:\Program Files\Apache Group\Apache\logs\website\access.log&quot; http://website.localhost<br />
	LOGFILE &quot;C:\Program Files\Apache Group\Apache\logs\website2\access.log&quot; http://website2.localhost
</blockquote>
<p>
Now save this file and run analog.exe.&nbsp; Once it finishes, it will have created an errors.txt file, and a Report.html (both of which will be overwritten every time analog.exe is run).
</p>
<p>
Assuming you made the minor change, you should be able to open the Reports.html file up and see the number of times you hit the Web site.&nbsp; If we hit the site some more and run analog.exe, we&#39;ll see that our new visits are recorded.
</p>
<p>
And with that, we&#39;ve successfully installed a very basic log file analyzer.&nbsp; Unfortunately, it doesn&#39;t give us the most interesting of results.&nbsp; At this point, however, we&#39;ll leave things as they are.&nbsp; Note that if we add any additional Web sites, we&#39;ll need to go back into the analog.cfg file and add them in as additional LOGFILE lines.
</p>
<p>
June 4, 2006: You may also find WebLog Expert Lite (currently 3.6) to also be of some use.&nbsp; This program can be found at <a href="http://www.weblogexpert.com/" target="_blank">http://www.weblogexpert.com/</a> and comes in both a free (Lite) version and a commercial version (non-Lite).&nbsp; Setup of the program is so easy that it hardly requires a tutorial.
</p>
<p>
<a href="/local-apache-server/">View all of the steps to creating a local Web server, for development</a>.
</p>

