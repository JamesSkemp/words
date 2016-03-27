+++
title = "Directories to parameters with IIS 6 and wildcard redirection"
description = "This could be old news, and since I'm talking about IIS 6, I know it is. But, I just discovered the other day how to pass parameters to a file using IIS 6, a virtual directory, and a URL that contains directories below the virtual directory. [slnet0514:3219a695-d0e2-4fcb-9f78-9cea8220350a]"
draft = false
comments = true
date = "2008-05-29T22:45:00-05:00"
modified = "2008-05-29T22:40:09-05:00"
slug = "Directories-to-parameters-with-IIS-6-and-wildcard-redirection"
blogengine = "3219a695-d0e2-4fcb-9f78-9cea8220350a"
categories = ["Internet", "software"]
tags = ["iis", "microsoft"]
+++

<div class="note">
<p>
Some parameters have been changed to protect the innocent.&nbsp; 
</p>
</div>
<p>
This could be old news, and since I&#39;m talking about IIS 6, I know it is. But, I just discovered the other day how to pass parameters to a file using IIS 6, a virtual directory,&nbsp;and a URL that contains directories below the virtual directory. 
</p>
<p>
So, at work I had a horrible URL like the following (ignore the invalid space): 
</p>
<blockquote>
	<p>
	/filename.cfm?parameterA=valueA&amp;parameterB=valueB &amp;issuemonth=4&amp;issueyear=2008&amp;groupname=publ 
	</p>
</blockquote>
<p>
What I wanted to do was allow someone to use a URL like this to get to that page: 
</p>
<blockquote>
	<p>
	/enews/publ/2008/4/<br />
	&nbsp;- or -<br />
	/enews/publ/2008/4 
	</p>
</blockquote>
<p>
Luckily, after a lucky Google search, I found a Microsoft TechNet on this very issue, in the Server 2003 <a href="http://www.microsoft.com/technet/prodtechnol/WindowsServer2003/Library/IIS/41c238b2-1188-488f-bf2d-464383b1bb08.mspx?mfr=true" target="_blank">Redirect Reference (IIS 6.0)</a>. 
</p>
<p>
The solution was to create a virtual directory called enews, and configure it to redirect to the&nbsp;<em>exact</em> URL entered: 
</p>
<blockquote>
	<p>
	*;/*/*/*/; /filename.cfm?parameterA=valueA&amp;parameterB=valueB&amp;issuemonth=$2&amp;issueyear=$1&amp;groupname=$0;/*/*/*; /filename.cfm?parameterA=valueA&amp;parameterB=valueB&amp;issuemonth=$2&amp;issueyear=$1&amp;groupname=$0 
	</p>
</blockquote>
<p>
Basically the second and third, semi-colon-delimited, strings handle the first URL (trailing slash) while the fourth and fifth handle the second. 
</p>
<p>
One thing that isn&#39;t covered is if they don&#39;t pass a &#39;month&#39;. However, I&#39;d assume that an additional &#39;block&#39; could be setup to handle this, as well as the case where there&#39;s only a group name. 
</p>
<p>
The disappointing thing is that this doesn&#39;t allow for too much in the way of wildcards - you can manually add text, or use a * for a wildcard - nothing fancy with switches or anything. But ... that&#39;s okay. 
</p>
<p>
The TechNet article covers a number of other things, so ... definitely give it a look. 
</p>
<p>
The more I use&nbsp;Microsoft products, the more impressed I am with the resources they make available online. 
</p>

