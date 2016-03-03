+++
title = "Upgrading to BlogEngine.NET 1.4.5"
summary = "My experience upgrading to BlogEngine.NET 1.4.5."
draft = false
comments = true
date = "2008-08-16T12:41:00-05:00"
modified = "2008-08-16T12:49:33-05:00"
slug = "Upgrading-to-BlogEngineNET-145"
blogengine = "b0656b33-a17d-4217-9c5e-d5fdb56d1bd2"
categories = ["software"]
tags = ["blogengine.net"]
+++

<p>
With the release of <a href="http://www.dotnetblogengine.net/" target="_blank">BlogEngine.NET 1.4.5</a> a bit ago ... it was time to give it <a href="/words/post/BlogEngineNET-14-Memory-usage-spike.aspx">another go upgrading</a>. 
</p>
<p>
Quick notes on my experience: 
</p>
<ol>
	<li>
	<div>
	Downloaded and FTP&#39;d the zip. 
	</div>
	</li>
	<li>
	<div>
	Remoted into my VPS.&nbsp; 
	</div>
	</li>
	<li>
	<div>
	Extracted the contents of the zip to another folder. 
	</div>
	</li>
	<li>
	<div>
	Unchecked read-only on the extracted contents. 
	</div>
	</li>
	<li>
	<div>
	Backed up my complete BlogEngine directory. 
	</div>
	<ol>
		<li>
		<div>
		I had issues with roles.xml not being accessible. For some reason I had to set the owner again ... 
		</div>
		</li>
	</ol>
	</li>
	<li>
	<div>
	Created app_offline.htm file in BlogEngine directory, and tested this displayed.&nbsp; 
	</div>
	</li>
	<li>
	<div>
	Begin moving all files/directories over, excluding app_data. I use the rewrite method so I don&#39;t have to go around setting up permissions again. 
	</div>
	</li>
	<li>
	<div>
	Made necessary change to robots.txt. 
	</div>
	</li>
	<li>
	<div>
	Recycle app pool. 
	</div>
	</li>
	<li>
	<div>
	Rename&nbsp;app_offline.htm 
	</div>
	</li>
	<li>
	<div>
	Recycle app pool again. 
	</div>
	</li>
	<li>
	<div>
	Reset main account&#39;s password. 
	</div>
	</li>
</ol>
<p>
I was getting a 404 for Default.aspx when I was remoted in, so I had to pull the app_offline file and hope for the best. It took a while to start back up, but ... it&#39;s up and my core posts are working. 
</p>
<p>
Now I get to start checking my various themes to see how they work. 
</p>

