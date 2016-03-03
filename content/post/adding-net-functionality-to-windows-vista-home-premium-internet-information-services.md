+++
title = "Adding .NET functionality to Windows Vista Home Premium Internet Information Services"
summary = "How to enable ASP.NET applications in IIS 7, on Windows Vista Home Premium. [slnet0514:87c5d691-ac12-4762-b35a-9a4ba13f15e3]"
draft = false
comments = true
date = "2008-03-22T09:00:00-05:00"
modified = "2008-03-22T10:20:52-05:00"
slug = "Adding-NET-functionality-to-Windows-Vista-Home-Premium-Internet-Information-Services"
blogengine = "87c5d691-ac12-4762-b35a-9a4ba13f15e3"
categories = ["software", "tutorials / guides"]
tags = ["microsoft", "vista", "iis"]
+++

<p>
I had previously covered <a href="/words/post/How-to-install-Internet-Information-Services-IIS-7-on-Windows-Vista-Home-Premium.aspx">how to install IIS 7 on Windows Vista Home Premium</a>. This time I&#39;ll be briefly covering what you need to enable ASP.NET as well. 
</p>
<p>
As before, you&#39;ll want to select <strong>Control Panel</strong> from the Start menu, then click on the <strong>Programs</strong> link. Next, click on <strong>Turn Windows features on or off</strong>. 
</p>
<p>
Expand <strong>Internet Information Services</strong>, followed by the <strong>World Wide Web Services</strong> and <strong>Application Development Features</strong>. 
</p>
<p>
Since we want to be able to run ASP.NET applications, we&#39;ll need to check the ASP.NET checkbox. This will also enable the following three features. 
</p>
<ul>
	<li>
	<div>
	.NET Extensibility 
	</div>
	</li>
	<li>
	<div>
	ISAPI Extensions 
	</div>
	</li>
	<li>
	<div>
	ISAPI Filters&nbsp; 
	</div>
	</li>
</ul>
<p>
If you also want to&nbsp;run classic ASP pages, you&#39;ll need to check the ASP checkbox as well. 
</p>

