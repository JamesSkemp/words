+++
title = "Making oXygen XML Editor (9.1) portable"
description = "A short guide on the ease of making oXygen XML Editor 9.1 portable. [slnet0514:8a9ba867-4fcc-40fe-af4a-9f8018711314]"
draft = false
comments = true
date = "2008-01-21T12:30:00-06:00"
modified = "2008-10-23T11:58:01-05:00"
slug = "Making-oXygen-XML-Editor-91-portable"
blogengine = "8a9ba867-4fcc-40fe-af4a-9f8018711314"
categories = ["software", "tutorials / guides"]
tags = ["xml"]
+++

<div class="note">
<p>
The below information is correct for version 9.1. Comments on other versions&nbsp;are appreciated. 
</p>
</div>
<p>
With flash drives becoming more and relevant, it&#39;s always good to find programs that can be run on these powerful drives. &lt;oXygen/&gt; XML Editor is one such program. 
</p>
<h3>Making &lt;oXygen/&gt; portable</h3>
<p>
On the official site, there&#39;s <a rel="nofollow" href="http://www.oxygenxml.com/forum/ftopic2610.html" target="_blank">a post regarding making &lt;oXygen/&gt; portable</a>. However, what does it really involve? 
</p>
<p>
Easily enough, it doesn&#39;t involve much more than is stated in the post. 
</p>
<p>
First, you&#39;ll want to get a coyp of &lt;oXygen/&gt; installed onto your flash drive. I had previously installed &lt;oXygen/&gt; to my computer, so I just copied the Oxygen XML Editor 9 folder, within the Program Files directory, to my flash drive. 
</p>
<p>
Next, there&#39;s a batch file called oxygen.bat in the main &lt;oXygen/&gt; directory. 
</p>
<p>
If you open this in a text editor,&nbsp;like Notepad, you&#39;ll want to either comment out the below line, using <strong>rem</strong> at the beginning of the line, delete it, or modify it. 
</p>
<blockquote>
	<p>
	java&nbsp; -Xss512k -Xmx256m -Dsun.java2d.noddraw=true -Dcom.oxygenxml.ApplicationDataFolder=&quot;%APPDATA%&quot; -cp %CP% ro.sync.exml.Oxygen %1 %2 %3 %4 %5 %6 %7 %8&nbsp; 
	</p>
</blockquote>
<p>
The line you&#39;ll want to end up with is as follows. 
</p>
<blockquote>
	<p>
	java&nbsp; -Duser.home=custom/license -Xss512k -Xmx256m -Dsun.java2d.noddraw=true -Dcom.oxygenxml.ApplicationDataFolder=&quot;%APPDATA%&quot; -cp %CP% ro.sync.exml.Oxygen %1 %2 %3 %4 %5 %6 %7 %8&nbsp; 
	</p>
</blockquote>
<p>
The relevant text is <strong>-Duser.home=custom/license</strong> . In this case I&#39;ve created a custom directory, under the &lt;oXygen/&gt; directory, as well as a license directory within that. 
</p>
<p>
Once I run this batch file, it creates a lock file under this directory. In my case, <strong>G:\Oxygen XML Editor 9\custom\license\oxygen.lock</strong> 
</p>
<p>
Once you&#39;ve run the batch file, you can enter your license into &lt;oXygen/&gt; as usual. Once the copy has been registered, you can close out of &lt;oXygen/&gt; and/or the batch file. For any further &lt;oXygen/&gt; needs you can just open the main oxygen executable. 
</p>
<h3>Portable apps</h3>
<p>
To see other applications that can be taken on the go, take a look at <a href="http://portableapps.com/" target="_blank">PortableApps.com</a>. 
</p>

