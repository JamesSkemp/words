+++
title = "Moving the location of PHP on your hard drive"
summary = "In this article, we'll be moving our installation of PHP 4.4.2 from c:\\php\\ to c:\\php4\\. We'll be doing this primarily because we may like the ability to run multiple versions of PHP at one time, on our development server."
draft = false
comments = true
date = "2006-07-01T07:26:00-05:00"
modified = "2007-09-06T22:34:35-05:00"
slug = "Moving-the-location-of-PHP-on-your-hard-drive"
blogengine = "bad3e3fc-b1b5-43ea-85e8-101854eca854"
categories = ["software", "tutorials / guides"]
tags = ["php", "apache"]
+++

<p>
In this article, we&#39;ll be moving our <a href="http://strivinglife.com/words/post/Installing-PHP-on-a-local-Windows-based%2c-Apache%2c-server.aspx">installation of PHP 4.4.2</a> from c:\php\ to c:\php4\. We&#39;ll be doing this primarily because we may like the ability to run multiple versions of PHP at one time, on our development server.
</p>
<p>
This will pave the way for our future installation of PHP 5.1.4 (or the current version of PHP 5.x). The added benefit is that we&#39;ll have an idea of just how many documents are involved in a relatively simple change.
</p>
<h4>Renaming the directory</h4>
<p>
The first thing we&#39;ll do is stop the Apache service. By doing this, anyone who attempts to visit our site, which is primarily us in this case, will see the same error message. On the other hand, if we were to move PHP without stopping Apache, it&#39;s possible that we could have a security hole &ndash; PHP code served as plaintext. While it&#39;s not too big of a concern for our development server, it could be a concern in a production environment, so we may as well just learn things right the first time.
</p>
<p>
Once Apache has stopped, we&#39;ll rename our directory from c:\php to c:\php4.
</p>
<p>
If you attempt to start Apache now, it won&#39;t work; Apache just won&#39;t want to start. We know why, but if you want the specifics, you can go to the Application errors under Event Viewer. If you followed the tutorial where we <a href="http://strivinglife.com/words/post/Creating-a-Microsoft-Management-Console-for-our-local-Windows-based%2c-Apache-server.aspx">setup a Microsoft Management Console</a>, then you can do this rather easily.
</p>
<h4>httpd.conf</h4>
<p>
The next thing to change is the httpd.conf file(s). If you&#39;ve got a number of these, then you&#39;ll probably want to change them all at the same time. However, you&#39;ll want to make a backup copy first.
</p>
<p>
Head over to C:\Program Files\Apache Group\Apache\conf\, or where ever your install directory is, backup each httpd.conf file that you need to (I had four to backup &ndash; one current, one backup, and two more for two versions of ColdFusion). Once you&#39;ve backed these up, open them up.
</p>
<p>
If we look back at our <a href="http://strivinglife.com/words/post/Installing-PHP-on-a-local-Windows-based%2c-Apache%2c-server.aspx">PHP install tutorial</a>, it looks like we have one thing to change in this document &ndash; we must find and correct the following line.
</p>
<blockquote>
	<p>
	LoadModule php4_module &quot;c:/php/php4apache.dll&rdquo;
	</p>
</blockquote>
<p>
Make the change in <em>each</em> of the httpd.conf files that you backed up, at the <em>same</em> time. It makes more sense to do it this way, unless you&#39;d like to test each of the httpd.conf files now. (Id est, in order to verify our correction, we&#39;d technically have to test each configuration now, to verify that we made the correction correctly. However, if we just carefully make each change at the semi-same time, we&#39;ll cut a corner and not <em>need</em> to test each configuration now. Of course, we really should, and if we have the time, we should.)
</p>
<p>
If you&#39;ll recall, when we installed PHP we also copied some files into the c:\windows\ folder, and it looks like we do have one other modification to make with a file there.
</p>
<h4>php.ini</h4>
<p>
There&#39;s one other change involving the c:\windows\php.ini file. Backing up this file is optional, depending upon how often you accidentally change more than you should ;) Open this file and correct the following line.
</p>
<blockquote>
	<p>
	extension_dir = &quot;C:\php\extensions\&quot;
	</p>
</blockquote>
<p>
Save this file. If you&#39;ve installed Zend Optimizer, you may also want to immediately make this change in the backup php.ini file(s) as well. We should now be ready to start Apache.
</p>
<h4>Starting Apache</h4>
<p>
If you followed the above correctly, you should now be able to start Apache successfully. If you have any problems, make sure you check the Application errors in the Event Viewer.
</p>
<p>
Go to your phpinfo file and verify that the page comes up correctly. Go to any of your other PHP files to verify that they also come up (like phpMyAdmin, and the like).
</p>
<p>
And with that, you&#39;ve setup PHP to use a different directory. As stated above, this will allow you to install PHP5 as well (in c:\php5, for example).
</p>
<p>
<a href="http://strivinglife.com/local-apache-server/">View all of the steps to creating a local Web server, for development.</a>
</p>

