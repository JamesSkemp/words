+++
title = "Error handling on a local Windows-based, Apache, server"
summary = "This time, we'll be setting up very basic error handling, and setup our first .htaccess file."
draft = false
comments = true
date = "2006-03-16T19:57:00-06:00"
slug = "Error-handling-on-a-local-Windows-based-Apache-server"
blogengine = "e04f361f-b8ad-4bdd-b2fb-6f4e3d516410"
categories = ["tutorials / guides"]
tags = ["apache"]
+++

<p>
This time, we&#39;ll be setting up very basic error handling, and setup our first .htaccess file.
</p>
<!--more--><!--adsense-->
<p>
If you&#39;ve been following along, we&#39;ve got no error handling in place. So, if you try to access a page that doesn&#39;t exist, like <a href="http://website.localhost/does_not_exist.html">http://website.localhost/does_not_exist.html</a>, you&#39;ll get a basic error page that comes straight out of Apache.
</p>
<p>
The problem with this is at least two-fold. First, someone will be able to determine our site&#39;s server software if they just try to hit a page that doesn&#39;t exist. Second, if we created an actual Web site, we&#39;d lose visitors. What we want to do is give the visitor an explanation of what may have happened, and offer them solutions &ndash; alternative pages and the like.
</p>
<p>
This time, we&#39;ll only be setting up a very basic, HTML, page. In a future article, we&#39;ll discuss how to create a more robust error handling page.
</p>
<p>
First, we&#39;ll want to create the page that the user will see. While we&#39;re doing this, we&#39;ll want to keep in mind that we should keep the file size relatively small, but larger than 512 bytes (due to Internet Explorer not being able to handle error pages smaller than this).
</p>
<p>
Something like the following should be enough.
</p>
<blockquote>
	<p>
	&lt;!DOCTYPE html PUBLIC &quot;-//W3C//DTD XHTML 1.0 Strict//EN&quot; &quot;http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd&quot;&gt;<br />
	&lt;html xmlns=&quot;http://www.w3.org/1999/xhtml&quot;&gt;<br />
	&lt;head&gt;<br />
	&lt;meta http-equiv=&quot;Content-Type&quot; content=&quot;text/html; charset=iso-8859-1&quot; /&gt;<br />
	&lt;title&gt;Whoops!&lt;/title&gt;<br />
	&lt;/head&gt;<br />
	&lt;body&gt;<br />
	&lt;br /&gt;&lt;br /&gt;<br />
	&lt;h1&gt;Whoops!&lt;/h1&gt;<br />
	&lt;p&gt;I&#39;m sorry, but the page that you&#39;re attempting to access either never existed, or no longer exists.&lt;/p&gt;<br />
	&lt;p&gt;Please visit our &lt;a href=&quot;/&quot;&gt;home page&lt;/a&gt; to continue.&lt;/p&gt;<br />
	&lt;p&gt;If you came upon this error by clicking on a link on this site, please contact the &lt;a href=&quot;mailto:insert_your_email@whatever_domain&quot;&gt;Webmaster&lt;/a&gt;.&lt;/p&gt;<br />
	&lt;/body&gt;<br />
	&lt;/html&gt;
	</p>
</blockquote>
<p>
Copy the above into a new file, and save it as error404.html in your website folder (c:\home\website\public_html\ if you&#39;ve been following along).
</p>
<p>
Now, create a new file in Notepad and paste the following into it:
</p>
<blockquote>
	<p>
	ErrorDocument 404 /error404.html
	</p>
</blockquote>
<p>
Now, save this file as &quot;.htaccess&quot;, again into your website folder (c:\home\website\public_html\). Note that there is a period before htaccess, and there is no extension.
</p>
<p>
Now, we&#39;ll make a slight modification to the Apache httpd.conf file (&quot;C:\Program Files\Apache Group\Apache\conf\httpd.conf&quot; if you&#39;ve been following along). Open this file and do a search for htaccess. The first uncommented line after your first find should be the following:
</p>
<blockquote>
	<p>
	AllowOverride None
	</p>
</blockquote>
<p>
Change this to:
</p>
<blockquote>
	<p>
	AllowOverride All
	</p>
</blockquote>
<p>
Now save httpd.conf, close the file, and restart Apache using the Services control panel.
</p>
<p>
Now, visit a page on &quot;website&quot; that doesn&#39;t exist, like we did before - <a href="http://website.localhost/does_not_exist.html">http://website.localhost/does_not_exist.html</a>
</p>
<p>
Once you&#39;ve done this, you should notice that the standard Apache error has been replaced by your custom error page. You can go ahead and custom this additionally, as necessary.
</p>
<p>
<a href="http://strivinglife.net/wordpress/a-local-apache-web-server-on-a-windows-xp-computer/">View all of the steps to creating a local Web server, for development.</a>
</p>

